# 🎨 Diseño de Prompts para UI & Bibliotecas DESIGN.md

Este documento forma parte de la **Guía del Ingeniero** y reúne las mejores **bibliotecas web de prompts de diseño, generadores de `DESIGN.md` y recursos de inspiración UI/UX** para que cualquier agente de IA o desarrollador cree interfaces de nivel mundial eliminando el "AI slop".

---

## 🌐 1. Bibliotecas Web de Prompts UI & Sistemas de Diseño para IA

Estas plataformas proporcionan sistemas de diseño, prompts estructurados y código listo para herramientas de IA (Cursor, Claude Code, v0, Lovable, Antigravity):

| Plataforma | Especialidad | Enlace Oficial | Qué aporta a la IA |
|---|---|---|---|
| **Neumorphism.io** | Generador de Sombras 3D & Soft UI | [neumorphism.io](https://neumorphism.io/) | Genera código CSS exacto para sombras dobles, curvaturas, superficies cóncavas/convexas y botones extruidos/hundidos. Ver catálogo de estilos: [`ESTILOS_UI.md`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/guia%20del%20ingeniero/ESTILOS_UI.md). |
| **MotionSites.ai** | Prompts para webs animadas & 3D | [motionsites.ai](https://motionsites.ai/) | Biblioteca de prompts ultra detallados (paletas, curvas de aceleración, hero sections y 3D) para generar webs interactivas en asistentes de código. |
| **Refero Styles** | 2,000+ Design Systems legibles por IA | [styles.refero.design](https://styles.refero.design/) | Genera archivos `DESIGN.md` listos para copiar con paletas, tipografía, espaciados y componentes de webs líderes. |
| **21st.dev** | El "NPM" de componentes para IA | [21st.dev](https://21st.dev/) | Catálogo de componentes modernos (Tailwind + React + Framer Motion) listos para copiar directo al prompt. |
| **Refero Design** | Flujos completos de productos SaaS | [refero.design](https://refero.design/) | Capturas de flujos reales (onboarding, pricing, dashboards) para usar como referencia visual en prompts. |
| **Godly** | Inspiración de alta artesanía web | [godly.website](https://godly.website/) | Las landing pages con mejores animaciones, tipografía y diseño interactivo del mundo. |
| **Mobbin** | Patrones de apps móviles y web | [mobbin.com](https://mobbin.com/) | Auditoría visual de más de 300,000 pantallas de aplicaciones reales (Stripe, Linear, Airbnb). |
| **Component Gallery** | Enciclopedia de componentes UI | [component.gallery](https://component.gallery/) | Muestra cómo diseñan botones, modales y tablas las mejores empresas del mundo. |
| **UI-UX Pro Max (Local)** | Motor offline de 192 reglas y tokens | [`diseño frontend ui-ux/`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/diseño%20frontend%20ui-ux/) | Motor local del workspace para generar tokens CSS y evitar antipatrones por industria. |

---

## 📄 2. ¿Qué es el estándar `DESIGN.md` y por qué es vital para la IA?

Un archivo **`DESIGN.md`** en la raíz de un proyecto actúa como el **"Manual de Marca y Reglas Visuales"** que la IA lee antes de escribir cualquier línea de HTML, CSS o React.

Evita que la IA adivine colores genéricos (azul plano, gris aburrido) y la obliga a usar la paleta exacta, fuentes y espaciados de tu producto:

### 📐 Anatomía de un `DESIGN.md` Profesional:

```markdown
---
tokens:
  colors:
    background: "#09090b"
    card: "#18181b"
    primary: "#6366f1"
    text_main: "#f4f4f5"
    text_muted: "#a1a1aa"
    border: "rgba(255, 255, 255, 0.08)"
  typography:
    heading_font: "Outfit, sans-serif"
    body_font: "Inter, sans-serif"
    mono_font: "JetBrains Mono, monospace"
  radii:
    card: "16px"
    button: "10px"
---

# Reglas de Diseño Visual
1. **Jerarquía:** Solo un <h1> por página, títulos con tracking ajustado (-0.02em).
2. **Botones:** Estados hover sutiles con transition de 0.2s, nunca usar colores planos sin gradiente o borde suave.
3. **Contraste:** Todo texto secundario debe cumplir ratio de contraste WCAG AAA (mínimo 4.5:1).
```

---

## 🎯 3. Plantillas de Prompts de UI de Alto Nivel (Copy-Paste)

### 🚀 Plantilla A: Landing Page de Producto de Alto Impacto (Estilo Linear / Apple)
```markdown
Diseña una landing page moderna con estética 'Dark Mode Premium'.
- Tipografía: Títulos en Outfit (peso 800, tracking -0.03em) y texto en Inter.
- Fondo: #09090b con un sutil glow radial púrpura/índigo de fondo.
- Componentes:
  1. Hero con píldora superior ('✨ Novedad v2.0'), título con gradiente blanco a gris y 2 botones (Primario con brillo suave, Secundario con borde sutil).
  2. Grid de características asimétricas (Bento Grid) con bordes de 1px en rgba(255,255,255,0.08) y fondo glassmorphism.
  3. Micro-animaciones en hover con transform: translateY(-2px).
- Evita: Colores saturados genéricos, sombras duras y botones cuadrados sin radio.
```

### 📊 Plantilla B: Dashboard SaaS FinTech / Analytics
```markdown
Construye una interfaz de dashboard financiero con máxima densidad de información y legibilidad:
- Paleta: Fondo #0c0f17, tarjetas #131826, acentos en Esmeralda (#10b981) para ganancias y Rosa (#f43f5e) para pérdidas.
- Tipografía: Números en fuente tabular monoespaciada (JetBrains Mono) para alineación perfecta de cifras decimales.
- Componentes:
  1. Header con selector de rango de fechas y buscador rápido.
  2. 4 KPIs principales con indicador de tendencia porcentual (↑ +12.4%).
  3. Gráfico de área suave y tabla de transacciones recientes con badges de estado redondeados.
```

---

## 💡 Flujo de Trabajo Senior para Nuevos Proyectos
1. **Explorar:** Entra a [styles.refero.design](https://styles.refero.design/) o [godly.website](https://godly.website/) y elige el estilo visual que encaja con el negocio.
2. **Extraer:** Copia los tokens o genera el `DESIGN.md` del estilo seleccionado.
3. **Instruir:** Pega el `DESIGN.md` en tu repositorio y dale la orden a la IA: *"Construye la siguiente pantalla respetando estrictamente los tokens de DESIGN.md"*.

---

*Este documento es extensible. Puedes agregar nuevos enlaces de inspiración y librerías de prompts a medida que los descubras.*
