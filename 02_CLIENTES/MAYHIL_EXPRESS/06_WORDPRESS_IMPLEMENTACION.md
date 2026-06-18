# WordPress — Plan de Implementación · Mayhil Express

| Campo | Valor |
|-------|-------|
| **Agente** | 08_WORDPRESS_DEVELOPER |
| **Fecha** | 2026-06-17 |
| **Versión** | 1.0 |
| **Estado** | Listo para desarrollo |
| **Inputs** | Brief v3.1 · PRD v3.0 · SEO Plan v1.0 · Wireframes v1.0 · Copy v1.0 |
| **Dominio** | mayhilexpress.com |
| **Principio rector** | Configurar antes de programar · JetEngine antes de código · Performance primero |

---

# PARTE I — ANÁLISIS TÉCNICO

## 1. Lectura del proyecto

### ¿Qué necesita el proyecto?

| Componente | Necesidad | Herramienta |
|-----------|-----------|-------------|
| 19 páginas estáticas (10 ES + 9 EN) | CMS con pages + multiidioma | WordPress Pages + WPML |
| Formulario B2B 11 campos | Formulario con notificaciones + tracking | Fluent Forms + GTM |
| WhatsApp flotante diferenciado por página | Widget con mensajes configurables | WP Social Chat |
| Design system negro/amarillo + Inter | Constructor visual con global styles | Elementor Pro |
| Header y footer globales | Theme Builder | Elementor Pro |
| Galería de flota H350 | Campos personalizados + galería | ACF (Advanced Custom Fields) |
| SEO on-page + schema + sitemap | SEO plugin completo | Rank Math Pro |
| Multiidioma ES/EN + hreflang | Gestión de traducciones | WPML |
| Analytics + tracking de conversiones | Tag Manager + Analytics | GTM + GA4 |
| Performance: CWV ≥ 75 | Caché + CDN + optimización imágenes | LiteSpeed Cache + Cloudflare |
| HTTPS + seguridad básica | Cloudflare + hardening WP | Cloudflare + config WP |
| Social proof condicional (logos vs texto) | Condición simple — visible/oculto | Elementor Conditions |

### ¿Qué puede resolverse sin código?

| Funcionalidad | Solución sin código |
|---------------|---------------------|
| Formulario B2B con notificaciones | Fluent Forms con notificaciones nativas |
| Header sticky | Elementor Theme Builder + CSS position: sticky |
| WhatsApp diferenciado | WP Social Chat → mensajes por URL de página |
| FAQ accordion | Elementor Widget Accordion |
| Galería flota | ACF Gallery Field + Elementor dinámico |
| Social proof condicional | Dos secciones en Elementor: mostrar/ocultar manualmente |
| Sitemap XML | Rank Math automático |
| Schema markup | Rank Math → configuración por página |
| hreflang ES/EN | WPML nativo |
| Google Maps embed | iFrame HTML embed en Elementor (sin plugin) |
| Breadcrumbs | Rank Math Breadcrumbs |
| Open Graph images | Rank Math → imagen por página |

### ¿Qué requiere código personalizado?

| Funcionalidad | Por qué requiere código | Prioridad |
|---------------|------------------------|-----------|
| Evento GTM `whatsapp_click` | WP Social Chat no dispara dataLayer nativo | Alta |
| Evento GTM `form_submit` con datos del formulario | Fluent Forms hook → GTM dataLayer push | Alta |
| Shortcode para mostrar/ocultar social proof | Alternativa si Elementor Conditions no es suficiente | Media |
| Custom CSS global para variables de diseño | Los tokens CSS del design system como `:root` variables | Alta |
| Función para inyectar hreflang alternativo | WPML ya lo maneja, pero verificar en head | Baja |

**Conclusión técnica:** Este proyecto puede implementarse en ~90% con configuración (plugins + Elementor). El código personalizado se limita a tracking GTM y Custom CSS tokens.

---

## 2. Decisiones técnicas del implementador

| Decisión | Opción elegida | Justificación |
|----------|---------------|---------------|
| JetEngine / Crocoblock | **No activar en Fase 1** | Estructura es simple (páginas estáticas). ACF suficiente para galería de flota |
| ACF vs metaboxes nativos | **ACF** | PRD lo exige. Mejor DX. Compatible con Elementor dinámico en Fase 2 |
| WPML vs Polylang | **WPML** | PRD lo recomienda. Mayor compatibilidad con Elementor Pro y Fluent Forms |
| WooCommerce | **No** | Fuera de alcance Fase 1 |
| Custom Post Types | **No (Fase 1)** | Solo 1 vehículo (H350). CPT de flota se aplaza a Fase 2 si se amplía flota |
| Plugin de seguridad | **No instalar en Fase 1** | Cloudflare + configuración WordPress hardening básico es suficiente. Evitar plugin extra |
| Plugin de optimización de imágenes | **Imagify** (alternativa: ShortPixel) | Integración LiteSpeed, WebP automático, compresión bulk |
| Backup | **UpdraftPlus** | Backup antes de lanzamiento. Configurar post-desarrollo |

---

# PARTE II — ARQUITECTURA WORDPRESS

## 3. Configuración WordPress Core

### Ajustes generales

| Opción | Valor |
|--------|-------|
| Título del sitio | Mayhil Express |
| Descripción | Transporte de Personal y Movilidad Corporativa en Lima |
| URL de WordPress | `https://mayhilexpress.com` |
| URL del sitio | `https://mayhilexpress.com` |
| Dirección de email | servicio@mayhilexpress.com |
| Zona horaria | America/Lima |
| Formato de fecha | d/m/Y |
| Idioma | Español (Perú) |

### Ajustes de lectura

| Opción | Valor |
|--------|-------|
| La portada muestra | Una página estática → seleccionar página "Inicio" |
| Página de entradas | Sin asignar (blog desactivado en Fase 1) |
| Visibilidad en motores de búsqueda | **Desmarcar** "Solicitar a los motores de búsqueda que no indexen este sitio" |

### Ajustes de escritura

| Opción | Valor |
|--------|-------|
| Categoría de entradas predeterminada | Desactivar (sin blog) |
| Pingbacks / Trackbacks | **Desactivar** |

### Ajustes de comentarios

| Opción | Valor |
|--------|-------|
| Permitir comentarios | **Desactivar** en todo el sitio |
| Permitir trackbacks y pingbacks | **Desactivar** |

### Estructura de permalinks

```
Configuración → URL permanentes
Seleccionar: Nombre de la entrada (/postname/)
Personalizado si es necesario: /%postname%/
```

**Nota:** La estructura `/postname/` permite que las páginas queden como `/nosotros/`, `/cobertura/` etc. El hub de servicios `/servicios/` se configura como **página padre** de todas las páginas de servicio.

### Estructura de páginas en el CMS

```
WordPress Pages — ES
├── Inicio (página de portada)
├── Nosotros
├── Servicios [página padre — sin contenido propio, redirige a hijos]
│   ├── Transporte de Personal [slug: transporte-de-personal]
│   ├── Transporte Corporativo [slug: transporte-corporativo]
│   ├── Traslado al Aeropuerto [slug: traslado-aeropuerto]
│   ├── Transporte Turístico [slug: transporte-turistico]
│   └── Transporte para Grupos [slug: transporte-grupos]
├── Cobertura
├── Preguntas Frecuentes [slug: preguntas-frecuentes]
└── Contacto

WordPress Pages — EN (gestionadas por WPML)
├── Home [/en/]
├── About Us [/en/about/]
├── Services [página padre EN]
│   ├── Staff Transport [/en/services/staff-transport/]
│   ├── Airport Transfer [/en/services/airport-transfer/]
│   └── Tour Transport [/en/services/tour-transport/]
├── Coverage [/en/coverage/]
├── FAQ [/en/faq/]
└── Contact [/en/contact/]
```

**Nota slug — `/servicios/`:** La página padre "Servicios" tiene slug `servicios`. Las páginas hijas heredan: `/servicios/transporte-de-personal/`, etc. Configurar la página padre como template **en blanco** o redirigir a la primera página hija (Transporte de Personal).

### Roles y usuarios WordPress

| Usuario | Rol | Propósito |
|---------|-----|-----------|
| Administrador agencia | Administrador | Desarrollo y configuración completa |
| Iván Mayorga (cliente) | Editor | Edición de contenido sin acceso a configuración |

**Nota seguridad:** Crear usuario administrador separado para el cliente con nombre de usuario no obvio. Cambiar el usuario admin por defecto.

---

# PARTE III — PLUGINS — STACK COMPLETO

## 4. Plugins requeridos

### Obligatorios — Fase 1

