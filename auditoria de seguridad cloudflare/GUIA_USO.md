# 🛡️ Guía de Auditoría de Seguridad: Cloudflare Security Audit Skill

El **Cloudflare Security Audit Skill** es el estándar de auditoría de código desarrollado por **Cloudflare** para agentes de IA y desarrolladores que necesitan evaluar la seguridad de un proyecto antes de desplegarlo a producción.

---

## 🎯 ¿Por qué este método elimina los "Falsos Positivos"?

| Auditoría de IA Tradicional ❌ | Auditoría Cloudflare Security Skill ✅ |
|---|---|
| Genera listas interminables de advertencias teóricas o falsos positivos. | Exige **evidencia real**: solo reporta vulnerabilidades si puede demostrar una ruta explotable. |
| Revisa archivos al azar sin entender el flujo de datos. | Mapea el flujo completo: desde la entrada del usuario (`request`), pasando por la lógica de negocio, hasta la base de datos (`sink`). |
| No propone soluciones concretas. | Proporciona el código de mitigación exacto y una prueba para verificar que el fallo quedó cerrado. |

---

## 🧭 Las 6 Fases del Protocolo de Seguridad

```
  ┌───────────────────────┐
  │ 1. RECONOCIMIENTO     │ ➔ Identifica endpoints públicos, inputs de usuario y dependencias.
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 2. PLAN DE COBERTURA  │ ➔ Clasifica archivos por nivel de riesgo (Auth, DB, Pagos, API).
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 3. CAZA DIRIGIDA      │ ➔ Busca vectores OWASP: SQLi, SSRF, IDOR/BOLA, XSS, Secretos.
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 4. VALIDACIÓN (PoC)   │ ➔ Descarta falsos positivos construyendo la prueba de concepto.
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 5. REPORTE SEVERIDAD  │ ➔ Clasificación CVSS (Crítica, Alta, Media) con remediación paso a paso.
  └──────────┬────────────┘
             ▼
  ┌───────────────────────┐
  │ 6. VERIFICACIÓN POST  │ ➔ Re-escanea el código tras aplicar el parche para confirmar la solución.
  └───────────────────────┘
```

---

## 📦 Vectores de Ataque Auditados

1. **Inyección & Sanitización:** SQL Injection, NoSQL Injection, Command Injection, XSS (Cross-Site Scripting).
2. **Autenticación & Autorización:** Control de Acceso Roto (IDOR / BOLA), JWT mal firmados o sin expiración, elevación de privilegios.
3. **Fugas de Información Crítica:** API Keys o credenciales *hardcoded*, variables `.env` expuestas al frontend, logs con datos sensibles.
4. **Red & Servidor:** SSRF (Server-Side Request Forgery), CORS mal configurado (`*` con credenciales), Open Redirects.
5. **Dependencias Vulnerables:** Paquetes npm/pip con CVEs conocidos o versiones obsoletas.

---

## 🚀 Instalación y Uso

### 1. Instalación mediante el Gestor de Skills
```bash
npx skills add https://github.com/cloudflare/security-audit-skill --skill security-audit
```

### 2. Plantilla de Invocación Directa para la IA
Para solicitar una auditoría formal en cualquier proyecto, ejecuta el siguiente prompt en tu agente:

```markdown
### 🛡️ Iniciar Auditoría de Seguridad Cloudflare

**Objetivo:** Auditar la seguridad del repositorio/carpeta `./src` siguiendo el protocolo Cloudflare Security Audit.

**Reglas de Ejecución:**
1. Ejecuta la Fase 1 (Reconocimiento) mapeando todas las entradas no confiables del usuario y rutas públicas.
2. Identifica cualquier vector de riesgo (SQLi, IDOR, SSRF, XSS, secretos expuestos).
3. Para cada hallazgo, proporciona:
   - **Severidad:** (Crítica / Alta / Media / Baja).
   - **Archivo y Línea:** Ubicación exacta.
   - **Explicación del Riesgo:** Cómo un atacante podría explotarlo.
   - **Código de Remediación:** El código corregido y seguro.
4. No reportes problemas de estilo; enfócate exclusivamente en vulnerabilidades explotables con evidencia.
```

---

## 🌐 Enlaces Oficiales
* **Repositorio GitHub:** [github.com/cloudflare/security-audit-skill](https://github.com/cloudflare/security-audit-skill)
* **Web Oficial de Cloudflare:** [cloudflare.com](https://www.cloudflare.com)

---

*Este documento forma parte del Toolkit Senior de Antigravity para garantizar despliegues seguros y libres de vulnerabilidades.*
