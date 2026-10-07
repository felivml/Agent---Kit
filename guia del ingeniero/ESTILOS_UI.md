# 🎨 Catálogo Maestro: Estilos de Diseño UI & Tendencias Visuales

Este documento constituye la enciclopedia definitiva de estilos visuales modernos para diseño de interfaces de usuario (UI), compilando las directrices estéticas, fórmulas matemáticas en CSS/Tailwind, advertencias de usabilidad y plantillas de prompts para agentes de Inteligencia Artificial.

> 📱 **Créditos y Referencia de Origen:**
> * **Fuente / Video de Inspiración:** [TikTok @ZSbqKXAna](https://vt.tiktok.com/ZSbqKXAna/)
> * **Compilación y Estandarización:** Senior Toolkit Hub (Antigravity & Google DeepMind).

---

## 🏛️ Los 9 Grandes Estilos Visuales de la UI Moderna

```
                                      ENCICLOPEDIA DE ESTILOS UI
                                                  │
         ┌──────────────────┬─────────────────────┼─────────────────────┬──────────────────┐
         ▼                  ▼                     ▼                     ▼                  ▼
  【 NEUMORFISMO 】   【 GLASSMORFISMO 】   【 CLAYMORFISMO 】   【 BRUTALISMO / NEO 】  【 BENTO GRID 】
  (Superficie 3D)     (Vidrio Translúcido)   (Plastilina 3D)      (Bordes 4px & Sombra 0) (Cuadrícula Apple)
         │                  │                     │                     │                  │
         └──────────────────┼─────────────────────┴─────────────────────┼──────────────────┘
                            ▼                                           ▼
                   【 MINIMALISMO / MAX 】                        【 UI ESPACIAL / LIQUID 】
                   (Espacio vs Saturación)                       (VisionOS & Vidrio Fluido)
```

---

## 1. 🫧 Neumorfismo (Soft UI)

* **Concepto:** La interfaz simula nacer extruida o hundida desde la misma superficie. El fondo del componente es idéntico al fondo de la pantalla y la ilusión 3D se logra con **doble `box-shadow`** (luz en una esquina y sombra en la opuesta).
* **Herramienta de Referencia:** [neumorphism.io](https://neumorphism.io/) (por Adam Giebl).
* **Fórmula CSS:**
  ```css
  /* Superficie Extruida */
  .neumorphic-card {
    border-radius: 24px;
    background: #e0e0e0;
    box-shadow: 20px 20px 60px #bebebe, -20px -20px 60px #ffffff;
  }
  /* Estado Presionado / Hundido */
  .neumorphic-inset {
    border-radius: 24px;
    background: #e0e0e0;
    box-shadow: inset 20px 20px 60px #bebebe, inset -20px -20px 60px #ffffff;
  }
  ```
* **Ideal para:** Diales de IoT/Domótica, reproductores de audio, calculadoras y tarjetas táctiles.

---

## 2. 🪟 Glassmorfismo (Glassmorphism)

* **Concepto:** Efecto de **vidrio esmerilado translúcido** flotante sobre fondos coloridos o gradientes dinámicos, utilizando desenfoque de fondo (*backdrop blur*), bordes sutiles de 1px y sombras difusas.
* **Fórmula CSS:**
  ```css
  .glass-card {
    background: rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 20px;
    box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
  }
  ```
* **Ideal para:** Modales flotantes, barras de navegación fijas (*sticky navbars*), tarjetas sobre fondos con gradientes vivos y dashboards oscuros modernos.

---

## 3. 🧸 Claymorfismo (Claymorphism)

* **Concepto:** Efecto de **plastilina inflable o arcilla 3D** con esquinas ultra redondeadas, sombras internas suaves para darle volumen cilíndrico/esférico y sombras inferiores flotantes. Transmite un tono amigable y lúdico.
* **Fórmula CSS:**
  ```css
  .clay-card {
    background: #f3f4f6;
    border-radius: 32px;
    box-shadow: 
      12px 12px 24px rgba(0, 0, 0, 0.12),
      inset -8px -8px 16px rgba(0, 0, 0, 0.08),
      inset 8px 8px 16px rgba(255, 255, 255, 0.85);
  }
  ```
* **Ideal para:** Aplicaciones educativas, Web3 lúdica, gamificación, apps infantiles y plataformas de onboarding interactivo.

---

## 4. 📐 Neo-Brutalismo (Neo-Brutalism / Pop-Brutalism)

* **Concepto:** Ruptura intencional de la delicadeza visual. Utiliza **bordes negros gruesos (2px a 4px)**, **sombras duras sin desenfoque (`blur: 0`)**, colores de alto impacto saturados (amarillo canario, violeta eléctrico, verde lima) y tipografía grotesca en negrita.
* **Fórmula CSS:**
  ```css
  .neo-brutalist-btn {
    background: #fde047; /* Amarillo brillante */
    border: 3px solid #000000;
    border-radius: 12px;
    box-shadow: 5px 5px 0px #000000;
    font-weight: 800;
    transition: all 0.15s ease;
  }
  .neo-brutalist-btn:hover {
    transform: translate(-2px, -2px);
    box-shadow: 7px 7px 0px #000000;
  }
  .neo-brutalist-btn:active {
    transform: translate(3px, 3px);
    box-shadow: 2px 2px 0px #000000;
  }
  ```
* **Ideal para:** Marcas juveniles, productos de desarrollo/dev-tools (estilo Gumroad o Figma retro), blogs de diseño y portafolios disruptivos.

---

## 5. 🍱 Bento Grid (Estilo Apple / Linear)

* **Concepto:** Organización de contenidos en una **cuadrícula asimétrica modular** inspirada en las bandejas japonesas Bento. Cada tarjeta tiene un tamaño diferente según su importancia jerárquica (1x1, 2x1, 2x2), con esquinas redondeadas amplias y fondos sutiles.
* **Fórmula CSS (Grid):**
  ```css
  .bento-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: 240px;
    gap: 16px;
  }
  .bento-item-large {
    grid-column: span 2;
    grid-row: span 2;
  }
  .bento-card {
    background: #18181b;
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 24px;
    padding: 24px;
    overflow: hidden;
  }
  ```
* **Ideal para:** Secciones de características (*Feature Showcase*) en SaaS, landing pages de hardware (Apple) y dashboards analíticos (Linear, Raycast).

---

## 6. 🌌 UI Espacial (Spatial UI / VisionOS Style)

* **Concepto:** Interfaces diseñadas para la computación espacial (VR/AR). Utilizan **profundidad real en el eje Z**, iluminación reactiva que sigue la mirada o el cursor, bordes ultra finos con reflejos metálicos y capas flotantes superpuestas.
* **Fórmula CSS:**
  ```css
  .spatial-surface {
    background: radial-gradient(circle at 50% 0%, rgba(255, 255, 255, 0.12), rgba(255, 255, 255, 0.02));
    backdrop-filter: blur(28px) saturate(180%);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 36px;
    box-shadow: 
      0 20px 50px rgba(0, 0, 0, 0.5),
      inset 0 1px 1px rgba(255, 255, 255, 0.4);
    transform: perspective(1000px) translateZ(20px);
  }
  ```
* **Ideal para:** Interfaces futuristas, experiencias inmersivas 3D, aplicaciones de inteligencia artificial y paneles de control inmersivos.

---

## 7. 💧 Liquid Glass (Vidrio Líquido & Refracción Fluida)

* **Concepto:** Evolución avanzada del glassmorfismo que incorpora **distorsiones ópticas de refracción, ondas orgánicas y gradientes animados** que parecen interactuar como líquido bajo un vidrio esmerilado.
* **Fórmula CSS (con Filtro SVG de Turbulencia):**
  ```css
  .liquid-glass {
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.15), rgba(255, 255, 255, 0.03));
    backdrop-filter: blur(20px) contrast(120%) brightness(110%);
    border: 1px solid rgba(255, 255, 255, 0.25);
    border-radius: 28px;
    box-shadow: 0 15px 35px rgba(31, 38, 135, 0.2);
  }
  ```
* **Ideal para:** Elementos decorativos Hero, fondos interactivos de landing pages y marcas de cosmética o diseño de alta gama.

---

## 8. ⚪ Minimalismo Riguroso (Swiss / Clean UI)

* **Concepto:** Eliminación total de lo innecesario. Se apoya en una **arquitectura tipográfica impecable**, contrastes en blanco y negro puros, espaciados generosos (*whitespace*) y jerarquía estricta sin adornos ni sombras superfluas.
* **Fórmula CSS:**
  ```css
  .minimal-card {
    background: #ffffff;
    border: 1px solid #e5e7eb;
    border-radius: 8px;
    padding: 32px;
    font-family: 'Inter', sans-serif;
  }
  .minimal-heading {
    letter-spacing: -0.03em;
    font-weight: 600;
    color: #111827;
  }
  ```
* **Ideal para:** Sitios editoriales, documentación técnica, herramientas de productividad pura (iA Writer) y firmas legales/financieras tradicionales.

---

## 9. 💥 Maximalismo (Maximalism / Expressive UI)

* **Concepto:** Opuesto al minimalismo. Utiliza **múltiples capas de color, tipografías expresivas combinadas, texturas densas, micro-animaciones constantes y alta saturación**. La filosofía es *"Más es Más"*.
* **Fórmula CSS:**
  ```css
  .maximal-card {
    background: linear-gradient(45deg, #ff007a, #7928ca, #0070f3);
    background-size: 300% 300%;
    animation: gradientShift 6s ease infinite;
    border-radius: 20px;
    color: #ffffff;
    padding: 28px;
  }
  @keyframes gradientShift {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }
  ```
* **Ideal para:** Eventos musicales, festivales de arte, campañas de marketing de moda urbana y lanzamientos virales.

---

## 🧠 Matriz Comparativa y Cuándo Elegir Cada Estilo

| Estilo UI | Personalidad | Rendimiento | Accesibilidad (WCAG) | Complejidad CSS |
|---|---|---|---|---|
| **Neumorfismo** | Táctil, Suave, Discreto | ⚡ Rápido | ⚠️ Media (Requiere acentos) | 🟢 Baja |
| **Glassmorfismo** | Futurista, Elegante, Moderno | 🟡 Medio (Usa GPU) | 🟢 Alta (Bien contrastado) | 🟡 Media |
| **Claymorfismo** | Lúdico, Inflable, Amigable | ⚡ Rápido | 🟢 Alta | 🟡 Media |
| **Neo-Brutalismo** | Rebelde, Audaz, Retro | ⚡ Ultra Rápido | 🟢 Máxima (Contraste 21:1) | 🟢 Muy Baja |
| **Bento Grid** | Ordenado, Premium, Apple-like | ⚡ Ultra Rápido | 🟢 Máxima | 🟡 Media (CSS Grid) |
| **UI Espacial** | Inmersivo, VisionOS, Z-Axis | 🔴 Pesado (3D/Blur) | 🟢 Alta | 🔴 Alta |
| **Liquid Glass** | Fluido, Orgánico, Artesanal | 🔴 Pesado (Shaders/SVG) | 🟡 Media | 🔴 Alta |
| **Minimalismo** | Sobrio, Atemporal, Limpio | ⚡ Ultra Rápido | 🟢 Máxima | 🟢 Muy Baja |
| **Maximalismo** | Vibrante, Intenso, Expresivo | 🟡 Medio | ⚠️ Media (Cuidar fondos) | 🟡 Media |

---

## 🚀 Plantilla Maestra de Invocación para Agentes de IA

Cuando ordenes una interfaz en cualquier estilo visual:

```markdown
### 🎨 Orden de Estilo UI para el Agente

**Estilo Seleccionado:** [Glassmorfismo / Neo-Brutalismo / Bento Grid / Neumorfismo / Claymorfismo]
**Paleta:** [Colores base y acentos contrastantes]
**Reglas:**
1. Aplica las fórmulas matemáticas de sombras, bordes y backdrop-filter documentadas en `ESTILOS_UI.md`.
2. Asegura cumplimiento WCAG AAA en todos los textos y estados interactivos.
3. Mantén la semántica HTML5 pura y animaciones a 60 FPS.
```

---

*Este documento forma parte de la Guía del Ingeniero del workspace como enciclopedia de diseño de interfaces de clase mundial.*