| Plugin | Rol | Tipo | Notas |
|--------|-----|------|-------|
| **Elementor Pro** | Constructor de páginas y Theme Builder | Premium | Incluye versión Free. Requiere licencia Pro para Theme Builder |
| **Rank Math Pro** | SEO, schema, sitemaps, breadcrumbs, OG | Premium | Rank Math Free tiene limitaciones en schema tipo Service |
| **Fluent Forms** | Formulario B2B con notificaciones | Free/Pro | La versión Free es suficiente para el formulario B2B |
| **ACF (Advanced Custom Fields)** | Campos personalizados para galería de flota | Free | La versión Pro no es necesaria en Fase 1 |
| **WPML** | Gestión multiidioma ES/EN + hreflang | Premium | Requiere: WPML Multilingual CMS + WPML String Translation |
| **WP Social Chat** | Widget WhatsApp flotante con mensajes por página | Free | Ex: Click to Chat for WhatsApp |
| **LiteSpeed Cache** | Caché de página, minificación, lazy load | Free | Solo funciona al 100% en hosting LiteSpeed/OpenLiteSpeed |
| **Imagify** | Optimización de imágenes + conversión a WebP | Free/Pro | Plan free: 25 MB/mes. Pro recomendado para subidas masivas |
| **UpdraftPlus** | Backup pre-lanzamiento | Free | Backup único antes de lanzamiento |
| **Google Site Kit** | Conexión GA4 + Search Console desde WordPress | Free | Alternativa a insertar GTM manualmente |

### Alternativos / Contingencia

| Plugin | Reemplaza a | Cuándo usar |
|--------|------------|-------------|
| Polylang | WPML | Si el cliente no quiere pagar WPML (~$99/año) |
| ShortPixel | Imagify | Si Imagify tiene problemas con el hosting |
| WP Rocket | LiteSpeed Cache | Si el hosting no es LiteSpeed (Apache/Nginx) |
| Smush | Imagify | Plan gratuito sin límite de tamaño |

### NO instalar

| Plugin | Por qué no |
|--------|-----------|
| Yoast SEO | Ya usamos Rank Math — nunca dos plugins SEO |
| Wordfence / iThemes Security | Cloudflare + hardening básico es suficiente. Los plugins de seguridad pesados afectan rendimiento |
| Jetpack | Demasiado pesado para lo que necesitamos |
| Contact Form 7 | Ya usamos Fluent Forms |
| WooCommerce | Fuera de alcance Fase 1 |
| Slider Revolution / WOW Slider | Afecta Core Web Vitals gravemente |
| Google Analytics para WordPress | Ya usamos GTM manualmente |

### Versiones mínimas requeridas

| Tecnología | Versión mínima |
|-----------|----------------|
| WordPress | 6.4+ |
| PHP | 8.1+ |
| MySQL | 8.0+ (MariaDB 10.6+ también válido) |
| RAM hosting | 2 GB mínimo (4 GB recomendado) |
| Disco | 10 GB mínimo |

---

# PARTE IV — ESTRUCTURA ELEMENTOR PRO

## 5. Configuración Global — Antes de diseñar

### 5.1 Colores Globales (Global Colors)

*Configurar en Elementor → Global Fonts & Colors antes de crear ninguna sección.*

| Nombre | Color HEX | Uso |
|--------|-----------|-----|
| Primary — Amarillo Mayhil | `#F5C400` | CTAs primarios, botones, acentos, íconos |
| Dark — Negro Mayhil | `#111111` | Navbar, hero, fondos premium, títulos |
| White | `#FFFFFF` | Fondos, texto sobre negro |
| Gray Light | `#F5F5F5` | Fondos alternos de sección |
| Gray Text | `#444444` | Párrafos y descripciones |
| Gray Mid | `#888888` | Labels, metadata, texto secundario |
| WhatsApp Green | `#25D366` | Botón WhatsApp, confirmaciones |
| Border | `#E5E5E5` | Bordes de tarjetas, separadores |

### 5.2 Fuentes Globales (Global Fonts)

| Rol | Fuente | Peso | Tamaño Desktop | Tamaño Mobile |
|-----|--------|------|---------------|---------------|
| Primary Heading | Inter | 800 | 52px | 34px |
| Secondary Heading | Inter | 700 | 38px | 28px |
| Text | Inter | 400 | 17px | 16px |
| Accent | Inter | 600 | 14px | 13px |

*Inter: cargar desde Google Fonts en Elementor → Ajustes tipografía globales.*

### 5.3 Configuración de Breakpoints

| Breakpoint | Valor |
|-----------|-------|
| Desktop | 1200px+ |
| Tablet | 768px |
| Mobile | 390px (iPhone 15 Pro) |

*Configurar en Elementor → Ajustes → Responsive → Custom Breakpoints.*

### 5.4 Ajustes de contenedor

```
Elementor → Ajustes → Características → Contenedores Flexbox → ACTIVAR
(Esta es la forma moderna — no usar columnas clásicas)

Ancho del contenedor: 1200px
Padding lateral container: desktop 80px / tablet 40px / mobile 24px
```

### 5.5 CSS Custom Properties (variables globales)

Agregar en Elementor → Custom CSS (o en child theme → style.css):

```css
/* Variables del sistema de diseño — Mayhil Express */
:root {
  --color-primary: #F5C400;
  --color-dark: #111111;
  --color-white: #FFFFFF;
  --color-gray-light: #F5F5F5;
  --color-gray-text: #444444;
  --color-whatsapp: #25D366;
  --color-border: #E5E5E5;
  --space-xs: 8px;
  --space-sm: 16px;
  --space-md: 24px;
  --space-lg: 48px;
  --space-xl: 80px;
  --container: 1200px;
  --border-radius: 4px;
}
```

---

## 6. Theme Builder — Plantillas Globales

### 6.1 Header

| Parámetro | Valor |
|-----------|-------|
| Tipo | Header |
| Condición de visualización | Todo el sitio |
| Posición | Fixed (sticky) |
| Fondo | `#111111` negro |
| Z-index | 9999 |
| Altura | 72px desktop / 60px mobile |

**Estructura del Header:**

```
Contenedor Flexbox [space-between · align-center · full-width]
├── Logo [imagen · amarillo/blanco · 140px ancho · enlace a Home]
├── Menú principal (desktop) [flex · gap 32px]
│   ├── Servicios [dropdown con 5 servicios]
│   ├── Nosotros
│   ├── Cobertura
│   └── Preguntas Frecuentes
└── CTA [botón amarillo "Solicitar Cotización" · enlace a #formulario-cotizacion o /contacto/]

Mobile (< 768px):
├── Logo [izquierda]
└── Hamburger Menu [derecha · color blanco → drawer lateral oscuro]
    Drawer incluye: Servicios (expandible), Nosotros, Cobertura, FAQ, [SOLICITAR COTIZACIÓN]
```

**Nota multiidioma:** WPML añade el selector de idioma. Configurar en WPML → Language Switcher → integrar en el header como ítem de menú o icono flotante.

### 6.2 Footer

| Parámetro | Valor |
|-----------|-------|
| Tipo | Footer |
| Condición de visualización | Todo el sitio |
| Fondo | `#111111` negro |
| Texto | `#FFFFFF` blanco |

**Estructura del Footer:**

```
Footer [fondo negro · padding 64px 0 32px]
├── Sección superior [4 columnas · gap 48px]
│   ├── Col 1: Logo blanco + tagline "Movilidad corporativa en Lima."
│   ├── Col 2: SERVICIOS [lista: Transporte Personal · Corporativo · Aeropuerto · Turístico · Grupos]
│   ├── Col 3: EMPRESA [lista: Nosotros · Cobertura · FAQ · Contacto]
│   └── Col 4: CONTACTO [teléfono · email · botón WhatsApp verde]
├── Separador horizontal [1px · #333333]
└── Sección inferior [copyright + política de privacidad]
    "© 2026 Mayhil Express · Lima, Perú"

Mobile: 1 columna · stack vertical · logo arriba · links abajo · contacto al final
```

### 6.3 Plantilla de Página de Servicio (reutilizable)

Crear como Template de Página en Elementor → guardar como "Plantilla Servicio Base".

Usar en: Corporativo, Aeropuerto, Turístico, Grupos, Cobertura.

**Estructura de la plantilla:**

```
[HEADER GLOBAL — Theme Builder]
├── Breadcrumb (Rank Math shortcode)
├── HERO [fondo negro · 60vh] — H1 + subtítulo + CTA
├── DESCRIPCIÓN [2 col · texto izq · foto H350 der]
├── CARACTERÍSTICAS [3 col · 3 íconos + beneficio]
├── CTA PRINCIPAL [B2B → formulario | B2C → WhatsApp]
├── SERVICIOS RELACIONADOS [3 tarjetas]
└── [FOOTER GLOBAL — Theme Builder]
```

