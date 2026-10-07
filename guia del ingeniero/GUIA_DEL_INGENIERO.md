# 🛠️ Guía del Ingeniero Senior: Diagnóstico de Arquitectura, Cuellos de Botella y Grafos

Esta guía está diseñada para que cualquier **desarrollador o agente de IA** pueda diagnosticar, detectar "puntos ciegos" (huecos de botella) y aplicar **soluciones definitivas** ante problemas complejos de arquitectura, dependencias enredadas y modelado de datos de negocio.

---

## 📚 Documentos Clave en este Módulo:
* 🛡️ **[`REGLAS_FIJAS_SITIOS_WEB_E_IA.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/REGLAS_FIJAS_SITIOS_WEB_E_IA.md)**: Reglas inmutables de seguridad para sitios web y apps hechas con IA: Row Level Security (RLS), CORS estricto, variables de entorno sin fugas y Rate Limiting.
* 📄 **[`GUIA_DEL_INGENIERO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/GUIA_DEL_INGENIERO.md)**: Diagnóstico de cuellos de botella y buenas prácticas de arquitectura.
* 💼 **[`COTIZACION.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/COTIZACION.md)**: Manual de cotización profesional de software de alta conversión: Llamada grabada + Transcripción IA + Propuesta visual + Video explicativo con [Loom](https://www.loom.com/).
* 🎨 **[`ESTILOS_UI.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/ESTILOS_UI.md)**: Catálogo Maestro de los 9 Grandes Estilos UI (Neumorfismo, Glassmorfismo, Claymorfismo, Neo-Brutalismo, Bento Grid, UI Espacial, Liquid Glass, Minimalismo y Maximalismo) con fórmulas CSS y prompts.
* 🛒 **[`ECOMMERCE_FULLSTACK_BAGISTO_Y_COLOMBIA.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/ECOMMERCE_FULLSTACK_BAGISTO_Y_COLOMBIA.md)**: Manual de eCommerce Open Source con Bagisto (Laravel + Vue), instalación, personalización y adaptación 100% legal/fiscal para Colombia (SIC, DIAN, Wompi).
* 📋 **[`METODOLOGIA_SRS_SPRINTS_Y_ENTREGA_CLIENTE.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/METODOLOGIA_SRS_SPRINTS_Y_ENTREGA_CLIENTE.md)**: Metodología Senior de entrega de software: SRS (59 págs / sin ambigüedades), Scrum/Kanban en Trello, Sprints, MVP y propiedad del código.
* 🧠 **[`CEREBROS_Y_GRAFOS.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/CEREBROS_Y_GRAFOS.md)**: Manual definitivo para crear un "Cerebro de Negocio" / GraphRAG con cero alucinaciones.
* 🔀 **[`ENRUTAMIENTO_APIS_Y_COSTO_CERO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/ENRUTAMIENTO_APIS_Y_COSTO_CERO.md)**: Enrutamiento de IA, alta disponibilidad (Auto-Fallback) y catálogo de Free LLM APIs (Costo Cero).
* ⚠️ **[`LA_REALIDAD_DEL_INGENIERO_Y_LA_IA.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/LA_REALIDAD_DEL_INGENIERO_Y_LA_IA.md)**: Manifiesto y guía definitiva: Vibe coding, asimetría de Code Review, rigor en Colombia (Confecámaras/Fedesoft) y la estrategia entre empleo (A), producto propio (B) e híbrido (C).
* 🎨 **[`DISEÑO_DE_PROMPTS_PARA_UI.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/DISE%C3%91O_DE_PROMPTS_PARA_UI.md)**: Bibliotecas de prompts de diseño, generadores de `DESIGN.md` y recursos de inspiración visual.
* 📜 **[`CREDITOS.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/CREDITOS.md)**: Atribución a `@Graphify-Labs` y `@diegosouzapw`.

---

## 🎯 Propósito de esta Guía
Cuando un proyecto crece o se vuelve confuso, los desarrolladores suelen cometer errores graves:
* No saben qué función o módulo rompe el sistema al hacer un cambio.
* Existen módulos monstruosos de los que depende todo (**"God Nodes"** o cuellos de botella).
* La IA alucina o inventa relaciones falsas entre tablas y reglas de negocio.
* El flujo de trabajo se interrumpe porque **el proveedor de IA se cae o agota su cuota**.

Esta guía proporciona el **procedimiento operativo estándar** para resolver esos problemas de raíz.

---

## 🧭 Diagnóstico de Cuellos de Botella: Matriz de Solución Rápida

| Síntoma o "Hueco" en el Proyecto | Riesgo Real | Solución Definitiva | Herramienta |
|---|---|---|---|
| **La IA "se queda sin pensar" (Error 429 / Cuota agotada):** El proveedor de LLM se satura o se cae en pleno desarrollo. | Parálisis del programador o fallo de agentes autónomos en producción. | Enrutamiento con auto-fallback multi-proveedor y Free LLM APIs a costo cero. | **OmniRoute + Free APIs** (Ver [`ENRUTAMIENTO_APIS_Y_COSTO_CERO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/ENRUTAMIENTO_APIS_Y_COSTO_CERO.md)) |
| **Módulo Monstruo ("God Node"):** Un solo archivo o tabla maneja casi toda la lógica del negocio. | Si ese archivo falla, todo el sistema colapsa. Difícil de testear. | Desacoplar en sub-módulos independientes y aplicar inversión de dependencias. | **Graphify** (`GRAPH_REPORT.md`) |
| **Dependencias Circulares:** El módulo A importa a B, y B importa a A. | Errores de inicio, fugas de memoria y bloqueos de compilación. | Crear un módulo intermedio compartido (`shared` / `core`) o usar eventos. | **Tree-Sitter AST** |
| **La IA alucina con reglas del negocio:** La IA olvida quién autoriza qué o cómo se conectan las tablas. | Respuestas incorrectas a clientes y bugs en producción. | Mapear la lógica en un archivo determinista **GraphRAG** (`graph.json`). | Ver [`CEREBROS_Y_GRAFOS.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/CEREBROS_Y_GRAFOS.md) |
| **Código Spaghetti sin mapa:** Nadie sabe cómo fluyen los datos en el sistema. | Miedo a tocar código antiguo (*legacy*). | Generar un mapa visual interactivo en 3D/2D para auditar conexiones. | **`graph.html`** |

---

## 🔬 Flujo de Trabajo para el Agente / Desarrollador

Cuando te enfrentes a un proyecto confuso o con cuellos de botella, sigue este protocolo:

### Paso 1: Mapear la Red de Conexiones (Cero Adivinanzas)
Antes de editar código a ciegas, genera el mapa del proyecto:
```bash
# Analizar el proyecto y generar el reporte arquitectónico
graphify ./src --output ./diagnostico-ingenieria
```

### Paso 2: Auditar el reporte `GRAPH_REPORT.md`
Revisa los 3 indicadores clave:
1. **Comunidades de Código:** ¿Están los módulos bien aislados o todo está mezclado?
2. **Nodos Críticos:** Identifica qué archivos tienen más de 15 conexiones entrantes (esos son los cuellos de botella prioritarios).
3. **Dependencias Huérfanas:** Código muerto que se puede eliminar de inmediato (aplicando `Ponytail`).

### Paso 3: Aplicar la Solución Definitiva
* **Si el problema es sobreingeniería:** Aplica la Escalera de Ponytail (eliminar capas intermedias innecesarias).
* **Si el problema es falta de claridad en el negocio:** Estructura las entidades en el `graph.json` para que la IA consulte relaciones exactas.
