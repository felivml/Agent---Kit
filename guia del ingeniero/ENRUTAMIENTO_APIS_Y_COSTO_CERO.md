# 🔀 Enrutamiento de IA, Alta Disponibilidad y APIs Gratuitas (Costo Cero)

Este documento forma parte de la **Guía del Ingeniero** y explica cómo estructurar un entorno de desarrollo con Inteligencia Artificial **ilimitado, de alta velocidad y costo cero**, resolviendo caídas por rate limits (429) y optimizando el consumo de tokens.

---

## 🎯 Arquitectura: La Sinergia entre OmniRoute y Free LLM APIs

Para programar con agentes o IDEs (Cursor, Claude Code, Antigravity, VS Code) sin pagar suscripciones costosas ni sufrir bloqueos, combinamos dos piezas clave:

```
┌─────────────────────────────────────────────────────────────────┐
│  🎁 1. FREE LLM APIS (El Combustible Gratuito)                  │
│  Gemini Flash (Free) + Groq (Free) + OpenRouter (Free) + Cerebras│
└──────────────────────────────┬──────────────────────────────────┘
                               │  (Se alimentan en cascada)
                               ▼
┌─────────────────────────────────────────────────────────────────┐
│  🔀 2. OMNIROUTE PROXY (El Enrutador Inteligente Local)         │
│  • Auto-fallback automático ante error 429 o caída de API       │
│  • Compresión de tokens RTK+Caveman (ahorro 15% a 95%)          │
│  • Endpoint OpenAI compatible (http://localhost:20128/v1)       │
└──────────────────────────────┬──────────────────────────────────┘
                               │
                               ▼
     🚀 IDEs / AGENTES: Cursor, Claude Code, Antigravity, Cline
```

---

## 🎁 Catálogo de Proveedores Gratuitos (Free LLM APIs)

Los siguientes proveedores ofrecen **niveles gratuitos permanentes (Free Tiers) o créditos sin tarjeta de crédito**:

| Proveedor | Modelo Recomendado | Límite Gratuito | Especialidad Senior | Enlace Oficial |
|---|---|---|---|---|
| **Google AI Studio** | `Gemini 2.0 Flash` | 15 RPM / 1M tokens context | Ventana de contexto masiva para leer proyectos enteros | [aistudio.google.com](https://aistudio.google.com/) |
| **Groq Cloud** | `Llama 3.3 70B / DeepSeek` | 30 RPM / 6K TPM | Inferencia ultra rápida (500+ tokens/segundo) | [console.groq.com](https://console.groq.com/) |
| **OpenRouter** | Modelos con tag `:free` | Rotación ilimitada | Acceso gratuito a DeepSeek R1, Mistral y Gemma | [openrouter.ai](https://openrouter.ai/) |
| **Cerebras AI** | `Llama 3.1 8B / 70B` | 30 RPM | Velocidad instantánea en chips Wafer-Scale | [cerebras.ai](https://cerebras.ai/) |
| **Cloudflare Workers AI** | `Llama 3.2 / Qwen` | 10,000 neuronas/día | Inferencia Edge distribuida con baja latencia | [developers.cloudflare.com](https://developers.cloudflare.com/workers-ai/) |

---

## 🔀 OmniRoute: El Enrutador Local y Conmutación por Error

* **Autor:** **Diego Souza** ([@diegosouzapw](https://github.com/diegosouzapw))
* **Repositorio en GitHub:** [github.com/diegosouzapw/OmniRoute](https://github.com/diegosouzapw/OmniRoute)
* **Web Oficial:** [omniroute.online](https://omniroute.online)

### ¿Qué problemas resuelve?
1. **Auto-Fallback (Conmutación por Error):** Si Google Gemini o Groq alcanzan el límite de 15/30 peticiones por minuto, OmniRoute conmuta automáticamente al siguiente proveedor en milisegundos sin cortar la sesión del programador.
2. **Compresión RTK + Caveman:** Comprime el texto y contexto redundante ahorrando entre **15% y 95%** de tokens.
3. **100% Local y Privado:** Corre en tu propia máquina (`localhost:20128`), por lo que tus API Keys y código fuente jamás pasan por servidores intermediarios en la nube.

---

## 🚀 Guía de Configuración Paso a Paso (5 Minutos)

### Paso 1: Obtener tus API Keys Gratuitas
1. Ve a [Google AI Studio](https://aistudio.google.com/) y genera tu API Key gratuita.
2. Ve a [Groq Console](https://console.groq.com/) y genera tu API Key gratuita.
3. Ve a [OpenRouter](https://openrouter.ai/) y genera tu API Key para modelos gratuitos.

### Paso 2: Iniciar OmniRoute en tu Máquina
```bash
# Opción con npx (rápida)
npx omniroute

# O con Docker (producción local)
docker run -d -p 20128:20128 --name omniroute diegosouzapw/omniroute:latest
```

### Paso 3: Configurar la Cascada de Fallback en el Dashboard
Abre `http://localhost:20128` en tu navegador y agrega tus claves:
* **Prioridad 1:** Groq (`Llama 3.3 70B`) ➔ Máxima velocidad.
* **Prioridad 2:** Google (`Gemini 2.0 Flash`) ➔ Contexto masivo si Groq satura su RPM.
* **Prioridad 3:** OpenRouter (`:free`) ➔ Respaldo de seguridad.

### Paso 4: Conectar tu IDE o Agente
En cualquier herramienta de desarrollo (Cursor, Claude Code, Antigravity, Cline, VS Code):
* **Base URL:** `http://localhost:20128/v1`
* **API Key:** `sk-local-omniroute` (o cualquier texto)

---

## 📋 Resumen de Beneficios para el Ingeniero

| Criterio | Desarrollo Tradicional | Arquitectura OmniRoute + Free APIs |
|---|---|---|
| **Costo Mensual** | $20 - $100 USD en tokens | **$0 USD (100% Gratuito)** |
| **Resiliencia** | Si la API se cae, el trabajo se detiene | **Auto-fallback transparente sin interrupción** |
| **Velocidad** | Sujeta al tráfico del proveedor | **Balanceo inteligente al proveedor más rápido** |
| **Privacidad** | Proxies externos de terceros | **Proxy 100% local en tu hardware** |

---

*Este documento forma parte del Toolkit Senior de Antigravity para diseño de infraestructuras resilientes y flujos de desarrollo a costo cero.*