---

## 7. Global Widgets y Secciones Globales

Los siguientes componentes se crean **una sola vez** y se reutilizan vía Global Widget o Global Section de Elementor, para que un cambio se propague a todas las páginas.

| Widget Global | Usado en | Contenido |
|--------------|---------|-----------|
| **Formulario Cotización B2B** | Home, Transporte Personal, Contacto | Fluent Forms embed + badge + título |
| **Sección Social Proof** | Home, Transporte Personal | Logos SEDAPAL/CLARO/MOVISTAR + fallback |
| **Trust Bar** | Home, Transporte Personal | 5 íconos + texto (GPS · 24/7 · 17 pax · Lima+ · 5 años) |
| **CTA Banner Final** | Todas las páginas internas | Fondo amarillo · headline · botón cotización |
| **Sección Cobertura Teaser** | Home | 4 zonas geográficas + CTA a /cobertura/ |

**Procedimiento para crear Global Widget en Elementor:**
1. Diseñar el widget en cualquier página
2. Clic derecho → "Guardar como global"
3. Darle nombre descriptivo: `[GLOBAL] Formulario B2B`, `[GLOBAL] Social Proof`, etc.
4. Insertar en otras páginas desde la biblioteca de widgets globales

---

## 8. Páginas — Estructura Elementor por página

### 8.1 Home (`/`) — Secciones

| # | Sección | Template Elementor | Fondo | Notas |
|---|---------|-------------------|-------|-------|
| 1 | Header | Theme Builder global | Negro | Sticky |
| 2 | Hero | Contenedor Flex 2-col | Negro | Imagen H350 der · Copy + CTAs izq |
| 3 | Trust Bar | `[GLOBAL] Trust Bar` | Amarillo | 5 columnas → scroll horiz. en mobile |
| 4 | Servicios | Grid 5 tarjetas | Blanco | Primera tarjeta con borde amarillo |
| 5 | Diferenciadores | Grid 3x2 | #F5F5F5 | 6 bloques ícono+texto |
| 6 | Social Proof | `[GLOBAL] Social Proof` | Negro | Logos grises o fallback texto |
| 7 | Formulario B2B | `[GLOBAL] Formulario B2B` | Blanco | Max-width 800px centrado |
| 8 | Flota | 2 columnas | #F5F5F5 | Foto H350 izq · Specs der |
| 9 | Cobertura Teaser | `[GLOBAL] Cobertura Teaser` | Amarillo | 4 zonas + CTA |
| 10 | CTA B2C | Centrado | Blanco | Headline H3 + botón WhatsApp |
| 11 | Footer | Theme Builder global | Negro | 4 columnas |

### 8.2 Transporte de Personal (`/servicios/transporte-de-personal/`) — Secciones

| # | Sección | Notas |
|---|---------|-------|
| 1 | Breadcrumb | Rank Math shortcode |
| 2 | Hero negro 60vh | H1: "Transporte de personal para empresas en Lima, Ica, Pisco y Huacho" |
| 3 | Propuesta de valor 3-col | Sin ausentismo / Control GPS / Sin permanencia |
| 4 | GPS destacado | 2 col · fondo negro · imagen/mockup GPS · specs a la derecha |
| 5 | Cobertura 2 col | Texto zonas + Google Maps embed iframe |
| 6 | Social proof | `[GLOBAL] Social Proof` — fondo amarillo en esta página |
| 7 | Cómo funciona | 3 pasos numerados · fondo #F5F5F5 |
| 8 | Formulario B2B | `[GLOBAL] Formulario B2B` |
| 9 | FAQ Accordion | 4 preguntas B2B + CTA a /preguntas-frecuentes/ |

### 8.3 Cobertura (`/cobertura/`) — Secciones

| # | Sección | Notas |
|---|---------|-------|
| 1 | Breadcrumb | — |
| 2 | Hero negro | H1: "Cubrimos toda Lima y llegamos hasta donde tu empresa opera" |
| 3 | Lima Metropolitana | Lista distritos con contexto industrial |
| 4 | Cobertura Regional | Ica (agroindustria) · Pisco (pesca) · Huacho (industria) |
| 5 | Google Maps | iFrame embed mostrando Lima + regiones |
| 6 | "¿Tu zona no aparece?" | CTA a WhatsApp o formulario |
| 7 | `[GLOBAL] CTA Banner` | Formulario cotización |

### 8.4 Contacto (`/contacto/`) — Secciones

| # | Sección | Notas |
|---|---------|-------|
| 1 | Hero negro 40vh | H1 + subtítulo |
| 2 | 2 columnas 60/40 | Col izq: `[GLOBAL] Formulario B2B` / Col der: WhatsApp + datos contacto |
| 3 | Cobertura Reminder | Fondo amarillo · texto zona cobertura · CTA a /cobertura/ |
| 4 | Google Maps | Solo si se confirma dirección física |

**Nota mobile — Contacto:** En mobile, invertir el orden: WhatsApp primero, formulario B2B segundo. Usar condición Elementor o CSS order para invertir columnas en mobile.

---

# PARTE V — CPTs Y TAXONOMÍAS

## 9. Custom Post Types

**Decisión: No se crean CPTs en Fase 1.**

| Motivo | Detalle |
|--------|---------|
| 1 solo vehículo | No tiene sentido un CPT "Flota" con un solo item |
| Testimonios no activos | No hay testimonios reales en Fase 1 |
| Servicios son páginas | 5 servicios = 5 páginas WordPress. No requieren CPT |
| Complejidad innecesaria | Blueprint Web Corporativa → Pages + ACF es suficiente |

### CPTs previstos para Fase 2 (documentar, no crear)

| CPT futuro | Slug | Cuándo activar |
|-----------|------|----------------|
| Vehículos de flota | `flota` | Si la empresa amplía su flota (3+ vehículos) |
| Testimonios | `testimonios` | Cuando se recolecten testimonios reales verificados |
| Entradas de blog | (nativo de WP) | Cuando se inicie blog SEO Fase 2 |
| Landing pages de Ads | `landing` | Fase 2 con Google Ads |

## 10. Taxonomías

**No se crean taxonomías en Fase 1.** Las páginas de servicios no necesitan categorización adicional.

---

# PARTE VI — CAMPOS PERSONALIZADOS (ACF)

## 11. Grupos de campos ACF

### 11.1 Grupo: "Flota — Hyundai H350"

**Asignado a:** Páginas con plantilla "Página de Nosotros" o manualmente asignado a la página "Nosotros"

| Campo | Nombre técnico | Tipo | Descripción |
|-------|---------------|------|-------------|
| Nombre del vehículo | `flota_nombre` | Texto | "Hyundai H350" |
| Capacidad (pasajeros) | `flota_capacidad` | Número | 17 |
| Año del vehículo | `flota_anio` | Número | — |
| Galería de fotos | `flota_galeria` | Galería | Exterior + interior + GPS dashboard |
| Especificaciones | `flota_specs` | Repeater | Lista de: ✓ GPS · ✓ A/C · ✓ WiFi · ✓ Maletero amplio · etc. |

**Uso en Elementor:**
- `flota_galeria` → Elementor Image Gallery dinámico (requiere Elementor Pro)
- `flota_specs` → Loop Elementor (si se activa JetEngine en Fase 2) o lista HTML por ahora

**Nota Fase 1:** Para la galería, usar Elementor Image Gallery widget con fotos subidas directamente, sin necesidad de ACF dinámico. ACF sirve para que el cliente actualice fotos desde el backend en Fase 2.

### 11.2 Grupo: "Configuración de Página de Servicio"

**Asignado a:** Páginas hijas de "Servicios"

| Campo | Nombre técnico | Tipo | Opciones |
|-------|---------------|------|---------|
| Audiencia primaria | `servicio_audiencia` | Select | B2B · B2C |
| Tipo de CTA primario | `servicio_cta_tipo` | Select | Formulario · WhatsApp · Mixto |
| Mensaje WhatsApp personalizado | `servicio_whatsapp_msg` | Textarea | Mensaje preconfigurado para este servicio |
| Icono del servicio | `servicio_icono` | Imagen | SVG o PNG del ícono de la tarjeta |

**Uso:** En Fase 1, estos campos se usan como referencia para el desarrollador al configurar cada página en Elementor. El cambio de CTA se hace manualmente en Elementor, no dinámicamente.

**En Fase 2 con JetEngine:** Los campos `servicio_cta_tipo` pueden usarse en condiciones dinámicas de Elementor para mostrar/ocultar CTAs automáticamente.

