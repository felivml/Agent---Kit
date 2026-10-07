# 🛡️ Reglas Inmutables de Seguridad y Arquitectura para Sitios Web y Apps con IA

> **Mandato para Desarrolladores y Agentes de IA:**  
> Cuando el código es generado por Inteligencia Artificial (Antigravity, Cursor, Claude Code, Copilot), la IA tiende a priorizar que *"la función ande rápido"* sacrificando la seguridad por defecto.  
> **Todo proyecto web, backend o integración de IA en este workspace DEBE cumplir obligatoriamente con las siguientes reglas inmutables antes de considerarse listo para desarrollo o producción.**

---

## 🧱 1. Row Level Security (RLS) & Aislamiento Estricto de Datos

### ⚠️ El Pecado Común de la IA
La IA crea tablas en bases de datos relacionales (PostgreSQL, Supabase, Neon) y las deja con RLS desactivado o escribe políticas comodín como:
```sql
-- ❌ ERROR FATAL DE IA: Permite que cualquier usuario lea y borre los datos de otros
CREATE POLICY "Public Access" ON documents FOR ALL USING (true);
```

### ✅ Regla Inmutable: RLS Obligatorio por Defecto
1. **Activar RLS en el 100% de las tablas:** Ninguna tabla con datos de usuarios o negocio puede existir sin `ENABLE ROW LEVEL SECURITY`.
2. **Políticas Basadas en Identidad del Token:** Las políticas deben validar siempre el identificador único del usuario autenticado (`auth.uid()`).
3. **Principio de Mínimo Privilegio (CRUD separado):** No usar `FOR ALL` perezoso; separar `SELECT`, `INSERT`, `UPDATE`, `DELETE`.

```sql
-- ✅ ESTÁNDAR SENIOR: RLS Blindado con Políticas Específicas
ALTER TABLE profiles ENABLE ROW LEVEL SECURITY;
ALTER TABLE documents ENABLE ROW LEVEL SECURITY;

-- 1. Lectura: Solo el dueño puede leer sus documentos
CREATE POLICY "Users can select own documents"
ON documents FOR SELECT
TO authenticated
USING (auth.uid() = user_id);

-- 2. Creación: El user_id insertado DEBE ser el del usuario autenticado
CREATE POLICY "Users can insert own documents"
ON documents FOR INSERT
TO authenticated
WITH CHECK (auth.uid() = user_id);

-- 3. Actualización: Solo el dueño puede modificar
CREATE POLICY "Users can update own documents"
ON documents FOR UPDATE
TO authenticated
USING (auth.uid() = user_id)
WITH CHECK (auth.uid() = user_id);

-- 4. Eliminación: Solo el dueño puede borrar
CREATE POLICY "Users can delete own documents"
ON documents FOR DELETE
TO authenticated
USING (auth.uid() = user_id);
```

---

## 🌐 2. Configuración Estricta de CORS (Cross-Origin Resource Sharing)

### ⚠️ El Pecado Común de la IA
Para evitar errores en consola durante el desarrollo local, la IA suele configurar `cors(*)` permitiendo que cualquier dominio malicioso ejecute peticiones autenticadas contra la API del backend.

```javascript
// ❌ ERROR FATAL DE IA: Abre la API al mundo entero
app.use(cors({ origin: '*' }));
```

### ✅ Regla Inmutable: Whitelist Dinámica por Entorno
1. **Nunca usar wildcard `*` en producción:** El origen debe ser una lista blanca (*whitelist*) explícita de dominios controlados.
2. **Manejo estricto de Credenciales / Cookies:** Si se usan cookies o encabezados de autorización (`credentials: true`), el navegador rechaza `*` y requiere un dominio explícito.
3. **Validación de Métodos y Headers permitidos:**

```typescript
// ✅ ESTÁNDAR SENIOR: Configuración Segura de CORS (Node.js / Express / Next.js)
import cors from 'cors';

const allowedOrigins = [
  'https://tudominio.com',
  'https://app.tudominio.com',
  ...(process.env.NODE_ENV === 'development' 
    ? ['http://localhost:3000', 'http://localhost:5173', 'http://127.0.0.1:3000'] 
    : [])
];

const corsOptions: cors.CorsOptions = {
  origin: (origin, callback) => {
    // Permitir peticiones sin origin (ej: mobile apps, curl interno o server-to-server)
    if (!origin || allowedOrigins.includes(origin)) {
      callback(null, true);
    } else {
      callback(new Error(`Bloqueado por política de seguridad CORS: ${origin}`));
    }
  },
  methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE', 'OPTIONS'],
  allowedHeaders: ['Content-Type', 'Authorization', 'X-Requested-With', 'X-CSRF-Token'],
  credentials: true,
  maxAge: 86400 // Cache pre-flight durante 24h para reducir latencia
};

app.use(cors(corsOptions));
```

