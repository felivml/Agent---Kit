# 📖 Guía Maestra: The Agent Skills Directory & Vercel CLI

Esta guía explica en detalle cómo funciona el ecosistema de **Vercel Labs** para descubrir, evaluar e instalar habilidades (`skills`) para agentes de inteligencia artificial.

---

## 🌐 ¿Qué es `skills.sh` y el formato `SKILL.md`?

* **Sitio Web Oficial:** [https://skills.sh](https://skills.sh)
* **Repositorio Central:** [https://github.com/vercel-labs/skills](https://github.com/vercel-labs/skills)
* **Creador:** **Vercel Labs** (Equipo de I+D de Vercel)
* **Licencia:** MIT

El formato `SKILL.md` es el estándar abierto de la industria para dotar a agentes de IA (como Antigravity, Claude Code, Cursor, Codex) de instrucciones estructuradas, flujos de trabajo Senior y scripts locales.

---

## 🚀 Las 2 Formas de Uso

```
                            ┌───────────────────────────────┐
                            │   ¿Cómo encontrar una Skill?   │
                            └──────────────┬────────────────┘
                                           │
                    ┌──────────────────────┴──────────────────────┐
                    ▼                                             ▼
       ┌─────────────────────────┐                   ┌─────────────────────────┐
       │   1. VÍA WEB (skills.sh)│                   │   2. VÍA CLI (Terminal) │
       └────────────┬────────────┘                   └────────────┬────────────┘
                    │                                             │
      • Exploración visual                          • Búsqueda por comando
      • Ranking de popularidad                      • Instalación en 1 paso
      • Métricas de GitHub                          • Integración directa
```

---

### 1️⃣ Método 1: Vía Web ([skills.sh](https://skills.sh))

Es la interfaz gráfica del directorio. Es ideal para explorar y descubrir nuevas herramientas visualmente.

1. **Ingresa a:** [https://skills.sh](https://skills.sh)
2. **Explora por Categorías:** Frontend, Backend, Testing, DevOps, AI, Bases de Datos, etc.
3. **Revisa Métricas de Confianza:**
   * ⭐ **Estrellas de GitHub** del repositorio.
   * 📥 **Número de instalaciones y descargas**.
   * 👤 **Reputación del autor**.
4. **Copia el comando:** La web te da directamente el comando `npx skills add` listo para pegar en tu terminal.

---

### 2️⃣ Método 2: Vía CLI (`npx skills`)

Permite interactuar con el directorio directamente desde la terminal de tu proyecto sin abrir el navegador.

#### A. Buscar habilidades desde la terminal
```bash
# Búsqueda por palabra clave o problema a resolver
npx skills find "<tema o consulta>"

# Ejemplos:
npx skills find "tailwind animation"
npx skills find "postgresql optimization"
npx skills find "nextjs seo"
```

#### B. Listar qué skills contiene un repositorio antes de instalar
```bash
npx skills add vercel-labs/agent-skills --list
```

#### C. Instalar una skill específica en tu proyecto
```bash
# Instala una skill puntual dentro de tu carpeta de proyecto
npx skills add vercel-labs/agent-skills --skill web-design-guidelines

# Instalar desde cualquier repo de GitHub
npx skills add <usuario/nombre-del-repo>
```

#### D. Probar una skill sin instalarla de forma permanente
```bash
npx skills use vercel-labs/agent-skills --skill web-design-guidelines
```

---

## 🛡️ Protocolo Senior de Seguridad al Instalar Skills

Cualquier desarrollador puede publicar una skill en GitHub. Por ello, en nuestro entorno siempre aplicamos estas 3 reglas:

1. **Verificar el autor y las estrellas:** Dar prioridad a repositorios de organizaciones reconocidas (como Vercel, Supabase, NextLevelBuilder) o con comunidad activa.
2. **Auditar scripts:** Revisar que los scripts locales no hagan peticiones de red a servidores desconocidos ni ejecuten código ofuscado.
3. **Registrar en el catálogo:** Documentar en [`REPOSITORIOS_SENIOR.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/REPOSITORIOS_SENIOR.md) su origen y ficha técnica.
