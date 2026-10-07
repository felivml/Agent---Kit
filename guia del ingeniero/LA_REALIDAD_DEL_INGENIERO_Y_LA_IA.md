# La Realidad del Ingeniero y la IA

### Del prototipo a producción, del Code Review a la caja registradora

**Por:** Antigravity (*Colaborador y Arquitecto Técnico*)  
**Tema:** Vibe coding, desconfianza técnica y la decisión entre empleo y emprendimiento en el contexto colombiano

---

## Tesis

La IA no eliminó la dificultad de la ingeniería de software. Cambió dónde está.

Escribir código es hoy casi gratis. **Entender un sistema, defender sus decisiones y responder por él cuando falla sigue siendo caro**, y es justamente eso lo que un empleador o un cliente está comprando. Este documento sostiene tres ideas:

1. La brecha entre un prototipo en `localhost` y un sistema en producción es el verdadero filtro del mercado.
2. El rechazo de los Tech Leads no es contra la IA, sino contra **el código que su autor no puede explicar**.
3. Elegir entre empleo y emprendimiento no es una cuestión de estilo ni de tolerancia a la fricción: es una cuestión de **criterio técnico, conocimiento del negocio y caja disponible**.

---

## 1. La ilusión del prototipo y el choque de producción

Con Claude, ChatGPT, Cursor o Copilot se llega en horas a una interfaz moderna, botones que responden y una base de datos conectada. La sensación de "ya casi está" es real y engañosa.

```
 [ ENTUSIASMO ]  ──►  [ LANZAMIENTO ]  ──►  [ CHOQUE REAL ]
 "Lo hice en 3 días"   Entran los primeros    Errores 500, cobros duplicados,
 "La IA lo programó"   usuarios y pagos       datos expuestos, soporte
```

Lo que en `localhost` no importa y en producción sí:

- **Concurrencia e integridad.** Si dos usuarios compran la última unidad en el mismo instante y el código solo sabe hacer `INSERT`, aparece inventario negativo o doble cobro. La solución exige transacciones, bloqueos o restricciones a nivel de base de datos, no un parche en el frontend.
- **Idempotencia.** Las pasarelas reenvían webhooks. Un handler que no es idempotente procesa el mismo pago dos veces.
- **Seguridad por defecto.** CORS abierto (`*`), tablas sin políticas de acceso (por ejemplo, sin RLS en Postgres/Supabase) y secretos en el cliente son inofensivos en local y catastróficos en producción: implican exposición de datos personales y responsabilidad legal.
- **El ciclo del parche ciego.** Se pega el error en el chat, la IA devuelve un arreglo que tapa el síntoma, y el defecto de fondo (un modelo de datos o un flujo mal pensado) sigue ahí. Dos días después aparecen tres fallos nuevos. Sin un modelo mental del sistema, no hay forma de distinguir un arreglo de un maquillaje.

> **Principio:** la IA es excelente generando soluciones locales y mediocre sosteniendo coherencia global. La coherencia global sigue siendo trabajo humano.

---

## 2. Lo que realmente teme un Tech Lead

Conviene ser preciso: **los equipos no rechazan la IA**. Muchos la fomentan. Lo que rechazan es un patrón concreto de riesgo.

| Temor real | Por qué es legítimo |
|---|---|
| **Asimetría de revisión** | Generar un PR de 800 líneas toma minutos; revisarlo bien toma horas. El costo lo asume el equipo senior, no el autor. |
| **Código que nadie entiende** | Si el autor no puede justificar una línea, nadie en el equipo es dueño de ella. Es deuda técnica con dueño desconocido. |
| **Parálisis en incidentes** | A las 2 a. m., con un sistema caído, hace falta razonar sobre logs, métricas y dependencias reales, no sobre un chat sin contexto de la infraestructura. |
| **Riesgos de cadena de suministro** | Los modelos pueden sugerir paquetes inexistentes o poco confiables, que un atacante puede registrar con ese nombre (*slopsquatting*). Dependencias que nadie auditó entran al repositorio. |
| **Fuga de información** | Pegar código propietario, credenciales o datos de clientes en un servicio externo de IA puede violar políticas internas y contractuales. |
| **Licencias y propiedad intelectual** | Código generado de procedencia incierta puede generar fricción legal en empresas reguladas. |

### Sobre los despidos en el período de prueba

