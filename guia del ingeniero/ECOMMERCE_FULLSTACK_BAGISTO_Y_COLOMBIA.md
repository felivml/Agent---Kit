# 🛒 Manual de Ingeniería: Bagisto eCommerce (Laravel + Vue) y Adaptación para Colombia

Este documento establece el estándar arquitectónico y la justificación técnica para el uso de **Bagisto** como la solución definitiva de comercio electrónico Open Source. Explica por qué **nunca se debe programar un eCommerce desde cero**, cómo instalarlo y cómo adaptarlo al 100% para el mercado colombiano cumpliendo la normativa fiscal y legal (SIC, DIAN, Habeas Data).

---

## 🧠 ¿Por qué usar Bagisto en lugar de programar desde cero? (Principio Anti-Sobreingeniería)

Programar un eCommerce completo desde cero requiere entre **4 y 8 meses de trabajo** (modelado de base de datos de variantes, pasarelas de pago, cálculo de impuestos, checkout seguro, panel administrativo, autenticación, carritos y control de stock).

> [!IMPORTANT]
> **Regla de Oro Senior (YAGNI & Reutilización):**
> Nunca reinventes la rueda. Bagisto ya resuelve el 95% de la infraestructura de comercio electrónico con la arquitectura más limpia del ecosistema PHP (**Laravel 11 + Vue.js + Tailwind CSS**). El rol del ingeniero es personalizar, conectar pasarelas y entregar valor en días, no en meses.

---

## 🏛️ Arquitectura Full-Stack de Bagisto

```
                                    BAGISTO ECOMMERCE ENGINE
                                               │
        ┌──────────────────────────────────────┴──────────────────────────────────────┐
        ▼                                                                             ▼
【 1. FRONTEND STOREFRONT (Público) 】                               【 2. ADMIN DASHBOARD (Privado) 】
• Catálogo con filtros dinámicos (Vue.js + Tailwind)                • Gestión de Inventario Multi-Almacén
• Página de inicio personalizable (Theme Customizer)                • Control de Pedidos y Envíos
• Checkout en 1 solo paso con cálculo de IVA                        • Cupones, Descuentos y Promociones
• Área "Mi Cuenta" para clientes (Rastreo y Facturas)               • Configuración de Pasarelas y Monedas
• 100% Responsive para móviles y tablets                            • Módulo CMS para Políticas Legales
```

---

## 🇨🇴 Adaptación Legal, Fiscal y Pasarelas de Pago para Colombia

Bagisto se adapta al 100% a la legislación colombiana sin costos ocultos:

| Área en Colombia | Requisito Legal / Fiscal | ¿Cómo se configura en Bagisto? |
| :--- | :--- | :--- |
| **Protección de Datos** | **Habeas Data (Ley 1581 de 2012):** Consentimiento expreso de datos. | Casilla (*checkbox*) obligatoria de aceptación en registro y checkout. |
| **Estatuto del Consumidor** | **Ley 1480:** Derecho de retracto (5 días), garantías y PQR. | Módulo CMS para publicar la página de *Términos y Condiciones*. |
| **Enlace Oficial SIC** | Exigencia de enlace visible a `www.sic.gov.co`. | Enlace directo en el footer configurable desde el panel. |
| **Impuestos (IVA)** | IVA general del 19% o 5% desglosado. | Regla de impuestos en `Configuración > Impuestos > Tarifa 19%`. |
| **Pasarelas de Pago** | Pagos en pesos colombianos (`COP $`) con PSE, Nequi y Tarjetas. | Integración con **Wompi (Bancolombia), MercadoPago Colombia, Bold o ePayco**. |
| **Facturación DIAN** | Factura electrónica obligatoria. | Conexión vía Webhook/API a Siigo, Alegra o Dataico. |

---

## 📜 Licencia MIT: Cero Comisiones y Soberanía Total

* **Sin Mensualidades:** A diferencia de Shopify ($39+ USD/mes), Bagisto es **gratuito de por vida**.
* **0% de Comisiones por Venta:** Todo el margen de ganancia es para el negocio.
* **White Label (Marca Blanca):** Puedes cambiar logos, personalizar la página de inicio al 100% y vendérselo a clientes como tu propio desarrollo profesional.

---

## 🚀 Guía de Instalación Paso a Paso

### Requisitos Previos:
* PHP 8.2 o superior (con extensiones `pdo_mysql`, `mbstring`, `intl`, `gd`, `curl`).
* Composer 2.x instalado.
* Base de datos MySQL 8.0+ o MariaDB.
* Node.js 18+ y NPM.

### 1. Crear el Proyecto con Composer
```bash
composer create-project bagisto/bagisto mi-tienda-online
cd mi-tienda-online
```

### 2. Configurar Base de Datos (`.env`)
Edita el archivo `.env` con las credenciales de tu base de datos:
```env
APP_NAME="Mi Tienda Colombia"
APP_ENV=production
APP_URL=https://mitienda.com

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=bagisto_db
DB_USERNAME=root
DB_PASSWORD=tu_password
```

### 3. Ejecutar el Instalador Automático
```bash
# Ejecuta migraciones, seeders y compila assets
php artisan bagisto:install
```

### 4. Iniciar el Servidor Local
```bash
php artisan serve
```
* **Tienda Pública:** `http://localhost:8000`
* **Panel de Administración:** `http://localhost:8000/admin` (usar credenciales creadas durante la instalación).

---

## 🎨 Personalización de la Página de Inicio

1. **Desde el Panel de Control (Sin Código):**
   * Ve a `Configuración > Temas > Personalizar`.
   * Agrega carruseles de banners promocionales, cuadrículas de categorías, productos más vendidos y promociones por temporada.
2. **Desde el Código Fuente (Con Blade y Tailwind):**
   * Modifica las vistas en `packages/Webkul/Shop/src/Resources/views/home/index.blade.php`.
   * Aplica componentes personalizados o animaciones interactivas libremente.

---

*Este documento forma parte de la Guía del Ingeniero del workspace como directriz oficial para proyectos de comercio electrónico.*
