# 🧬 Guía Maestra: Suite Mimic (Ingeniería Inversa de APIs y UI)

Esta guía documenta la suite de **Ingeniería Inversa con IA** compuesta por **Divy Srivastava** ([@littledivy](https://github.com/littledivy) - Deno Core) para **APIs/Tráfico de Red** y **Suman Roy** ([@sumanrox](https://github.com/sumanrox)) para **Diseño y UI Visual**.

---

## 🏛️ Las Dos Vertientes de Mimic

```
                                INGENIERÍA INVERSA CON IA
                                            │
        ┌───────────────────────────────────┴───────────────────────────────────┐
        ▼                                                                       ▼
【 1. littledivy/mimic 】                                              【 2. sumanrox/mimic 】
(Tráfico de Red ➔ SDK Python)                                        (Frontend ➔ DESIGN.md & UI)
• Intercepta con mitmproxy                                           • Inspección headless con Playwright
• Captura tokens/cookies de sesión                                   • Extrae CSS Computed y variables
• Claude genera cliente Python tipado                                • Reconstruye layout, motion y WebGL
```

---

## 🛠️ 1. Mimic por @littledivy: De Tráfico de Red a Librería en Python

### ¿Cómo Funciona?
1. **Intercepción HTTP/HTTPS:** Inicia un proxy local (`mitmproxy`) que captura todas las solicitudes y respuestas mientras navegas o interactúas con la web o aplicación.
2. **Extracción de Autenticación:** Extrae cabeceras de autorización (`Authorization: Bearer ...`), cookies de sesión y tokens anti-CSRF.
3. **Generación con Claude:** Pasa la secuencia de endpoints y esquemas JSON a Claude para generar un módulo de Python tipado y limpio.

### Instalación & Ejecución
```bash
# Clonar y ejecutar mimic de littledivy
git clone https://github.com/littledivy/mimic.git
cd mimic
cargo run # o mediante su CLI oficial
```

### Ejemplo de Salida Generada (`client.py`)
```python
import requests

class AppClient:
    def __init__(self, token="<capturado_automaticamente>"):
        self.base_url = "https://api.empresa.com/v1"
        self.headers = {"Authorization": f"Bearer {token}"}

    def get_dashboard(self):
        res = requests.get(f"{self.base_url}/metrics", headers=self.headers)
        return res.json()
```

---

## 🎨 2. Mimic por @sumanrox: De URL a Sistema de Diseño (`DESIGN.md`)

### Instalación vía Gestor de Skills
```bash
npx skills add https://github.com/sumanrox/mimic --skill mimic
```

### Flujo de Trabajo
1. **Inspección de DOM & CSS:** Extrae la paleta cromática exacta calculada por el navegador, espaciados y jerarquía tipográfica.
2. **Curvas de Movimiento:** Captura transiciones y aceleraciones Bézier para animaciones fluidas a 60 FPS.
3. **Generación de `DESIGN.md`:** Produce un archivo de especificaciones listo para que cualquier agente construya la UI con fidelidad de píxel.

---

## ⚖️ Directrices Éticas y de Seguridad Senior

> [!CAUTION]
> **Seguridad y Términos de Servicio (ToS):**
> * **Uso Autorizado:** Utiliza estas herramientas únicamente sobre tus propias cuentas, entornos de prueba, APIs públicas o para fines de aprendizaje e investigación de seguridad.
> * **Certificate Pinning:** Aplicaciones móviles nativas con *certificate pinning* estricto bloquearán proxies MITM sin certificados personalizados instalados a nivel de sistema.
> * **Propiedad Intelectual:** No utilices código o recursos gráficos propietarios de terceros para suplantación de identidad o competencia desleal.

---

*Este documento forma parte del Toolkit Senior de Antigravity para ingeniería inversa y desarrollo avanzado.*