Circulan muchos testimonios de contratos cancelados durante el primer mes por dependencia excesiva de la IA. Son **anécdotas creíbles, no estadística**. No hay una cifra sólida que cuantifique el fenómeno, y una cancelación temprana puede tener otras causas: onboarding deficiente, cambios de presupuesto, desajuste cultural o un líder sin tiempo para mentorar. Lo que sí es consistente en esos relatos es el mecanismo: **el candidato no logra defender ni modificar con autonomía lo que entregó.**

---

## 3. Qué miden hoy las entrevistas y el período de prueba

Escribir un bucle `for` dejó de ser señal. Hoy se evalúa:

- **Diseño de sistemas:** trade-offs SQL vs. NoSQL, latencia, particionamiento, colas, consistencia.
- **Defensa de decisiones:** *"¿Por qué este patrón aquí?"*, *"¿Cómo garantizas la idempotencia de este webhook?"*
- **Colaboración real:** Git en equipo (rebase, resolución de conflictos, PRs atómicos), Code Reviews, lectura de código existente.
- **Autonomía:** capacidad de avanzar sin que alguien (o algo) dicte cada paso.

La respuesta *"la IA me lo sugirió y funcionó en mi máquina"* es descalificante no por mencionar la IA, sino porque **demuestra ausencia de criterio**.

> **La línea que importa:** usar la IA como *herramienta de productividad* es aplaudido. Usarla como *sustituto del conocimiento* es lo que genera rechazo.

---

## 4. El toolkit: andamio de aprendizaje, no escudo

Existen prácticas y herramientas que reducen riesgos reales: TDD, políticas de acceso a nivel de base de datos (RLS), escaneo de secretos, revisión estática, principio YAGNI, CI/CD con puertas de calidad. Son valiosas. Pero hay que ser honestos sobre lo que **no** hacen:

> Una herramienta puede demostrar que existe un proceso. **No puede demostrar que tú entiendes lo que entregas.**

Si ante un Code Review la respuesta es *"el kit aprobó la auditoría"*, es la misma dependencia ciega que *"la IA lo generó"*, solo un nivel más arriba. El toolkit sirve cuando **te obliga a aprender el porqué**, no cuando te exime de saberlo.

| Temor del Tech Lead | Qué lo desarma de verdad | Cómo ayuda una herramienta |
|---|---|---|
| "Meterá código que no entiende" | Poder explicar cada línea y borrar lo innecesario | Linters, análisis de complejidad y la disciplina YAGNI te señalan qué sobra |
| "Dejará huecos de seguridad" | Conocer el modelo de amenazas y el principio de mínimo privilegio | Escaneo de secretos, revisión de políticas de acceso, auditorías automáticas como **segunda opinión** |
| "Romperá producción" | Haber escrito pruebas que definan el comportamiento esperado | TDD y CI que bloquea merges sin pruebas |
| "No sabrá navegar código legacy" | Haber leído, ejecutado y depurado repositorios grandes | Grafos de dependencias y búsqueda semántica aceleran la exploración, pero no reemplazan leer y probar |
| "Se paralizará en un incidente" | Saber leer logs, métricas y trazas; haber practicado postmortems | Observabilidad, runbooks y simulacros |
| "Hará interfaces genéricas" | Gusto, criterio de producto y sistema de diseño propio | Guías y tokens de diseño como punto de partida, no como resultado final |

**Regla práctica:** cada herramienta del kit debe responder a la pregunta *"¿qué aprendí por usarla?"* Si la respuesta es *"nada"*, estás delegando, no aprendiendo.

---

## 5. Plan de transformación: de usuario de IA a ingeniero aumentado

### 5.1 Regla de oro: no commitees lo que no puedas explicar

Antes de un `git push`, hazte esta prueba: *si el Tech Lead señala la línea 45 y pregunta por qué usé este `reduce` o este bloqueo de base de datos, ¿puedo responder sin abrir el chat?* Si no, el commit espera.

### 5.2 Usa la IA como mentor crítico, no como mecanógrafo

En lugar de *"escríbeme esta función"*, prueba:

> *"Actúa como un Tech Lead estricto. Esta es mi solución a este problema. Critica sin piedad seguridad, concurrencia, rendimiento y dependencias innecesarias. Para cada observación, explícame el porqué y el riesgo concreto."*

Escribe primero tu propio diseño y usa la IA para atacarlo, no al revés.

### 5.3 Domina los cuatro fundamentos que la IA no te da por ósmosis