```python
# ✅ ESTÁNDAR SENIOR: Configuración Segura de CORS (Python / FastAPI)
from fastapi import FastAPI
from fastapi.middleware.cors import CORSMiddleware
import os

app = FastAPI()

origins = [
    "https://tudominio.com",
    "https://app.tudominio.com",
]

if os.getenv("ENVIRONMENT") == "development":
    origins.extend([
        "http://localhost:3000",
        "http://localhost:5173",
        "http://127.0.0.1:8000"
    ])

app.add_middleware(
    CORSMiddleware,
    allow_origins=origins,
    allow_credentials=True,
    allow_methods=["GET", "POST", "PUT", "PATCH", "DELETE", "OPTIONS"],
    allow_headers=["Content-Type", "Authorization", "X-CSRF-Token"],
    max_age=86400,
)
```

---

## 🔑 3. Gestión de Variables de Entorno (`.env`) & Cero Fuga de Secretos

### ⚠️ El Pecado Común de la IA
* La IA pone el prefijo `NEXT_PUBLIC_` o `VITE_` a claves secretas como `OPENAI_API_KEY` o `SUPABASE_SERVICE_ROLE_KEY`, exponiéndolas en el bundle JavaScript que cualquier usuario puede leer en el navegador con *Inspeccionar Elemento*.
* La IA hardcodea contraseñas de bases de datos o secretos JWT directamente en el código fuente.

### ✅ Regla Inmutable: Barrera Cliente-Servidor & Sanitización
1. **Regla de Oro de Prefijos:**
   * `NEXT_PUBLIC_*` o `VITE_*` ➔ **SOLO** para URLs públicas o claves públicas anónimas (ej: `VITE_SUPABASE_ANON_KEY`, `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY`).
   * **PROHIBIDO** prefijar claves maestras (`SERVICE_ROLE_KEY`, `STRIPE_SECRET_KEY`, `OPENAI_API_KEY`, `DATABASE_URL`).
2. **`.gitignore` Obligatorio e Inmediato:**
   Todo `.gitignore` debe contener:
   ```gitignore
   .env
   .env.local
   .env.development.local
   .env.test.local
   .env.production.local
   *.pem
   *.key
   serviceAccountKey.json
   ```
3. **Plantilla `.env.example` Sanitizada:** Siempre crear un `.env.example` documentando cada variable requerida sin valores reales:
   ```env
   # Backend & Database
   DATABASE_URL="postgresql://user:password@host:5432/dbname"
   JWT_SECRET="genera_un_secreto_aleatorio_de_64_caracteres"

   # AI Providers (Solo Servidor)
   OPENAI_API_KEY="sk-proj-..."
   ANTHROPIC_API_KEY="sk-ant-..."

   # Frontend Public Variables
   NEXT_PUBLIC_SUPABASE_URL="https://tuproyecto.supabase.co"
   NEXT_PUBLIC_SUPABASE_ANON_KEY="eyJhbGciOi..."
   ```
4. **Validación de Esquema en Inicio:** Usar **Zod** o **Pydantic** para validar que todas las variables de entorno existan al levantar el servidor. Si falta una variable crítica, el proceso debe fallar inmediatamente (*Fail-Fast*).

---

## 🚦 4. Rate Limiting & Blindaje de Endpoints de IA (Anti-Quiebra)

### ⚠️ El Pecado Común de la IA
Exponer una ruta pública como `/api/chat` o `/api/generate` sin autenticación ni límite de frecuencia. Un atacante o bot puede lanzar 10,000 peticiones en 1 minuto y consumir todo el saldo de tu cuenta de OpenAI/Anthropic.

### ✅ Regla Inmutable: Rate Limiting & Auth en Todo Endpoint Costoso
1. **Rate Limiting por IP y por Usuario:** Implementar limitadores de tasa (ej: 20 peticiones por minuto por IP con Redis o middleware en memoria).
2. **Autenticación Previa:** Exigir sesión antes de permitir llamadas a modelos LLM.
3. **Límite de Tokens (`max_tokens`) y Timeout Estricto:** Fijar siempre un límite máximo de tokens de salida y timeout de conexión.