---

# PARTE VII — FORMULARIOS (FLUENT FORMS)

## 12. Formulario de Cotización B2B

### 12.1 Configuración del formulario

**Nombre del formulario:** `Cotización Empresarial — Mayhil Express`
**ID del formulario:** `1` (o el que asigne el plugin)
**Formulario embed ID para GTM:** `cotizacion_b2b`

### 12.2 Campos del formulario

| # | Campo | Nombre técnico | Tipo | Requerido | Opciones / Validación |
|---|-------|---------------|------|:---------:|----------------------|
| 1 | Nombre de empresa | `empresa` | Texto | ✓ | — |
| 2 | Nombre del responsable | `responsable` | Texto | ✓ | — |
| 3 | Cargo | `cargo` | Texto | — | — |
| 4 | Email corporativo | `email` | Email | ✓ | Validación formato + dominio no @gmail/@hotmail |
| 5 | Teléfono | `telefono` | Teléfono | ✓ | Formato Perú: +51 9XX XXX XXX |
| 6 | Cantidad de personas | `personas` | Select | ✓ | 1–10 / 11–17 / Más de 17 / Por definir |
| 7 | Frecuencia del servicio | `frecuencia` | Select | — | Diario / Semanal / Puntual / Por definir |
| 8 | Zona de recojo | `zona_recojo` | Texto | — | — |
| 9 | Zona de destino | `zona_destino` | Texto | — | — |
| 10 | Horario aproximado | `horario` | Texto | — | Ej: 7:00am · Turno noche · Variable |
| 11 | Mensaje adicional | `mensaje` | Textarea | — | Max 500 caracteres |
| — | Honeypot anti-spam | `_ffc_hp` | Hidden | — | Activar en Fluent Forms ajustes |
| — | GDPR / Privacidad | `privacidad` | Checkbox | — | "Acepto que mis datos se usen para contactarme" |

### 12.3 Configuración de notificaciones

**Notificación 1 — Al equipo Mayhil:**

```
Para:    servicio@mayhilexpress.com
Asunto:  [COTIZACIÓN B2B] Nueva solicitud — {empresa}
Cuerpo:
  Nueva solicitud de cotización empresarial recibida.
  
  Empresa: {empresa}
  Responsable: {responsable}
  Cargo: {cargo}
  Email: {email}
  Teléfono: {telefono}
  Personas: {personas}
  Frecuencia: {frecuencia}
  Zona recojo: {zona_recojo}
  Zona destino: {zona_destino}
  Horario: {horario}
  Mensaje: {mensaje}
  
  Fecha: {date}
  Página origen: {page_url}
  
  Responder en menos de 24 horas.
```

**Notificación 2 — Confirmación automática al lead:**

```
Para:    {email}
De:      Mayhil Express <servicio@mayhilexpress.com>
Asunto:  Hemos recibido tu solicitud — Mayhil Express
Cuerpo:
  Hola {responsable},

  Gracias por contactarnos. Hemos recibido tu solicitud de cotización 
  para {empresa} y te responderemos en menos de 24 horas hábiles.

  Si necesitas atención inmediata, puedes escribirnos por WhatsApp:
  https://wa.me/51941747096

  El equipo de Mayhil Express
  servicio@mayhilexpress.com
  +51 941 747 096
```

### 12.4 Configuración post-envío

| Acción | Configuración |
|--------|--------------|
| Mensaje de éxito | "✓ Tu solicitud fue enviada. Te contactaremos en menos de 24 horas." (en la misma página, sin redirección) |
| Redirección | No redirigir (mantiene al usuario en la misma página) |
| Desactivar el formulario tras envío | No — permitir múltiples envíos |
| Anti-spam | Activar Honeypot. No usar reCAPTCHA (friction) en Fase 1 |

### 12.5 Integración GTM — Evento de formulario

Fluent Forms no empuja a `dataLayer` nativo. Se requiere código JavaScript:

```javascript
// Agregar en GTM → Tag HTML personalizado → disparar en "Form Submit" de Fluent Forms
// O via hook de WordPress en función personalizada

// Evento que debe quedar configurado en GTM:
// Trigger: "Fluent Form Submit" - basado en el evento del DOM del plugin
// Variable: formulario ID = 1

// DataLayer push esperado:
{
  'event': 'form_submit',
  'form_name': 'cotizacion_b2b',
  'form_empresa': '[valor del campo empresa]',
  'form_personas': '[valor del campo personas]'
}
```

*Ver sección "Código Requerido" para el hook PHP de implementación.*

### 12.6 Embed del formulario

El formulario se embebe en tres páginas con el shortcode de Fluent Forms:

```
[fluentform id="1"]
```

O vía Widget de Elementor → Fluent Forms (compatible nativo).

---

# PARTE VIII — MULTIIDIOMA (WPML)

## 13. Configuración WPML

### 13.1 Setup inicial

| Parámetro | Valor |
|-----------|-------|
| Idioma predeterminado | Español (es) |
| Idioma secundario | Inglés — English (en) |
| URL del idioma EN | Prefijo: `/en/` |
| URL del idioma ES | Sin prefijo (raíz) |
| Selector de idioma | En el header — integrar en menú o header de Elementor |

### 13.2 Componentes WPML requeridos

| Componente | Rol |
|-----------|-----|
| WPML Multilingual CMS | Traducción de páginas |
| WPML String Translation | Traduce strings de plugins (Fluent Forms labels, etc.) |
| WPML Media Translation | Permite asignar imágenes diferentes por idioma si es necesario |

### 13.3 Mapa de páginas ES → EN

| Página ES | Página EN | URL ES | URL EN |
|-----------|-----------|--------|--------|
| Inicio | Home | `/` | `/en/` |
| Nosotros | About Us | `/nosotros/` | `/en/about/` |
| Servicios [padre] | Services [padre] | `/servicios/` | `/en/services/` |
| Transporte de Personal | Staff Transport | `/servicios/transporte-de-personal/` | `/en/services/staff-transport/` |
| Transporte Corporativo | *incluido en Staff Transport EN* | `/servicios/transporte-corporativo/` | *no tiene equivalente independiente* |
| Traslado Aeropuerto | Airport Transfer | `/servicios/traslado-aeropuerto/` | `/en/services/airport-transfer/` |
| Transporte Turístico | Tour Transport | `/servicios/transporte-turistico/` | `/en/services/tour-transport/` |
| Transporte Grupos | *incluido en Staff Transport EN* | `/servicios/transporte-grupos/` | *no tiene equivalente independiente* |
| Cobertura | Coverage | `/cobertura/` | `/en/coverage/` |
| Preguntas Frecuentes | FAQ | `/preguntas-frecuentes/` | `/en/faq/` |
| Contacto | Contact | `/contacto/` | `/en/contact/` |

**Nota:** Transporte Corporativo y Grupos en español no tienen página equivalente en inglés — su contenido está fusionado en `/en/services/staff-transport/`. WPML puede configurarse para que estas 2 páginas ES apunten como hreflang alternativo a la página EN fusionada.

### 13.4 hreflang — Configuración

WPML genera hreflang automáticamente en el `<head>` cuando las páginas están vinculadas. Verificar post-lanzamiento en Search Console → Cobertura → hreflang.

Formato esperado en el `<head>`:

```html
<link rel="alternate" hreflang="es" href="https://mayhilexpress.com/servicios/transporte-de-personal/" />
<link rel="alternate" hreflang="en" href="https://mayhilexpress.com/en/services/staff-transport/" />
<link rel="alternate" hreflang="x-default" href="https://mayhilexpress.com/servicios/transporte-de-personal/" />
```

### 13.5 Formulario B2B en versión EN

Crear un segundo formulario en Fluent Forms con labels en inglés:

**Nombre:** `Quote Request — Mayhil Express (EN)`

Labels en inglés: Company name / Contact person / Position / Corporate email / Phone / Number of passengers / Service frequency / Pickup area / Destination / Estimated schedule / Additional notes.

---

# PARTE IX — WHATSAPP (WP SOCIAL CHAT)

## 14. Configuración del Widget WhatsApp

### 14.1 Ajustes generales

| Parámetro | Valor |
|-----------|-------|
| Número WhatsApp | +51 941 747 096 |
| Nombre mostrado | Mayhil Express |
| Horario de atención | 24/7 (sin limitación de horario en el widget) |
| Posición del widget | Inferior derecha |
| Color del botón | `#25D366` verde WhatsApp |
| Tamaño del ícono | 56px |
| Z-index | 9998 (debajo del header en 9999) |

### 14.2 Mensajes diferenciados por página

El plugin WP Social Chat permite configurar mensajes distintos por URL. Configurar:

