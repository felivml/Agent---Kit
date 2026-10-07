# 🤖 Reglas de Trabajo y Toolkit Senior para Antigravity

Este workspace cuenta con herramientas y repositorios estructurados para garantizar código y diseño de nivel **Senior**, eliminando el código genérico de IA ("AI slop") y la sobreingeniería.

---

## 🛠️ Herramientas y Skills Disponibles en este Workspace

### 1. Sistema de Diseño Inteligente: `ui-ux-pro-max`
* **Ubicación:** [`diseño frontend ui-ux/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/diseño%20frontend%20ui-ux/)
* **Autor:** [@nextlevelbuilder](https://github.com/nextlevelbuilder)
* **Instrucción para el Agente:** Antes de programar cualquier frontend, landing page o dashboard, el agente **DEBE** consultar el motor local para obtener la paleta, fuentes y reglas anti-patrones:
  ```bash
  python "d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend ui-ux/src/ui-ux-pro-max/scripts/search.py" "<descripción del proyecto o industria>" --design-system
  ```

### 2. Landing Pages 3D Continuas: `scroll-world`
* **Ubicación:** [`diseño frontend 3d/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/diseño%20frontend%203d/)
* **Autor:** [@oso95](https://github.com/oso95)
* **Instrucción para el Agente:** Al construir experiencias 3D inmersivas controladas por scroll (estilo Apple), usar la arquitectura de *video-scrubbing* en Vanilla JS con *frame-locking* en lugar de Three.js pesado.

### 3. Anti-Sobreingeniería & YAGNI: `ponytail`
* **Ubicación:** [`ponytail anti-sobreingenieria/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/ponytail%20anti-sobreingenieria/)
* **Autor:** [@DietrichGebert](https://github.com/DietrichGebert)
* **Instrucción para el Agente:** Aplicar siempre "La Escalera de Decisión":
  1. *¿Necesita existir? (YAGNI)*
  2. *¿Ya existe en el código? (Reutilizar)*
  3. *¿La librería estándar lo resuelve?*
  4. *¿HTML/CSS nativo lo cubre?*
  5. *¿Puede ser una sola línea?*
  *Prohibido instalar paquetes innecesarios o crear capas abstractas sin justificación.*

### 4. Diagnóstico de Arquitectura & Grafos: `guia del ingeniero`
* **Ubicación:** [`guia del ingeniero/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/)
* **Instrucción para el Agente:** Ante refactorizaciones complejas, cuellos de botella ("huecos"), saturación de APIs o necesidad de diseñar un cerebro con relaciones de negocio sin alucinaciones, consultar [`GUIA_DEL_INGENIERO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/GUIA_DEL_INGENIERO.md), [`CEREBROS_Y_GRAFOS.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/CEREBROS_Y_GRAFOS.md) y [`ENRUTAMIENTO_APIS_Y_COSTO_CERO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/ENRUTAMIENTO_APIS_Y_COSTO_CERO.md).

### 5. Indicadores Semánticos de IA: `thinking-orbs`
* **Ubicación:** [`animaciones ai thinking-orbs/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/animaciones%20ai%20thinking-orbs/)
* **Autor:** [@Jakubantalik](https://github.com/Jakubantalik)
* **Instrucción para el Agente:** En interfaces de IA, sustituir spinners genéricos por esferas de partículas en Canvas 2D a 60 FPS reflejando el estado real (`searching`, `thinking`, `solving`, `composing`). Ver [`GUIA_USO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/animaciones%20ai%20thinking-orbs/GUIA_USO.md).

### 6. Roles Especializados de Negocio: `agency-agents`
* **Ubicación:** [`roles y agentes agency-agents/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/roles%20y%20agentes%20agency-agents/)
* **Autor:** [@msitarzewski](https://github.com/msitarzewski)
* **Instrucción para el Agente:** Cuando el usuario requiera tareas no estrictamente de programación (SEO, Marketing, RH, Contratos/Legal, Pricing SaaS), consultar [`GUIA_ROLES.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/roles%20y%20agentes%20agency-agents/GUIA_ROLES.md) y asumir el rol especializado correspondiente con rigor profesional.

### 7. Gestor de Habilidades: `skills (find-skills)`
* **Ubicación:** [`gestor de skills vercel/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/gestor%20de%20skills%20vercel/)
* **Autor:** [@vercel-labs](https://github.com/vercel-labs)
* **Instrucción para el Agente:** Para buscar e instalar skills comunitarias ligeras en formato `SKILL.md`, utilizar `npx skills find <tema>` o el directorio oficial [skills.sh](https://skills.sh).

### 8. Auditoría de Seguridad & Pentesting: `security-audit-skill`
* **Ubicación:** [`auditoria de seguridad cloudflare/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/auditoria%20de%20seguridad%20cloudflare/)
* **Autor:** [@cloudflare](https://github.com/cloudflare)
* **Instrucción para el Agente:** Antes de desplegar código a producción o abrir endpoints públicos, ejecutar el protocolo de auditoría en 6 fases de Cloudflare (OWASP Top 10, SSRF, IDOR, SQLi, secretos expuestos) verificando siempre con prueba de concepto (PoC) sin falsos positivos. Ver [`GUIA_USO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/auditoria%20de%20seguridad%20cloudflare/GUIA_USO.md).

### 9. Ingeniería Full-Stack & Ciclo TDD: `flujo fullstack ecc`
* **Ubicación:** [`flujo fullstack ecc/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/flujo%20fullstack%20ecc/)
* **Autor:** [@affaan-m](https://github.com/affaan-m)
* **Instrucción para el Agente:** Al afrontar tareas de desarrollo complejas o refactorizaciones de múltiples archivos, aplicar el ciclo en 5 fases de ECC (Planificación ➔ Arquitectura ➔ TDD/Tests First ➔ Implementación Limpia ➔ Code Review) para evitar la degradación de contexto (*context rot*). Ver [`GUIA_USO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/flujo%20fullstack%20ecc/GUIA_USO.md).

### 10. Trilogía de Diseño Frontend & MCPs: `design skills`
* **Ubicación:** [`design skills/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/design%20skills/)
* **Autores:** [@emilkowalski](https://github.com/emilkowalski), [@pbakaus](https://github.com/pbakaus) & [@Leonxlnx](https://github.com/Leonxlnx)
* **Instrucción para el Agente:** Al diseñar interfaces y componentes UI, aplicar la física de resortes (`spring`) de Emil Kowalski, la dirección de arte/tipografía de Impeccable (`/polish`, `/typeset`) y diales anti-slop de Taste-Skill. Utilizar activamente los MCPs de **Figma** (inspección de diseño) y **Playwright** (verificación visual en navegador). Ver [`GUIA_USO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/design%20skills/GUIA_USO.md).

### 11. Ingeniería Inversa Full-Stack (Tráfico/APIs & UI): `mimic`
* **Ubicación:** [`ingenieria inversa ui mimic/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/ingenieria%20inversa%20ui%20mimic/)
* **Autores:** [@littledivy](https://github.com/littledivy) (Tráfico/APIs a SDK Python) & [@sumanrox](https://github.com/sumanrox) (UI/Tokens a DESIGN.md)
* **Instrucción para el Agente:** Para crear wrappers y clientes Python de apps sin API pública, aplicar el flujo de captura de tráfico e intercepción MITM de `littledivy/mimic`. Para extraer sistemas de diseño y estilos visuales basados en URLs, ejecutar el protocolo de extracción de `sumanrox/mimic` (`DESIGN.md` y motion) respetando siempre las directrices de seguridad y propiedad intelectual. Ver [`GUIA_USO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/ingenieria%20inversa%20ui%20mimic/GUIA_USO.md).

### 12. Pentesting Autónomo DevSecOps: `strix`
* **Ubicación:** [`pentesting autonomo strix/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/pentesting%20autonomo%20strix/)
* **Autor:** [@usestrix](https://github.com/usestrix)
* **Instrucción para el Agente:** Cuando se requiera validar la seguridad dinámica (DAST) de una aplicación antes del despliegue o en pipelines CI/CD, consultar la arquitectura de Strix para ejecutar pruebas de penetración en Docker Sandbox, exigir PoCs reproducibles para descartar falsos positivos y aplicar auto-remediación con Pull Requests. Ver [`GUIA_USO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/pentesting%20autonomo%20strix/GUIA_USO.md).

### 13. Automatización Web Ultraligera para IA: `agent-browser`
* **Ubicación:** [`automatizacion navegador agent-browser/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/automatizacion%20navegador%20agent-browser/)
* **Autor:** [@vercel-labs](https://github.com/vercel-labs)
* **Instrucción para el Agente:** Al automatizar tareas de navegación web, scraping o pruebas E2E, preferir el CLI y árbol semántico de accesibilidad de `agent-browser` (`@e1`, `@e2`, etc.) para ahorrar hasta un 90% de tokens y evitar la sobrecarga del contexto del LLM. Ver [`GUIA_USO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/automatizacion%20navegador%20agent-browser/GUIA_USO.md).

### 14. Mapas Interactivos Vectoriales Modernos: `mapcn`
* **Ubicación:** [`mapas interactivos mapcn/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/mapas%20interactivos%20mapcn/)
* **Autor:** [@AnmolSaini16](https://github.com/AnmolSaini16)
* **Instrucción para el Agente:** Al desarrollar mapas interactivos, visualizaciones geoespaciales, selectores de ubicación o dashboards de delivery/rutas, emplear la arquitectura de `mapcn` (MapLibre GL + Tailwind CSS + CartoDB Dark Matter / Positron) con costo cero y marcadores animados a 60 FPS. Ver [`GUIA_USO.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/mapas%20interactivos%20mapcn/GUIA_USO.md) y [`demo.html`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/mapas%20interactivos%20mapcn/demo.html).

---

## 📜 Registro Maestro y Atribución
Consulta siempre [`REPOSITORIOS_SENIOR.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/REPOSITORIOS_SENIOR.md) para ver el catálogo actualizado de herramientas, enlaces oficiales y créditos.



