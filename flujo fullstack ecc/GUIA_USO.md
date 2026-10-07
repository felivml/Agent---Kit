# 🚀 Guía de Ingeniería Full-Stack: Metodología ECC (Everything Claude Code)

La metodología **ECC (Everything Claude Code)**, creada por el ganador del Hackathon de Anthropic **Affaan Mustafa**, es un marco operativo de trabajo para evitar la "pudrición de contexto" (*context rot*) y obligar a la IA a trabajar con el rigor de un **Ingeniero Full-Stack Senior**.

---

## 💥 El Problema que Resuelve: "Context Rot"

Cuando una sesión de desarrollo con IA supera los 15-20 mensajes, el agente:
* Olvida variables y tipos que declaró al inicio.
* Empieza a generar código redundante o sobreingeniería.
* Modifica archivos sin verificar si rompió otra parte del sistema.

**ECC resuelve esto dividiendo el ciclo de vida del software en 5 Etapas Disciplinadas:**

```
  ┌───────────────────────┐
  │ 1. PLANIFICACIÓN      │ ➔ Define el PRD, alcance y checklist de tareas antes de escribir código.
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 2. ARQUITECTURA       │ ➔ Modela esquemas SQL/TypeScript y contratos de API REST/GraphQL.
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 3. TDD (TESTS FIRST)  │ ➔ Escribe los tests unitarios primero (los tests deben fallar inicialmente).
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 4. IMPLEMENTACIÓN     │ ➔ Escribe el código mínimo necesario para que todos los tests pasen (YAGNI).
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 5. REVIEW & COMMIT    │ ➔ Revisa principios SOLID, seguridad, formatea y genera commit atómico.
  └───────────────────────┘
```

---

## 🛠️ Las 5 Etapas en Detalle

### 1️⃣ Etapa 1: Planificación Quirúrgica
Antes de tocar cualquier archivo, el agente debe generar un plan con:
* **Archivos a Crear/Modificar:** Lista exacta de rutas.
* **Dependencias:** Si ya existen en el proyecto o si la librería estándar las resuelve (filtro Ponytail).
* **Riesgos Potenciales:** Qué podría romperse en bases de datos o contratos existentes.

### 2️⃣ Etapa 2: Arquitectura & Tipado Estricto
* Definición de interfaces TypeScript / esquemas de base de datos primero.
* Contratos de entrada y salida (`request` / `response`) validados con Zod o validadores nativos.

### 3️⃣ Etapa 3: Desarrollo Guiado por Pruebas (TDD)
* Escribir la suite de tests (`vitest`, `jest`, `pytest` o el runner del proyecto).
* Ejecutar la prueba para verificar que **falla** por la razón correcta (Red).

### 4️⃣ Etapa 4: Implementación Limpia
* Programar la solución con el código más simple posible (Green).
* Cero abstracciones prematuras ni capas intermedias innecesarias.

### 5️⃣ Etapa 5: Code Review & Commit Atómico
* Auditoría de seguridad básica (sanitización de inputs, variables de entorno protegidas).
* Ejecución de linters (`eslint`, `tsc`, `biome`).
* Commit de Git con mensaje estandarizado:
  ```bash
  git commit -m "feat(auth): implementar middleware de verificacion JWT y tests"
  ```

---

## 🎯 Plantilla de Activación del Flujo Full-Stack ECC

Para iniciar cualquier tarea compleja con esta disciplina, ejecuta el siguiente prompt en tu asistente de IA:

```markdown
### 🚀 Iniciar Tarea con Metodología Full-Stack ECC

**Misión:** Actúa como un Ingeniero Full-Stack Senior siguiendo la metodología ECC de Affaan Mustafa.
**Objetivo de la Tarea:** [Describe lo que necesitas construir o refactorizar]

**Reglas de Flujo Obligatorias:**
1. **Paso 1 (Plan):** Muestra el plan de archivos a modificar y el checklist de pasos. No escribas código aún.
2. **Paso 2 (Arquitectura & Tests):** Define los tipos/interfaces y escribe los tests unitarios que validen la solución.
3. **Paso 3 (Implementación):** Escribe el código mínimo y necesario para que los tests pasen al 100%.
4. **Paso 4 (Review):** Revisa que no haya dependencias innecesarias, ejecuta los tests y confirma que el build es exitoso.
```

---

## 🌐 Recursos Oficiales
* **Repositorio GitHub:** [github.com/affaan-m/ECC](https://github.com/affaan-m/ECC)
* **Web Oficial de Affaan Mustafa:** [affaanmustafa.com](https://affaanmustafa.com)

---

*Este documento forma parte del Toolkit Senior de Antigravity para garantizar ingeniería de software rigurosa y código de producción.*