| Página | Mensaje preconfigurado |
|--------|----------------------|
| **Todas las páginas (default)** | `Hola Mayhil Express, me interesa su servicio. ¿Pueden brindarme más información?` |
| **/servicios/traslado-aeropuerto/** | `Hola, necesito un traslado al Aeropuerto Jorge Chávez. ¿Tienen disponibilidad? Somos [N] personas.` |
| **/servicios/transporte-turistico/** | `Hola, me interesa un tour privado. Somos [N] personas. ¿Cuáles son los destinos y precios?` |
| **/servicios/transporte-grupos/** | `Hola, necesito transporte para un grupo de [N] personas. ¿Pueden cotizarme?` |
| **/en/** y páginas EN | `Hello! I'm interested in your transportation services. Could you provide more information?` |
| **/en/services/airport-transfer/** | `Hello, I need an airport transfer to/from Jorge Chávez Airport. We are [N] people. Is there availability?` |

**Nota técnica:** WP Social Chat → configurar "Custom Message" por URL en cada entrada de configuración del plugin.

### 14.3 Tracking del clic en WhatsApp — GTM

El clic en el widget de WhatsApp debe disparar un evento en GTM:

```
Trigger GTM: Clic en elemento con URL que contenga "wa.me" o "api.whatsapp.com"
Evento: 'whatsapp_click'
Variables adicionales: página origen ({Page URL}), dispositivo ({Device Category})
```

*Ver sección "Código Requerido" para la implementación exacta.*

---

# PARTE X — SEO TÉCNICO (RANK MATH)

## 15. Configuración Rank Math Pro

### 15.1 Asistente de configuración

| Opción | Valor |
|--------|-------|
| Tipo de sitio | Negocio Local |
| Categoría | Transportation Service |
| Nombre | Mayhil Express |
| Logo | Logo PNG/SVG alta resolución |
| Imagen social | Foto H350 exterior (1200×630px JPG) |
| Separador de título | ` | ` (pipe con espacios) |

### 15.2 Ajustes generales SEO

| Parámetro | Configuración |
|-----------|--------------|
| Indexar páginas | SÍ — todas las páginas de contenido |
| No indexar | `/wp-admin/`, páginas de sistema, política de privacidad (opcional) |
| Nofollow links externos | No (no aplicar globalmente) |
| URL canónica | Automática — verificar que no haya conflictos con WPML |
| Breadcrumbs | Activar — separador: `>` |
| Schema global | Organization + LocalBusiness |

### 15.3 Meta Titles y Descriptions por página

*(Extraídos del SEO Plan v1.0 — copiar exactamente)*

| Página | Meta Title | Meta Description |
|--------|-----------|-----------------|
| Home ES | Transporte de Personal y Movilidad Corporativa en Lima \| Mayhil Express | Empresa de transporte de personal para empresas en Lima con GPS en tiempo real. 24/7 · 17 pasajeros · Lima, Ica, Pisco y Huacho. Solicita cotización hoy. |
| Transporte Personal | Transporte de Personal Lima para Empresas \| GPS · 24/7 \| Mayhil Express | Servicio de transporte de personal para empresas en Lima con monitoreo GPS. Cobertura en todos los distritos y regiones: Ica, Pisco, Huacho. Sin permanencia mínima. |
| Transporte Corporativo | Transporte Corporativo Lima \| Ejecutivos y Eventos Empresariales \| Mayhil Express | Movilidad corporativa para ejecutivos, reuniones y eventos empresariales en Lima. Vehículo privado, conductor profesional, disponibilidad 24/7. Solicita propuesta. |
| Traslado Aeropuerto | Traslado Aeropuerto Lima Jorge Chávez \| Van Privada 24/7 \| Mayhil Express | Traslados al y desde el Aeropuerto Jorge Chávez en van privada para hasta 17 personas. Reserva por WhatsApp. Atención las 24 horas, todos los días del año. |
| Transporte Turístico | Transporte Turístico Lima, Paracas y Huacachina \| Van Privada \| Mayhil Express | Tour y transporte turístico privado en Lima, Paracas, Huacachina e Ica. Hasta 17 pasajeros, A/C, WiFi. Reserva por WhatsApp fácil y rápido. |
| Transporte Grupos | Transporte Privado para Grupos Lima \| Hasta 17 Pasajeros \| Mayhil Express | Van privada para grupos de hasta 17 personas en Lima. Ideal para eventos, excursiones, traslados corporativos. Precio único. Cotiza ahora. |
| Cobertura | Cobertura en Lima, Ica, Pisco y Huacho \| Transporte de Personal \| Mayhil Express | Cubrimos todos los distritos de Lima Metropolitana y regiones: Ica, Pisco y Huacho. Transporte de personal e interprovincial para empresas. Consulta tu zona. |
| Nosotros | Nosotros \| 5 Años en Transporte Privado Lima \| Mayhil Express | Conoce Mayhil Express: 5 años transportando personal, ejecutivos y turistas en Lima. Flota Hyundai H350 con GPS. Movilidad corporativa confiable y puntual. |
| FAQ | Preguntas Frecuentes \| Transporte Personal y Aeropuerto Lima \| Mayhil Express | Respuestas a las preguntas más frecuentes sobre transporte de personal, traslados al aeropuerto y turismo privado en Lima con Mayhil Express. |
| Contacto | Solicitar Cotización Transporte de Personal Lima \| Mayhil Express | Solicita tu cotización de transporte de personal o traslado en Lima. Formulario empresarial. Respuesta en menos de 24 horas. |
| Home EN | Corporate Staff Transport in Lima, Peru \| GPS · 24/7 \| Mayhil Express | Private transportation for corporate staff in Lima with real-time GPS monitoring. Available 24/7. Coverage: Lima, Ica, Pisco and Huacho. Request a quote today. |
| Staff Transport EN | Staff Transport Lima Peru \| Corporate Mobility with GPS Tracking \| Mayhil Express | Corporate staff transportation in Lima with real-time GPS. Up to 17 passengers, 24/7 service, coverage across Lima and regions. No minimum commitment required. |
| Airport Transfer EN | Airport Transfer Lima Jorge Chávez \| Private Van 24/7 \| Mayhil Express | Private airport transfers to/from Lima Jorge Chávez International Airport. Up to 17 passengers. Book via WhatsApp. Available 24 hours a day. |

### 15.4 Schema markup — Configuración por página

| Página | Schema Rank Math | Campos a completar |
|--------|-----------------|-------------------|
| Home | `Organization` + `LocalBusiness` | name, telephone, email, url, openingHours, areaServed, logo, image |
| Páginas de servicio | `Service` | name, description, provider (→ Organization), areaServed |
| FAQ | `FAQPage` | Pares question/answer por cada FAQ del accordion |
| Cobertura | `LocalBusiness` + `areaServed` | PostalAddress con Lima, Ica, Pisco, Huacho |
| Nosotros | `Organization` | foundingDate: 2021, description |
| Todas las subpáginas | `BreadcrumbList` | Automático via Rank Math breadcrumbs |

**JSON-LD del Home — LocalBusiness (completar cuando se tenga dirección):**

```json
{
  "@type": "TransportService",
  "name": "Mayhil Express",
  "telephone": "+51941747096",
  "email": "servicio@mayhilexpress.com",
  "url": "https://mayhilexpress.com",
  "openingHours": "Mo-Su 00:00-23:59",
  "areaServed": [
    {"@type": "City", "name": "Lima"},
    {"@type": "City", "name": "Ica"},
    {"@type": "City", "name": "Pisco"},
    {"@type": "City", "name": "Huacho"}
  ],
  "priceRange": "$$",
  "image": "https://mayhilexpress.com/wp-content/uploads/h350-exterior.jpg",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Lima",
    "addressCountry": "PE"
  }
}
```

*Completar `streetAddress` y `postalCode` cuando el cliente confirme la dirección.*

### 15.5 Sitemap XML

| Configuración | Valor |
|--------------|-------|
| Generar sitemap | Activado |
| URL del sitemap | `https://mayhilexpress.com/sitemap_index.xml` |
| Incluir | Páginas + hreflang |
| Excluir | Páginas de sistema · admin · login |
| Enviar a GSC | Inmediato post-lanzamiento |
| Frecuencia de actualización | Al publicar/actualizar contenido |

### 15.6 robots.txt

```
User-agent: *
Allow: /

Disallow: /wp-admin/
Disallow: /wp-includes/
Disallow: /wp-json/
Disallow: /wp-login.php
Disallow: /?s=
Disallow: /feed/

Sitemap: https://mayhilexpress.com/sitemap_index.xml
```

### 15.7 Open Graph y redes sociales

| Parámetro | Valor |
|-----------|-------|
| OG Default Image | Foto H350 exterior · 1200×630px · formato JPG |
| OG Title | Igual al meta title de cada página |
| OG Description | Igual al meta description de cada página |
| Twitter Card | `summary_large_image` |
| Facebook App ID | PENDIENTE DE VALIDACIÓN |

---

# PARTE XI — ANALÍTICA (GTM + GA4)

## 16. Google Tag Manager

### 16.1 Configuración del contenedor

| Parámetro | Valor |
|-----------|-------|
| Nombre del contenedor | Mayhil Express |
| Plataforma objetivo | Web |
| ID del contenedor | GTM-XXXXXXX (asignar al crear) |

### 16.2 Instalar GTM en WordPress

**Opción A (recomendada):** Plugin "GTM4WP" → insertar el ID del contenedor.

**Opción B:** Agregar manualmente el snippet en el `<head>` y `<body>` vía hook de WordPress.

### 16.3 Tags necesarios

| Tag | Tipo | Trigger |
|-----|------|---------|
| GA4 — Configuración | GA4 Configuration | All Pages |
| GA4 — Form Submit B2B | GA4 Event: `form_submit` | Trigger: Fluent Form Submit |
| GA4 — WhatsApp Click | GA4 Event: `whatsapp_click` | Trigger: clic en wa.me |
| GA4 — Pageview | (incluido en GA4 Configuración) | All Pages |

### 16.4 Triggers necesarios

| Trigger | Tipo | Condición |
|---------|------|-----------|
| All Pages | Pageview | — |
| Fluent Form Submit | Elemento del DOM | Class: `.ff-btn-submit` o por custom event |
| WhatsApp Click | Clic en enlace | URL contiene `wa.me` o `api.whatsapp.com` |

### 16.5 Variables necesarias

| Variable | Tipo | Valor |
|----------|------|-------|
| GA4 Measurement ID | Constante | G-XXXXXXXXXX (ID de GA4 del cliente) |
| Page URL | URL automática de GTM | — |
| Click URL | Clic automático de GTM | — |
| Device Category | User Agent parser | mobile / desktop / tablet |

### 16.6 Eventos GA4 configurados

| Evento GA4 | Cuándo se dispara | Parámetros |
|-----------|------------------|-----------|
| `form_submit` | Al enviar formulario B2B | `form_name: 'cotizacion_b2b'`, `form_empresa: [valor]` |
| `whatsapp_click` | Al clic en widget/botón WhatsApp | `page_location: [URL]`, `device_category: [mobile/desktop]` |
| `page_view` | En cada cambio de página | Automático vía GA4 |

### 16.7 Conversiones en GA4

Marcar como conversiones en GA4 → Configuración → Eventos:

| Conversión | Evento de origen |
|-----------|-----------------|
| Cotización B2B enviada | `form_submit` |
| Clic WhatsApp | `whatsapp_click` |

### 16.8 Vincular GA4 con Google Search Console

En GA4 → Administración → Vinculaciones de Search Console. Requiere que Search Console esté verificado previamente.

---

# PARTE XII — CLOUDFLARE

## 17. Configuración Cloudflare

### 17.1 Setup DNS

| Acción | Detalle |
|--------|---------|
| Añadir sitio | mayhilexpress.com |
| Plan | Free (suficiente para este proyecto) |
| Modo proxy | Activar proxy naranja (🟠) en registros A y CNAME del dominio |
| DNS Records | Configurar A record → IP del hosting / CNAME si es necesario |

### 17.2 SSL/TLS

| Parámetro | Valor |
|-----------|-------|
| Modo SSL | Full (Strict) — requiere certificado SSL en el hosting |
| HTTPS Siempre | Activar → redirige todo HTTP → HTTPS |
| HSTS | Activar con max-age=31536000 |
| Versión TLS mínima | TLS 1.2 |
| TLS 1.3 | Activar |

### 17.3 Performance

| Optimización | Estado |
|-------------|--------|
| Auto Minify (HTML, CSS, JS) | Activar todos |
| Brotli Compression | Activar |
| HTTP/2 | Activar (automático con Cloudflare) |
| HTTP/3 (QUIC) | Activar |
| Rocket Loader | **DESACTIVAR** — interfiere con Elementor y Fluent Forms |
| Mirage (lazy images) | Activar |
| Polish (optimización imágenes) | Activar → Lossless (las imágenes ya se optimizan con Imagify) |

### 17.4 Caché Cloudflare

| Parámetro | Valor |
|-----------|-------|
| Nivel de caché | Standard |
| TTL de borde | 4 horas |
| Cache-Control | Respetar los headers del servidor |
| Purge cache | Hacer purge completo post-lanzamiento y tras actualizaciones |

### 17.5 Page Rules (Reglas de página)

| URL Pattern | Acción |
|------------|--------|
| `mayhilexpress.com/wp-admin/*` | Cache Level: Bypass |
| `mayhilexpress.com/wp-login.php` | Security Level: High + Cache Bypass |
| `mayhilexpress.com/?s=*` | Cache Level: Bypass (búsqueda interna — no hay, pero por si acaso) |

### 17.6 Seguridad Cloudflare

| Parámetro | Valor |
|-----------|-------|
| Bot Fight Mode | Activar |
| Browser Integrity Check | Activar |
| Security Level | Medium |
| Challenge Passage | 30 minutos |
| Hotlink Protection | Activar (protege imágenes del sitio) |
| Email Address Obfuscation | Activar |

---

# PARTE XIII — RENDIMIENTO Y CORE WEB VITALS

## 18. Objetivos Core Web Vitals

| Métrica | Objetivo | Herramienta de verificación |
|---------|----------|----------------------------|
| LCP (Largest Contentful Paint) | < 2.5s | PageSpeed Insights + Search Console |
| INP (Interaction to Next Paint) | < 200ms | PageSpeed Insights |
| CLS (Cumulative Layout Shift) | < 0.1 | PageSpeed Insights |
| TTFB (Time to First Byte) | < 600ms | PageSpeed Insights |
| Score móvil PageSpeed | ≥ 75 | PageSpeed Insights |
| Score desktop PageSpeed | ≥ 90 | PageSpeed Insights |

## 19. LiteSpeed Cache — Configuración

*Si el hosting usa Apache u Nginx, reemplazar con WP Rocket.*

### 19.1 Ajustes de caché

| Opción | Valor |
|--------|-------|
| Activar caché | Sí |
| Caché de páginas | Sí |
| Caché para usuarios logueados | No |
| Caché para móviles | Sí (separado) |
| TTL de caché | 604800 (1 semana) |
| Purgar al publicar | Sí |

### 19.2 Optimización CSS/JS

| Opción | Valor |
|--------|-------|
| Combinar CSS | No (Elementor ya lo maneja) |
| Minificar CSS | Sí |
| Minificar JS | Sí |
| Combinar JS | No (puede romper Elementor/Fluent Forms) |
| Diferir JS | Sí — exceptuar jQuery y scripts críticos |
| Eliminar CSS no usado | Con precaución — verificar que no rompa Elementor |
| Critical CSS | Activar — Elementor Pro puede generar el critical CSS |

### 19.3 Optimización de imágenes (LiteSpeed)

| Opción | Valor |
|--------|-------|
| Lazy Load imágenes | Sí |
| Lazy Load iframes (Google Maps) | Sí |
| Dimensiones de imágenes | Siempre definir `width` y `height` en HTML (evita CLS) |
| WebP reemplazar | Sí (si Imagify ya convirtió las imágenes) |

## 20. Imágenes — Protocolo WebP

**Regla:** Toda imagen que se suba al sitio debe estar en formato WebP antes de publicar.

| Paso | Acción |
|------|--------|
| 1 | Instalar Imagify y activar optimización automática |
| 2 | Al subir imágenes desde la biblioteca de medios, Imagify convierte automáticamente a WebP |
| 3 | Configurar: Modo de optimización → Aggressive (sin pérdida visual perceptible) |
| 4 | Formatos de salida: WebP Activado · AVIF: Desactivado (compatibilidad) |
| 5 | Bulk optimize: Después de subir el logo y fotos del H350, hacer optimización masiva |

### Especificaciones por tipo de imagen

| Imagen | Dimensiones | Formato | Max Peso |
|--------|-----------|---------|---------|
| Hero — H350 exterior | 1440×810px | WebP | 150 KB |
| Foto interior H350 | 800×600px | WebP | 80 KB |
| Foto GPS / dashboard | 800×600px | WebP | 60 KB |
| Logo Mayhil (en negro) | 280×80px | SVG o WebP | 20 KB |
| Logo Mayhil (en blanco) | 280×80px | SVG o WebP | 20 KB |
| OG Social image | 1200×630px | JPG | 100 KB |
| Logos SEDAPAL/CLARO/MOVISTAR | 160×48px | SVG preferido | 10 KB c/u |
| Íconos de servicios | 48×48px | SVG | < 5 KB |

---

# PARTE XIV — SEGURIDAD WORDPRESS

## 21. Hardening básico (sin plugin de seguridad)

### 21.1 Configuración WordPress

| Acción | Método |
|--------|--------|
| Cambiar usuario "admin" | Crear usuario con nombre no obvio, eliminar "admin" |
| Contraseña fuerte | Mínimo 16 caracteres alfanuméricos + especiales |
| Actualizar WordPress al instalar | Siempre instalar la versión estable más reciente |
| Actualizar todos los plugins | Antes del lanzamiento |
| Desactivar XML-RPC | Agregar en `.htaccess` o con snippet PHP |
| Proteger `wp-login.php` | Cloudflare Security Level: High en esa URL |
| Deshabilitar edición de archivos desde el panel | Agregar `define('DISALLOW_FILE_EDIT', true);` en `wp-config.php` |
| Prefijo de tablas DB | Cambiar de `wp_` a prefijo personalizado durante instalación |
| Ocultar versión de WordPress | Vía función PHP: `remove_action('wp_head', 'wp_generator')` |
| HTTPS forzado | Cloudflare Always Use HTTPS |

### 21.2 Permisos de archivos en hosting

| Recurso | Permiso |
|---------|---------|
| Carpetas de WordPress | 755 |
| Archivos de WordPress | 644 |
| `wp-config.php` | 600 |
| `.htaccess` | 644 |

---

# PARTE XV — FLUJO DE IMPLEMENTACIÓN

## 22. Orden de ejecución por fases

### FASE 1 — Setup (Día 1)

| Paso | Acción | Tiempo estimado |
|------|--------|----------------|
| 1.1 | Verificar hosting: PHP 8.1+, RAM ≥ 2GB, LiteSpeed/Apache | 30 min |
| 1.2 | Instalar WordPress · Idioma: Español (Perú) | 15 min |
| 1.3 | Configurar WordPress: permalinks, ajustes, hardening básico | 30 min |
| 1.4 | Instalar plugins base: Elementor Pro · Rank Math · ACF · Fluent Forms · WPML · WP Social Chat · LiteSpeed · Imagify | 45 min |
| 1.5 | Activar licencias de plugins premium | 15 min |
| 1.6 | Configurar Cloudflare: DNS · SSL · Page Rules · Performance | 30 min |
| 1.7 | Configurar Elementor: Global Colors · Global Fonts · Contenedores Flexbox · Breakpoints | 30 min |
| 1.8 | Configurar Rank Math: asistente inicial · tipo de negocio · schema global | 30 min |

---

### FASE 2 — Estructura base + Global Components (Día 1–2)

| Paso | Acción | Tiempo |
|------|--------|--------|
| 2.1 | Crear páginas WordPress (10 ES) con slugs correctos | 20 min |
| 2.2 | Crear página "Servicios" como padre + hijos | 10 min |
| 2.3 | Construir Header (Theme Builder) | 90 min |
| 2.4 | Construir Footer (Theme Builder) | 45 min |
| 2.5 | Crear formulario B2B en Fluent Forms (11 campos + notificaciones) | 60 min |
| 2.6 | Crear `[GLOBAL] Formulario B2B` en Elementor | 30 min |
| 2.7 | Crear `[GLOBAL] Social Proof` en Elementor (con logos + fallback) | 45 min |
| 2.8 | Crear `[GLOBAL] Trust Bar` en Elementor | 30 min |
| 2.9 | Crear `[GLOBAL] CTA Banner Final` en Elementor | 20 min |

---

### FASE 3 — Home (Día 2–3)

| Paso | Acción | Tiempo |
|------|--------|--------|
| 3.1 | Construir sección Hero con imagen H350 + copy + CTAs | 60 min |
| 3.2 | Insertar Trust Bar global | 10 min |
| 3.3 | Construir grid de 5 servicios | 60 min |
| 3.4 | Construir 6 diferenciadores 3x2 | 45 min |
| 3.5 | Insertar Social Proof global | 10 min |
| 3.6 | Insertar Formulario B2B global | 10 min |
| 3.7 | Construir sección Flota (foto + specs H350) | 45 min |
| 3.8 | Construir Cobertura Teaser amarilla | 30 min |
| 3.9 | Construir CTA final B2C (WhatsApp) | 20 min |
| 3.10 | Responsivo mobile completo de Home | 90 min |

---

### FASE 4 — Página Pilar: Transporte de Personal (Día 3–4)

| Paso | Acción | Tiempo |
|------|--------|--------|
| 4.1 | Hero negro + H1 SEO + CTA | 30 min |
| 4.2 | Propuesta de valor 3 bloques | 30 min |
| 4.3 | Sección GPS diferenciador (imagen + specs) | 60 min |
| 4.4 | Sección cobertura + Google Maps embed | 45 min |
| 4.5 | Social Proof global | 10 min |
| 4.6 | Sección Cómo funciona (3 pasos) | 30 min |
| 4.7 | Formulario B2B global embebido | 10 min |
| 4.8 | FAQ accordion 4 preguntas + CTA a /preguntas-frecuentes/ | 30 min |
| 4.9 | Breadcrumbs (Rank Math) | 10 min |
| 4.10 | Responsivo mobile | 60 min |

---

### FASE 5 — Páginas secundarias (Días 5–6)

| Página | Tiempo estimado |
|--------|----------------|
| Nosotros | 3 horas |
| Cobertura (con mapa) | 2.5 horas |
| Contacto (formulario + columna info) | 2 horas |
| FAQ (accordion 13 preguntas) | 2 horas |
| Transporte Corporativo | 1.5 horas (template base) |
| Traslado Aeropuerto | 1.5 horas |
| Transporte Turístico | 1.5 horas |
| Transporte Grupos | 1.5 horas |

---

### FASE 6 — Multiidioma EN (Días 7–8)

| Paso | Acción | Tiempo |
|------|--------|--------|
| 6.1 | Configurar WPML: idiomas · selector · prefijo `/en/` | 60 min |
| 6.2 | Traducir header y menú EN | 30 min |
| 6.3 | Crear y traducir Home EN | 3 horas |
| 6.4 | Crear y traducir Staff Transport EN | 2.5 horas |
| 6.5 | Crear Airport Transfer EN | 1.5 horas |
| 6.6 | Crear Tour Transport EN | 1.5 horas |
| 6.7 | Crear About Us, Coverage, FAQ, Contact EN | 3 horas |
| 6.8 | Vincular todas las páginas ES ↔ EN en WPML | 30 min |
| 6.9 | Verificar hreflang en código fuente | 20 min |

---

### FASE 7 — SEO On-Page (Día 9)

| Paso | Acción |
|------|--------|
| 7.1 | Completar meta titles y descriptions en las 19 páginas (copiar de SEO Plan) |
| 7.2 | Configurar schema por tipo de página en Rank Math |
| 7.3 | Rellenar datos de LocalBusiness schema en Home |
| 7.4 | Configurar FAQPage schema en /preguntas-frecuentes/ |
| 7.5 | Verificar breadcrumbs en todas las subpáginas |
| 7.6 | Configurar Open Graph images (1 por página) |
| 7.7 | Configurar sitemap XML + excluir páginas de sistema |
| 7.8 | Verificar robots.txt |
| 7.9 | Agregar alt text en todas las imágenes |
| 7.10 | Verificar H1 único por página |

---

### FASE 8 — Integraciones analítica (Día 10)

| Paso | Acción |
|------|--------|
| 8.1 | Crear contenedor GTM |
| 8.2 | Instalar GTM en WordPress (plugin GTM4WP) |
| 8.3 | Crear property GA4 + obtener Measurement ID |
| 8.4 | Configurar Tag GA4 en GTM |
| 8.5 | Configurar Trigger y Tag form_submit (formulario B2B) |
| 8.6 | Configurar Trigger y Tag whatsapp_click |
| 8.7 | Publicar contenedor GTM |
| 8.8 | Verificar en GTM Preview Mode: events se disparan correctamente |
| 8.9 | Verificar conversiones en GA4 Real Time |
| 8.10 | Verificar dominio en Google Search Console |
| 8.11 | Enviar sitemap XML a Search Console |
| 8.12 | Configurar WP Social Chat: número + mensajes por URL |

---

### FASE 9 — QA (Día 11)

*Transferir a 10_QA_MANTENIMIENTO — ver checklist de QA.*

---

### FASE 10 — Lanzamiento (Días 12–13)

*Transferir a 11_DEVOPS_DEPLOYMENT.*

---

# PARTE XVI — CÓDIGO REQUERIDO

## 23. Identificación de código necesario

### 23.1 GTM dataLayer — Form Submit (Fluent Forms)

**Qué hace:** Empuja un evento al dataLayer de GTM cuando el formulario B2B es enviado exitosamente.

**Dónde implementar:** Fluent Forms → Global Settings → Advanced → Custom JS (Post Submission), O en función PHP en plugin personalizado.

**Evento esperado:**
```javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  'event': 'form_submit',
  'form_name': 'cotizacion_b2b',
  'form_empresa': // valor del campo empresa
});
```

### 23.2 GTM dataLayer — WhatsApp Click

**Qué hace:** Empuja un evento al dataLayer cuando el usuario clica en el widget de WhatsApp.

**Dónde implementar:** GTM → Trigger de tipo "Clic en enlace" cuya URL contenga `wa.me`.

**Evento esperado:**
```javascript
dataLayer.push({
  'event': 'whatsapp_click',
  'page_location': window.location.href
});
```

### 23.3 WordPress wp-config.php — Hardening

**Constantes a agregar en `wp-config.php`:**
```php
define('DISALLOW_FILE_EDIT', true);
define('WP_DEBUG', false);
define('DISALLOW_UNFILTERED_HTML', true);
```

### 23.4 Redireccionamiento de página "Servicios" padre

La página `/servicios/` es solo un contenedor. Debe redirigir a `/servicios/transporte-de-personal/`.

**Método:** Rank Math → Redirections → Agregar regla 301: `/servicios/` → `/servicios/transporte-de-personal/`

*No requiere código PHP — se resuelve con Rank Math Redirections.*

### 23.5 Custom CSS — Variables globales y helpers

Agregar en Elementor → Custom CSS (Site Wide):

```css
/* Reset de márgenes en mobile para contenedores Elementor */
@media (max-width: 390px) {
  .e-con { padding-left: 24px !important; padding-right: 24px !important; }
}