1. **Git colaborativo:** ramas, rebase, conflictos, PRs pequeños y bien descritos.
2. **Bases de datos reales:** transacciones ACID, niveles de aislamiento, índices, bloqueos y políticas de acceso.
3. **Lectura de código legacy:** contribuir a repositorios existentes y grandes, no solo crear proyectos vacíos.
4. **TDD:** escribe la prueba que define el comportamiento y luego pide a la IA una implementación que la haga pasar. Tú eres dueño de la especificación.

### 5.4 Cómo responder en un Code Review

- ❌ *"La IA me lo sugirió así y funcionó en mi máquina."*
- ✅ *"Comparé dos enfoques: eventos y polling. Elegí eventos porque evitan sobrecargar la API y permiten reintentos con backoff exponencial. Añadí tres pruebas para los casos borde: duplicados, orden inverso y timeout. El riesgo que acepto es la complejidad extra de la cola."*

### 5.5 Checklist antes de abrir un Pull Request

- [ ] Puedo explicar cada función sin consultar la IA.
- [ ] Revisé cada dependencia nueva: existe, está mantenida y su licencia es compatible.
- [ ] No hay secretos, tokens ni datos reales en el código ni en prompts que haya compartido.
- [ ] Hay pruebas que fallan si rompo el comportamiento clave.
- [ ] El PR es pequeño y su descripción explica **el porqué**, no solo el qué.
- [ ] Sé qué pasa si esto falla en producción y cómo lo detectaría.

---

## 6. Distribución y retención: lo que el código no resuelve

Si el código es cada vez más un *commodity*, la ventaja competitiva se desplaza a lo que no se copia con un prompt:

- **Distribución:** audiencia propia, SEO, contenido, alianzas, canales validados.
- **Retención:** conseguir 1.000 registros genera dopamina; si la mayoría no vuelve al día 7, no hay negocio. Hay que leer reseñas y tickets, medir retención, iterar con frecuencia y ajustar precio según la disposición real de pago.
- **Confianza:** en B2B, el cliente compra continuidad y respaldo, no pantallas bonitas.

Esto aplica también a quien trabaja en empresa: entender cómo el software genera ingresos te vuelve mejor ingeniero.

---

## 7. Colombia: contexto y datos (con matices)

### Talento y empleo

- Gremio y Gobierno hablan de un **déficit de talento tecnológico**: MinTIC ha citado un déficit de hasta 112.000 programadores en un año reciente, y Fedesoft proyectó cerca de 162.000 talentos faltantes hacia 2025. Existe además un estudio nacional más reciente de MinTIC y Fedesoft sobre brecha de talento 2025-2030.
- **Matiz importante:** estas son **proyecciones de vacantes**, con metodologías y años distintos. No equivalen a que cualquier perfil junior sea contratable. Que falte talento *especializado y con criterio* es perfectamente compatible con que las empresas sean muy selectivas con perfiles sin base sólida.

### Cumplimiento normativo

- Tratamiento de datos personales: **Ley 1581 de 2012** y supervisión de la **SIC**.
- Facturación electrónica ante la **DIAN** para quienes están obligados.
- Pasarelas locales (por ejemplo, Wompi o PayU) con sus propias exigencias de integración y conciliación.
- **ISO 27001** no es una obligación legal general, pero es habitual que **clientes corporativos y procesos de compra** la exijan o evalúen prácticas equivalentes (DevSecOps, gestión de accesos, trazabilidad).

### Supervivencia empresarial

Según el estudio de Confecámaras *La Supervivencia Empresarial en Colombia* (cohorte creada en 2017 y observada en 2022), **solo el 33,5 % de las empresas sobreviven a los cinco años**, por debajo del promedio de la OCDE (superior al 40 %). Para microempresas la cifra es 33,4 %; para pequeñas, 60,9 %. Los factores asociados a la permanencia que el estudio destaca incluyen el tamaño, el acceso a mercados internacionales, la atracción de capital, el acceso al crédito y pertenecer a un clúster. Además, las actividades **intensivas en conocimiento** tienen mayor supervivencia.

Dos precisiones frente a lo que suele repetirse: la cifra de referencia es a **cinco años**, no tres, y el estudio **no afirma** que la causa número uno de cierre sea la falta de audiencia o de conocimiento del dolor del cliente. Esas son lecturas razonables, pero deben presentarse como interpretación y no como dato de Confecámaras.

---

## 8. La encrucijada: A, B, y la opción que casi nadie nombra

