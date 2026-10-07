# 🎨 Guía Maestra: Design Skills & Trilogía Frontend Anti-Slop

Esta guía documenta la suite de **Design Skills** creada por los mejores diseñadores de producto e ingenieros de interacción del mundo (**Emil Kowalski**, **Paul Bakaus** y **Leon Lin**), y cómo se combina con los **MCPs de Figma y Playwright** para crear interfaces al nivel de Stripe, Linear y Vercel.

---

## 🏛️ La Trilogía de Diseño Frontend Senior

```
                       ARQUITECTURA DE DISEÑO & EXPERIENCIA
                                         │
    ┌────────────────────────────────────┼────────────────────────────────────┐
    ▼                                    ▼                                    ▼
【 1. EMIL KOWALSKI 】               【 2. IMPECCABLE 】                 【 3. TASTE-SKILL 】
(Micro-animaciones & Física)         (Dirección de Arte & Tipografía)     (Anti-Slop Dials & Asimetría)
• Física de resortes (Springs)       • Jerarquía y escala tipográfica     • Dial DESIGN_VARIANCE (1-10)
• Estados interactivos y táctiles    • Comandos: /polish, /typeset       • Dial MOTION_INTENSITY (1-10)
• Cero saltos bruscos a 60 FPS       • Auditoría de contrastes WCAG       • Asimetría y layouts modernos
```

---

## 🛠️ Detalle de las 3 Skills y sus Comandos

### 1️⃣ Emil Kowalski: Design Engineering & Micro-Interacciones
* **Autor:** **Emil Kowalski** ([@emilkowalski](https://github.com/emilkowalski))
* **Instalación:**
  ```bash
  npx skills add https://github.com/emilkowalski/skills --skill emil-design-eng
  ```
* **Reglas de Oro:**
  - **Física Real:** Las animaciones usan curvas de resorte (*spring physics*) con amortiguación suave (`damping: 20`, `stiffness: 100`).
  - **Feedback Inmediato:** Cada botón y tarjeta debe responder visualmente al `hover`, `active` y `focus-visible`.
  - **Continuidad Espacial:** Los modales y drawers no aparecen de la nada; escalan o emergen desde el origen del click.

---

### 2️⃣ Impeccable: Dirección de Arte para la IA
* **Autor:** **Paul Bakaus** ([@pbakaus](https://github.com/pbakaus))
* **Instalación:**
  ```bash
  npx skills add https://github.com/pbakaus/impeccable --skill impeccable
  ```
* **Comandos Clave de Pulido:**
  - `/polish`: Inspecciona el espaciado, bordes y sombras para alinearlos con el diseño general.
  - `/typeset`: Ajusta la jerarquía tipográfica, el `letter-spacing` y la longitud de línea (máximo 65-75 caracteres por renglón).
  - `/audit`: Evalúa contrastes de color según accesibilidad WCAG AAA y elimina elementos redundantes.

---

### 3️⃣ Taste-Skill: Diales de Personalidad y Anti-Slop
* **Autor:** **Leon Lin** ([@Leonxlnx](https://github.com/Leonxlnx))
* **Instalación:**
  ```bash
  npx skills add https://github.com/Leonxlnx/taste-skill --skill taste
  ```
* **Diales Numéricos Configurables:**
  ```yaml
  DESIGN_VARIANCE: 8   # (1=Genérico/Bootstrap, 10=Vanguardista/Asimétrico)
  MOTION_INTENSITY: 7  # (1=Estático, 10=Ultra interactivo)
  VISUAL_DENSITY: 6    # (1=Minimalista espaciado, 10=Alta densidad FinTech)
  ```

---

## 🔌 El Poder de los MCPs Activos en Antigravity

La combinación de estas skills con los **Model Context Protocols (MCP)** de tu IDE cierra el ciclo de diseño perfecto:

1. 🎯 **Figma MCP (`mcp/figma`):**
   * El agente lee los componentes, colores, medidas en píxeles y tipografías directamente de tu archivo Figma sin que tengas que describirlos manualmente.
2. 🎭 **Playwright MCP (`mcp/playwright`):**
   * El agente abre un navegador real en segundo plano, toma una captura de pantalla (*screenshot*), verifica el renderizado a nivel de píxel y comprueba que no haya saltos visuales ni bugs de interacción.

---

## 🚀 Plantilla de Invocación para el Agente

Cuando quieras construir o rediseñar una interfaz con este nivel de excelencia:

```markdown
### 🎨 Orden de Diseño Frontend Senior (Trilogía Anti-Slop)

**Misión:** Diseña y programa el siguiente componente/página aplicando la Trilogía de Diseño Senior:
1. **Dirección de Arte (Impeccable):** Jerarquía tipográfica estricta, un solo <h1>, tracking ajustado (-0.02em) y bordes de 1px sutiles con sombras suaves.
2. **Interacciones (Emil Kowalski):** Micro-animaciones con física de resorte (spring), estados hover fluidos (transition 0.2s) y feedback táctil inmediato.
3. **Personalidad (Taste-Skill):** DESIGN_VARIANCE=8, composición asimétrica (Bento Grid) y paleta con contrastes cuidados (WCAG AAA).
4. **Verificación:** Si hay Playwright activo, valida el resultado con un screenshot del navegador.
```

---

*Este documento forma parte del Toolkit Senior de Antigravity para diseño de interfaces de clase mundial.*