/* Botones touch-friendly en mobile */
@media (max-width: 768px) {
  .elementor-button { min-height: 44px !important; }
}

/* Formulario Fluent Forms — label arriba · focus amarillo */
.ff-el-input:focus, .ff-el-textarea:focus {
  border-color: #F5C400 !important;
  outline: none !important;
}
```

### 23.6 Función para ocultar versión de WordPress

Agregar en el plugin personalizado o `functions.php` del child theme:

```php
remove_action('wp_head', 'wp_generator');
```

---

# PARTE XVII — RIESGOS TÉCNICOS

## 24. Riesgos identificados

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|:---:|:---:|------------|
| Hosting incompatible (no LiteSpeed, PHP < 8.1) | Media | Alto | Verificar ANTES de instalar WordPress. Si no es LiteSpeed, usar WP Rocket en lugar de LiteSpeed Cache |
| WPML conflicto con Elementor Theme Builder | Baja | Alto | WPML tiene compatibilidad oficial con Elementor Pro. Usar versiones actualizadas de ambos |
| Fluent Forms no dispara evento GTM correctamente | Media | Alto | Probar en GTM Preview Mode antes del lanzamiento. Tener fallback con GTM Form Submit trigger |
| ACF campos no se sincronizan en versión EN | Media | Medio | Configurar WPML + ACF Field Synchronization en ajustes de WPML |
| LiteSpeed Cache rompe Elementor o Fluent Forms | Media | Alto | Desactivar "Combinar JS". Agregar Fluent Forms JS a la lista de exclusiones de LiteSpeed |
| Cloudflare Rocket Loader interfiere con scripts | Alta | Medio | DESACTIVAR Rocket Loader desde el inicio |
| Imágenes sin dimensiones fijas → CLS alto | Media | Medio | Definir width y height en todos los elementos Elementor Image |
| Formulario B2B llega a spam del cliente | Media | Alto | Configurar SPF/DKIM del dominio de email. Usar servicio SMTP (Brevo free o similar) |
| SEDAPAL/CLARO/MOVISTAR logos sin autorización | Alta | Bajo | Implementar sección fallback con texto. Widget visible = logos. Widget oculto = texto genérico |
| Dirección física no confirmada → Maps embed vacío | Alta | Bajo | No insertar Maps iframe hasta tener dirección. Reemplazar con imagen de mapa estática de Lima |

---

# PARTE XVIII — RECOMENDACIONES TÉCNICAS

## 25. Recomendaciones adicionales

### SMTP para emails del formulario

Los emails de WordPress (`wp_mail()`) enviados desde el servidor de hosting frecuentemente terminan en spam. Instalar un plugin SMTP o usar el API de un servicio de email transaccional:

| Opción | Plan | Emails/mes | Recomendación |
|--------|------|-----------|---------------|
| Brevo (ex Sendinblue) | Free | 300/día | ✓ Recomendado — API simple, integración con Fluent Forms |
| Mailgun | Pay-as-you-go | Variable | Buena deliverability |
| Gmail SMTP | Free con límites | 500/día | Válido para volumen bajo |

Configurar en Fluent Forms → Global Settings → Email Settings → usar API key de Brevo.

### Child Theme

Crear un child theme de Hello Elementor (el tema base recomendado con Elementor) para:
1. Agregar funciones PHP personalizadas sin riesgo al actualizar temas
2. Guardar CSS custom
3. Mantener la lógica de tracking GTM separada

Nombre del child theme: `hello-elementor-mayhil`

### Hello Elementor como tema base

Hello Elementor es el tema oficial de Elementor. Es mínimo, sin JavaScript innecesario, optimizado para Elementor y Elementor Theme Builder.

| Opción | Veredicto |
|--------|-----------|
| Hello Elementor | ✅ Recomendado |
| Astra | Válido pero innecesario con Elementor Pro |
| GeneratePress | Válido pero innecesario con Elementor Pro |
| Divi, OceanWP, Enfold | ❌ No usar con Elementor Pro |

---

# PARTE XIX — PRÓXIMOS PASOS

## 26. Acciones inmediatas del desarrollador

| # | Acción | Bloqueante | Depende de |
|---|--------|:----------:|-----------|
| 1 | Confirmar hosting (PHP 8.1+, RAM 2GB, LiteSpeed) | SÍ | Cliente |
| 2 | Obtener acceso al dominio mayhilexpress.com | SÍ | Cliente |
| 3 | Obtener acceso cPanel / FTP / SSH hosting | SÍ | Cliente |
| 4 | Cliente crea cuenta GA4 y comparte Measurement ID | SÍ | Cliente |
| 5 | Cliente crea contenedor GTM y comparte ID | SÍ | Cliente |
| 6 | Cliente entrega logo SVG/PNG alta resolución | SÍ | Cliente |
| 7 | Cliente entrega fotos H350 exterior + interior (mínimo 3 fotos) | SÍ | Cliente |
| 8 | Confirmar email destino para notificaciones del formulario | SÍ | Cliente |
| 9 | Confirmar número WhatsApp activo (+51 941 747 096) | — | Cliente |
| 10 | Confirmar autorización SEDAPAL/CLARO/MOVISTAR | — | Cliente (pendiente) |

## 27. Acción post-lanzamiento inmediata

| # | Acción |
|---|--------|
| 1 | Crear/reclamar Google Business Profile |
| 2 | Enviar sitemap XML a Search Console |
| 3 | Verificar hreflang en Search Console → Cobertura |
| 4 | Verificar CWV con PageSpeed Insights en mobile |
| 5 | Test end-to-end: enviar formulario real y verificar llegada al email |
| 6 | Probar WhatsApp: clic desde desktop y mobile |
| 7 | Verificar GA4 Real Time: pageviews y eventos |
| 8 | Backup completo con UpdraftPlus |

---

## 28. Próximo agente

**10_QA_MANTENIMIENTO**

Inputs requeridos:
- `06_WORDPRESS_IMPLEMENTACION.md` (este documento)
- `02_PRD.md` — criterios de aceptación (Sección 22)
- `03_SEO_PLAN.md` — checklist SEO técnico (Sección 14)
- Acceso al sitio en staging antes del lanzamiento

---

*Documento producido por 08_WORDPRESS_DEVELOPER · IA-WEB-STUDIO-OS · Mayhil Express · 2026-06-17 · Versión 1.0*

*Principios aplicados: Configurar antes de programar · JetEngine antes de código · Código antes que plugin innecesario · Performance primero · Seguridad por defecto · Mobile First*

*Próximo agente: 10_QA_MANTENIMIENTO*