```
              ¿Cuál es tu situación real hoy?
                          │
     ┌────────────────────┼─────────────────────┐
     ▼                    ▼                     ▼
 CAMINO A              CAMINO C               CAMINO B
 Empleo en empresa     Híbrido                Producto propio
                       (A + B)
```

**Camino A: empleo.** Ingresos estables, mentoría, exposición a sistemas reales, aprendizaje de procesos y de negocio con el riesgo financiero absorbido por otro. El costo: menor autonomía y adaptarse a la cultura del equipo.

**Camino B: producto propio.** Autonomía y potencial de upside. El costo: **eres a la vez ingeniero, vendedor, soporte y responsable legal**, y la caja decide cuánto tiempo puedes seguir. No hay "libertad de aprobación": cambias a un Tech Lead por clientes, pasarelas, reguladores y flujo de caja, que son revisores más duros.

**Camino C: híbrido.** Salario o freelance como colchón, producto propio en paralelo sobre un problema validado con clientes reales, y salto a dedicación completa cuando haya evidencia (ingresos recurrentes, retención, pipeline).

### Cuándo tiene sentido pasar de A a B

Señales prácticas, no absolutas:

1. Tienes **runway** (meses de gastos cubiertos) sin depender de que el producto facture ya.
2. Conoces **un dolor concreto** de un tipo de cliente y hablaste con varios que ya dijeron que pagarían.
3. Tienes **un canal de distribución** probado, aunque sea pequeño.
4. Puedes **operar** el producto: monitoreo, respaldos, soporte y cumplimiento básico.
5. Tu motivación es **construir un negocio**, no escapar de que te cuestionen.

> Si lo que te impulsa a B es evitar la fricción de un Code Review, B no te la quitará: te la multiplicará. Los clientes, los auditores y la SIC también hacen preguntas incómodas, y sus consecuencias son más costosas.

---

## 9. Veredicto

**Lo esencial:** no uses la IA para huir del rigor técnico. Úsala para llegar más rápido a él. Entender arquitectura es lo que te permite saber qué pedirle, cómo evaluarlo y cuándo desconfiar.

**Sobre la decisión:** a largo plazo, **construir algo propio puede ser la opción de mayor upside**, pero solo para quien llega con tres cosas: criterio técnico para que el producto no colapse, conocimiento real del negocio y del cliente, y caja suficiente para resistir. Con la mayoría de las empresas colombianas sin alcanzar los cinco años, el orden importa más que la elección.

**La recomendación estratégica:**

1. **Primero, criterio.** Domina los fundamentos y aprende a defender cada decisión.
2. **Después, negocio.** Trabaja un tiempo en un equipo, preferiblemente uno que use IA con criterio, o haz consultoría para ver los problemas reales de empresas reales.
3. **Luego, validación.** Habla con empresarios que sufren con la tecnología. Entiende su stack, su presupuesto y su dolor antes de escribir una línea.
4. **Finalmente, producto propio con runway.** No como escape, sino como consecuencia lógica de lo aprendido.

**Camino A, Camino B o ambos en secuencia: lo que no cambia es que la IA te amplifica.** Si amplifica criterio, te vuelve muy valioso. Si amplifica ausencia de criterio, solo acelera el momento en que el problema se hace visible.

---

## Fuentes y notas de verificación

- **Confecámaras**, *La Supervivencia Empresarial en Colombia: estudio de los factores clave que impulsan la permanencia de las empresas* (cohorte 2017, observación 2022): supervivencia a 5 años 33,5 %; microempresas 33,4 %; pequeñas 60,9 %; medianas 73,7 %; grandes 85,7 %. Cifras reproducidas por Confecámaras, Portafolio, Bloomberg Línea e INCP.
- **Fedesoft / MinTIC:** déficits proyectados citados en medios (hasta 112.000 programadores según MinTIC; ~162.000 para 2025 según Fedesoft) y estudio nacional de empleabilidad y talento digital 2025-2030. Son proyecciones con metodologías distintas; conviene citar el informe original y su fecha en la versión final.
- **Pendiente de respaldo antes de publicar:** cualquier cifra sobre el porcentaje de empresas de software colombianas que integran IA, y cualquier estadística sobre despidos en el primer mes. Si no se consigue una fuente primaria, presentarlas como observación cualitativa.
- Las referencias a normativa (Ley 1581 de 2012, SIC, DIAN) y a prácticas (RLS, idempotencia, TDD, ISO 27001) son de carácter general; para decisiones legales o de cumplimiento, consultar a un profesional especializado.
