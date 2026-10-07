# 🔮 Guía de Uso: Thinking Orbs (Animaciones Semánticas para IA)

**Thinking Orbs** es una biblioteca de componentes visuales creada por **Jakub Antalík** diseñada para interfaces de Inteligencia Artificial, chatbots y agentes autónomos.

---

## 🎯 ¿Por qué usar Thinking Orbs en lugar de un Spinner normal?

| Spinner Convencional ❌ | Thinking Orb Semántico ✅ |
|---|---|
| Rueda genérica de carga ("cargando...") | Esfera de partículas 3D reactiva y orgánica. |
| No comunica qué está pasando internamente. | Comunica el **estado exacto** del agente (`searching`, `thinking`, `composing`). |
| Sensación de lentitud o bloqueo. | Sensación de "vida", fluidez y procesamiento inteligente a 60 FPS. |

---

## 🎨 Los 9 Estados Semánticos

1. **`idle`**: Respiración sutil en reposo, esperando la entrada del usuario.
2. **`listening`**: Onda expansiva suave que reacciona mientras el usuario habla o escribe.
3. **`searching`**: Partículas en barrido radial/dispersión buscando información en bases de datos o web.
4. **`thinking`**: Núcleo rotatorio denso procesando lógica interna.
5. **`solving`**: Órbita acelerada con partículas convergiendo hacia el centro para tomar una decisión.
6. **`composing` / `shaping`**: Partículas organizándose geométricamente mientras se redacta la respuesta.
7. **`speaking`**: Modulación rítmica sincronizada con síntesis de voz / streaming de audio.
8. **`working`**: Patrón constante de cálculo en segundo plano.
9. **`pulsing`**: Destello de atención o notificación de éxito.

---

## 🛠️ Guía de Adaptación por Framework (Universal)

Al ser una animación matemática basada en `<canvas>` 2D, se adapta de forma natural a **cualquier stack tecnológico**:

---

### 1️⃣ React / Next.js / Remix
* **Instalación:** `npm install thinking-orbs`
* **Next.js (App Router):** Requiere `'use client'` porque interactúa con el DOM y `requestAnimationFrame`.

```tsx
'use client';
import { ThinkingOrb } from 'thinking-orbs';

export function AgentOrb({ status }: { status: 'thinking' | 'searching' | 'idle' }) {
  return <ThinkingOrb state={status} size="small" />;
}
```

---

### 2️⃣ Vue 3 / Nuxt 3
En Vue, puedes encapsular el `<canvas>` dentro de un componente con `onMounted` y `watch`:

```vue
<script setup>
import { ref, onMounted, onUnmounted, watch } from 'vue';

const props = defineProps({
  state: { type: String, default: 'thinking' } // idle, searching, thinking, etc.
});

const canvasRef = ref(null);
let animationId = null;

onMounted(() => {
  const ctx = canvasRef.value.getContext('2d');
  // Iniciar loop de partículas en canvas
});

onUnmounted(() => {
  if (animationId) cancelAnimationFrame(animationId);
});
</script>

<template>
  <div class="agent-orb-wrapper">
    <canvas ref="canvasRef" width="120" height="120"></canvas>
  </div>
</template>
```

---

### 3️⃣ Svelte / SvelteKit
En Svelte, se monta limpiamente en el ciclo de vida `onMount`:

```svelte
<script>
  import { onMount } from 'svelte';
  export let status = 'thinking';

  let canvas;
  onMount(() => {
    const ctx = canvas.getContext('2d');
    // Loop de partículas Canvas
  });
</script>

<canvas bind:this={canvas} width="120" height="120"></canvas>
```

---

### 4️⃣ Vanilla JS / Astro / PHP / Laravel / HTML Puro
Cero compiladores, cero Node.js. Copias el `<canvas>` y el bloque `<script>` de [`demo.html`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/animaciones%20ai%20thinking-orbs/demo.html) y funciona de inmediato en cualquier navegador a 60 FPS.

---

## 🌐 Implementación Base en Canvas (Vanilla JS 60 FPS)

```html
<canvas id="orbCanvas" width="120" height="120"></canvas>

<script>
  const canvas = document.getElementById('orbCanvas');
  const ctx = canvas.getContext('2d');
  const numParticles = 80;
  const particles = [];

  // Generar coordenadas sobre esfera 3D
  for (let i = 0; i < numParticles; i++) {
    const theta = Math.random() * Math.PI * 2;
    const phi = Math.acos((Math.random() * 2) - 1);
    particles.push({ theta, phi, radius: 40 });
  }

  let angle = 0;
  function animate() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    const cx = canvas.width / 2;
    const cy = canvas.height / 2;
    angle += 0.02;

    particles.forEach(p => {
      // Proyección matemática 3D a 2D
      const x = p.radius * Math.sin(p.phi) * Math.cos(p.theta + angle);
      const y = p.radius * Math.sin(p.phi) * Math.sin(p.theta + angle);
      const z = p.radius * Math.cos(p.phi);

      const scale = (z + 60) / 100;
      const alpha = Math.max(0.2, (z + 40) / 80);

      ctx.beginPath();
      ctx.arc(cx + x, cy + y, 2.2 * scale, 0, Math.PI * 2);
      ctx.fillStyle = `rgba(139, 92, 246, ${alpha})`;
      ctx.fill();
    });

    requestAnimationFrame(animate);
  }
  animate();
</script>
```

---

## ⚡ Buenas Prácticas Senior
1. **Accesibilidad:** Incluye siempre un `aria-live="polite"` y `aria-label="El asistente está pensando"` en el contenedor para lectores de pantalla.
2. **Consumo de Batería:** Pausa la animación con `cancelAnimationFrame` cuando la pestaña esté en segundo plano (`document.visibilityState === 'hidden'`).
3. **Escala:** Usa el tamaño `small` (20-24px) para indicadores inline al lado del texto y `regular` (64-120px) para avatares principales del asistente.
