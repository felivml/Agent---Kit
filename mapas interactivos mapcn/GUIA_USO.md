# 🗺️ Guía Maestra: Mapcn (Mapas Interactivos Modernos & Open Source)

Esta guía documenta la integración de **`mapcn`** por **Anmol Saini** ([@AnmolSaini16](https://github.com/AnmolSaini16)), el estándar de componentes de mapas estilo **shadcn/ui** basados en **MapLibre GL / OpenStreetMap** y **Tailwind CSS**.

---

## 🏛️ Filosofía y Arquitectura de Mapcn

```
                                      MOTOR MAPCN
                                           │
         ┌─────────────────────────────────┴─────────────────────────────────┐
         ▼                                                                   ▼
【 MOTOR DE RENDERIZADO 】                                           【 CAPA DE ESTILOS & UI 】
• MapLibre GL / OpenStreetMap                                       • Tailwind CSS + shadcn/ui
• Tiles Gratuitos (CartoDB Dark/Positron)                           • Marcadores animados (Pulse effect)
• Cero API Keys obligatorias                                        • Popups interactivos con cards
• Renderizado a 60 FPS por GPU                                      • Selector de temas (Dark / Light / Satellite)
```

---

## 🛠️ Instalación & Configuración

### 1. Instalación de Dependencias Core (React / Next.js / Vite)
```bash
npm install maplibre-gl @types/maplibre-gl lucide-react clsx tailwind-merge
```

### 2. Estilos Globales de MapLibre (en `index.css` o `globals.css`)
```css
@import "maplibre-gl/dist/maplibre-gl.css";
```

---

## 🚀 Componentes Clave de Mapcn

### 1️⃣ Mapa Base con Modo Oscuro (Zero Config)

```tsx
import React, { useEffect, useRef } from 'react';
import maplibregl from 'maplibre-gl';

export function MapComponent({ center = [-74.0721, 4.7110], zoom = 12 }) {
  const mapContainer = useRef(null);

  useEffect(() => {
    if (!mapContainer.current) return;

    const map = new maplibregl.Map({
      container: mapContainer.current,
      style: 'https://basemaps.cartocdn.com/gl/dark-matter-gl-style/style.json', // Dark Mode
      center: center,
      zoom: zoom,
    });

    map.addControl(new maplibregl.NavigationControl(), 'top-right');

    return () => map.remove();
  }, [center, zoom]);

  return (
    <div className="relative w-full h-[500px] rounded-2xl overflow-hidden border border-white/10 shadow-2xl">
      <div ref={mapContainer} className="w-full h-full" />
    </div>
  );
}
```

---

### 2️⃣ Marcador Pulsante con Card Interactiva

```tsx
// Crear un marcador HTML personalizado con efecto pulse
const el = document.createElement('div');
el.className = 'relative flex items-center justify-center';
el.innerHTML = `
  <span class="absolute w-6 h-6 bg-blue-500 rounded-full animate-ping opacity-75"></span>
  <span class="relative w-3 h-3 bg-blue-400 border-2 border-white rounded-full shadow-lg"></span>
`;

new maplibregl.Marker({ element: el })
  .setLngLat([-74.0721, 4.7110])
  .setPopup(
    new maplibregl.Popup({ offset: 25 }).setHTML(`
      <div class="p-3 bg-zinc-900 text-white rounded-xl border border-zinc-800">
        <h4 class="font-bold text-sm">Sede Bogotá</h4>
        <p class="text-xs text-zinc-400 mt-1">Operaciones activas 24/7</p>
      </div>
    `)
  )
  .addTo(map);
```

---

## 🎨 Fuentes de Tiles Open Source y Gratuitas (Costo Cero)

| Estilo | URL del Estilo MapLibre | Apariencia |
| :--- | :--- | :--- |
| **Dark Matter (Recomendado)** | `https://basemaps.cartocdn.com/gl/dark-matter-gl-style/style.json` | Fondo oscuro elegante para dashboards SaaS. |
| **Positron (Light)** | `https://basemaps.cartocdn.com/gl/positron-gl-style/style.json` | Fondo claro minimalista. |
| **Voyager** | `https://basemaps.cartocdn.com/gl/voyager-gl-style/style.json` | Colores vivos con puntos de interés. |
| **OpenStreetMap Raster** | `https://tile.openstreetmap.org/{z}/{x}/{y}.png` | Estándar libre mundial. |

---

## 🎯 ¿Cuándo usar Mapcn en lugar de Google Maps?

* ✅ **Cero Facturación Sorpresa:** No tienes que poner tarjeta de crédito en Google Cloud para que no te bloqueen el mapa.
* ✅ **Estética Cohesiva con Tailwind & shadcn/ui:** Las tarjetas, modales y popups heredan el sistema de diseño exacto de tu aplicación.
* ✅ **Alto Rendimiento por GPU:** MapLibre GL renderiza vectores fluidos a 60 FPS sin saturar la CPU.

---

## 🚀 Demo Interactiva en el Workspace

Puedes abrir y probar en vivo el mapa interactivo con marcadores, selector de capas y controles en:
👉 **[`mapas interactivos mapcn/demo.html`](file:///d:/Program%20Files/Felipe/Downloads/Agent%20-%20Kit/mapas%20interactivos%20mapcn/demo.html)**

---

*Este documento forma parte del Toolkit Senior de Antigravity para interfaces geoespaciales y mapas interactivos.*