```typescript
// ✅ ESTÁNDAR SENIOR: Middleware de Rate Limit (Express)
import rateLimit from 'express-rate-limit';

export const aiEndpointLimiter = rateLimit({
  windowMs: 1 * 60 * 1000, // 1 minuto
  max: 15, // Máximo 15 peticiones por ventana
  standardHeaders: true,
  legacyHeaders: false,
  message: {
    status: 429,
    error: 'Has superado el límite de solicitudes de IA. Espera un minuto antes de reintentar.'
  }
});

// Aplicar solo a la ruta de IA
app.use('/api/ai/', aiEndpointLimiter);
```

---

## 🧼 5. Sanitización y Validación Tipada (Zod / Pydantic)

### ⚠️ El Pecado Común de la IA
Confiar ciegamente en `req.body` o usar `as any` en TypeScript, abriendo la puerta a inyecciones SQL, inyecciones de comandos, NoSQL Injections o *Prompt Injection*.

### ✅ Regla Inmutable: Schema-First Validation
Todo endpoint backend debe validar rigurosamente la estructura y tipos de la petición antes de tocar la base de datos o el modelo de IA:

```typescript
// ✅ ESTÁNDAR SENIOR: Validación con Zod
import { z } from 'zod';

export const CreatePromptSchema = z.object({
  prompt: z.string().min(3).max(2000).trim(),
  temperature: z.number().min(0).max(1).default(0.7),
  model: z.enum(['gpt-4o', 'claude-3-5-sonnet', 'gemini-1.5-pro']),
});

// En el controlador
export async function handleAIRequest(req: Request, res: Response) {
  const parseResult = CreatePromptSchema.safeParse(req.body);
  if (!parseResult.success) {
    return res.status(400).json({ errors: parseResult.error.flatten() });
  }
  
  const { prompt, temperature, model } = parseResult.data;
  // Ejecutar lógica segura...
}
```

---

## 🔒 6. Encabezados de Seguridad HTTP (Security Headers)

### ✅ Regla Inmutable: Headers OWASP Obligatorios
Todo servidor web debe incluir los encabezados de protección estándar:
* **`Content-Security-Policy` (CSP):** Evita ejecución de scripts maliciosos (XSS).
* **`X-Content-Type-Options: nosniff`:** Evita que el navegador adivine el tipo MIME.
* **`X-Frame-Options: DENY` o `SAMEORIGIN`:** Protege contra ataques de *Clickjacking*.
* **`Strict-Transport-Security` (HSTS):** Fuerza HTTPS en todas las conexiones.

En Next.js (`next.config.js`):
```javascript
const securityHeaders = [
  { key: 'X-DNS-Prefetch-Control', value: 'on' },
  { key: 'Strict-Transport-Security', value: 'max-age=63072000; includeSubDomains; preload' },
  { key: 'X-Frame-Options', value: 'SAMEORIGIN' },
  { key: 'X-Content-Type-Options', value: 'nosniff' },
  { key: 'Referrer-Policy', value: 'origin-when-cross-origin' }
];

module.exports = {
  async headers() {
    return [{ source: '/(.*)', headers: securityHeaders }];
  }
};
```

---

## 📋 Checklist Rápido de Pre-Despliegue para el Desarrollador Senior

| Área | Verificación | Estado |
|---|---|---|
| **RLS** | ¿Todas las tablas tienen `ENABLE ROW LEVEL SECURITY` y políticas por `auth.uid()`? | 🟢 Obligatorio |
| **CORS** | ¿Se eliminó el wildcard `*` y se configuró una whitelist explícita de dominios? | 🟢 Obligatorio |
| **Secretos** | ¿Se verificó que `.env` está en `.gitignore` y que no hay claves privadas en el frontend? | 🟢 Obligatorio |
| **IA Endpoints** | ¿Tienen Rate Limiting y autenticación para evitar consumo desmedido de saldo? | 🟢 Obligatorio |
| **Validación** | ¿Todos los endpoints validan entradas con Zod / Pydantic y sanitizan datos? | 🟢 Obligatorio |
| **Headers** | ¿El servidor emite cabeceras de seguridad HSTS, CSP y X-Frame-Options? | 🟢 Obligatorio |
