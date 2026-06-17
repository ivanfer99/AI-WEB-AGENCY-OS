# Wireframes — Mayhil Express

**Agente responsable:** 04_UX_UI_DESIGNER
**Fecha:** 2026-06-17
**Versión:** 1.0
**Estado:** Listo para desarrollo Elementor
**Basado en:** Brief v3.1 + PRD v2 + SEO Plan v1.0
**Stack:** WordPress + Elementor Pro

---

## 1. Dirección Visual

**Estilo:** Corporativo B2B · Premium · Funcional

**Por qué:**
Mayhil Express vende confianza a Gerentes de RRHH y Logística que toman decisiones de contratación empresarial. El sitio debe transmitir solidez institucional, no estética creativa. El decisor B2B necesita sentir que está contratando con una empresa seria, no con un particular.

El amarillo energiza los CTAs y botones. El negro proyecta seriedad y premium. El blanco da respiro. No hay lugar para decoración que no cumpla función.

**Referencias de estilo:** Empresas de logística corporativa, flotas empresariales, proveedores de servicios B2B en Latinoamérica.

**Lo que NO debe parecer:** Un taxi, una agencia de tours, un negocio informal.

---

## 2. Estrategia CRO

### Principio rector

> Un Gerente de RRHH que llega al sitio ya tiene un problema. El sitio no debe convencerlo de que tiene un problema — debe convencerlo de que Mayhil Express es la solución correcta.

### Jerarquía de conversión

```
ACCIÓN PRIMARIA   →  Formulario de cotización B2B
ACCIÓN SECUNDARIA →  Clic en WhatsApp (B2C)
ACCIÓN TERCIARIA  →  Navegación a página de servicio específico
```

### Elementos de confianza — orden de impacto

| Elemento | Impacto | Posición en Home |
|----------|---------|-----------------|
| SEDAPAL · CLARO · MOVISTAR | Máximo | Encima del pliegue (fold) en la sección 5 |
| GPS en tiempo real | Alto | Trust bar + sección diferenciadores |
| 5 años de experiencia | Medio | Hero o trust bar |
| 24/7 · 365 días | Alto | Trust bar |
| 17 pasajeros en 1 vehículo | Alto | Trust bar |
| Cobertura Lima + regiones | Medio-alto | Diferenciadores + sección dedicada |

### Reglas CRO aplicadas

- El formulario de cotización B2B aparece **en el Home** (no solo en /contacto/) — el decisor no debe buscar dónde cotizar
- El CTA "Solicitar cotización" aparece en el **Hero**, en el **medio** de la página (formulario) y en el **footer**
- El WhatsApp flotante es **siempre visible** pero **no es el CTA principal** — está para B2C
- El mensaje del WhatsApp cambia según la página en la que esté el usuario
- Cada página de servicio termina con el formulario de cotización **embebido**, no con un enlace a /contacto/

---

## 3. Design System Inicial

### Paleta de colores

| Token | Color | Hex | Uso |
|-------|-------|-----|-----|
| `--color-primary` | Amarillo Mayhil | `#F5C400` | CTAs, botones primarios, acentos, íconos |
| `--color-dark` | Negro Mayhil | `#111111` | Navbar, hero fondo, fondos premium, texto títulos |
| `--color-white` | Blanco | `#FFFFFF` | Fondos de sección, texto sobre negro, tarjetas |
| `--color-gray-light` | Gris claro | `#F5F5F5` | Fondos alternos, secciones neutras |
| `--color-gray-text` | Gris texto | `#444444` | Párrafos, descripciones |
| `--color-gray-mid` | Gris medio | `#888888` | Etiquetas, metadata |
| `--color-success` | Verde | `#22C55E` | WhatsApp button, confirmaciones |
| `--color-border` | Borde | `#E5E5E5` | Separadores, bordes de tarjetas |

### Tipografía

| Rol | Fuente | Peso | Tamaño Desktop | Tamaño Mobile |
|-----|--------|------|---------------|---------------|
| H1 | Inter | 800 ExtraBold | 52–60px | 32–36px |
| H2 | Inter | 700 Bold | 36–42px | 26–30px |
| H3 | Inter | 600 SemiBold | 24–28px | 20–22px |
| Cuerpo | Inter | 400 Regular | 16–18px | 15–16px |
| Label / Badge | Inter | 600 SemiBold | 12–14px | 12px |
| CTA Button | Inter | 700 Bold | 16px | 15px |

*Inter es open source, disponible en Google Fonts, compatible con Elementor Pro.*

### Espaciado

| Token | Valor | Uso |
|-------|-------|-----|
| `--space-xs` | 8px | Gap entre elementos pequeños |
| `--space-sm` | 16px | Padding interno de componentes |
| `--space-md` | 24px | Gap entre componentes |
| `--space-lg` | 48px | Separación entre secciones en mobile |
| `--space-xl` | 80px | Separación entre secciones en desktop |
| `--space-2xl` | 120px | Secciones hero y principales |
| `--container` | 1200px max | Ancho máximo del contenedor |
| `--container-padding` | 24px / 80px | Padding lateral mobile / desktop |

### Componentes Base

#### Botón Primario
```
╔══════════════════════════════╗
║  [→] SOLICITAR COTIZACIÓN   ║  ← Amarillo (#F5C400) · texto negro · bold
╚══════════════════════════════╝
Hover: amarillo más oscuro (#D4A900) · sombra sutil
Tamaño: padding 14px 28px · border-radius 4px
```

#### Botón Secundario
```
╔══════════════════════════════╗
║  [💬] CONSULTAR POR WHATSAPP ║  ← Verde (#25D366) · texto blanco · bold
╚══════════════════════════════╝
Hover: verde más oscuro · sombra
```

#### Botón Terciario / Ghost
```
┌──────────────────────────────┐
│      VER MÁS SERVICIOS       │  ← Fondo transparente · borde amarillo · texto amarillo
└──────────────────────────────┘
Sobre fondo oscuro. Hover: rellena en amarillo.
```

#### Tarjeta de Servicio
```
┌─────────────────────────────┐
│  [ÍCONO 48px]               │
│  Título del Servicio        │  ← H3 Bold
│  Descripción corta 2 líneas │  ← Body regular
│                             │
│  [→ Ver servicio]           │  ← Link amarillo
└─────────────────────────────┘
Fondo: blanco · borde-radius: 8px · sombra: 0 2px 12px rgba(0,0,0,.08)
Hover: sombra más pronunciada · borde superior amarillo 3px
```

#### Bloque Diferenciador
```
┌─────────────────────────────┐
│  [ÍCONO 40px amarillo]      │
│  Título corto               │  ← H3 SemiBold
│  Descripción 1-2 líneas     │  ← Body regular gris
└─────────────────────────────┘
Fondo: #F5F5F5 · sin borde · border-radius: 8px
```

#### Badge / Etiqueta
```
 ┌──────────────────┐
 │  ★ 5 AÑOS        │  ← Fondo amarillo · texto negro · bold · font 12px
 └──────────────────┘
 border-radius: 100px (pill)
```

#### Logo Cliente (Social Proof)
```
┌──────────────────────────┐
│  [LOGO empresa grayscale]│  ← Escala de grises + amarillo hover
└──────────────────────────┘
Ancho: 120–160px · altura: 48px · object-fit: contain
```

#### Campo de Formulario
```
┌──────────────────────────────────────────┐
│ Nombre de empresa *               [____] │
└──────────────────────────────────────────┘
Label arriba · border: 1px solid #E5E5E5 · focus: border amarillo
border-radius: 4px · padding: 12px 16px
```

---

## 4. Componentes Reutilizables (Elementor)

| Componente | Template Elementor | Reutilizado en |
|------------|------------------|----------------|
| Header / Navbar | Theme Builder → Header | Todas las páginas |
| Footer | Theme Builder → Footer | Todas las páginas |
| WhatsApp widget flotante | Plugin widget global | Todas las páginas |
| Tarjeta de servicio | Widget Inner Section | Home, Servicios hub |
| Bloque diferenciador (ícono + título + texto) | Widget Icon Box | Home, Transporte Personal |
| Formulario B2B | Fluent Forms → Global Form | Home, Transporte Personal, Contacto |
| Sección "Empresas que confían" | Section global (Elementor) | Home, Transporte Personal |
| CTA Banner final (amarillo full-width) | Section global | Todas las páginas internas |
| Trust bar (íconos + etiquetas) | Section global | Home, Transporte Personal |
| FAQ Accordion | Widget Accordion | FAQ, Transporte Personal |

---

## 5. Wireframes — HOME (`/`)

### 5.1 Desktop (1200px)

```
╔══════════════════════════════════════════════════════════════════════════════╗
║  HEADER — posición fixed · fondo negro · z-index alto                       ║
║                                                                              ║
║  [LOGO amarillo] ←izq     [Servicios ▼] [Nosotros] [Cobertura] [FAQ] →der  ║
║                            [SOLICITAR COTIZACIÓN] ← botón amarillo          ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 1 — HERO                                                           ║
║  Fondo: negro (#111) · altura: 90vh · imagen H350 derecha con overlay       ║
║                                                                              ║
║   ┌─────────────────────────────────┐    ┌───────────────────────────────┐  ║
║   │                                 │    │                               │  ║
║   │ [Badge: ★ 5 AÑOS EN LIMA]       │    │                               │  ║
║   │                                 │    │   ////  FOTO H350  ////       │  ║
║   │ Movilidad corporativa           │    │   ////  (exterior) ////       │  ║
║   │ para empresas en Lima           │    │   ////             ////       │  ║
║   │ con monitoreo GPS               │    │                               │  ║
║   │ en tiempo real.                 │    │                               │  ║
║   │                    (H1 blanco)  │    └───────────────────────────────┘  ║
║   │                                 │                                        ║
║   │ Transportamos hasta 17          │                                        ║
║   │ colaboradores, cubrimos         │                                        ║
║   │ Lima, Ica, Pisco y Huacho.      │                                        ║
║   │ Disponibles 24/7, sin           │                                        ║
║   │ permanencia mínima.  (párrafo)  │                                        ║
║   │                                 │                                        ║
║   │ [→ SOLICITAR COTIZACIÓN]        │                                        ║
║   │ [💬 CONSULTAR POR WHATSAPP]     │                                        ║
║   └─────────────────────────────────┘                                        ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 2 — TRUST BAR                                                      ║
║  Fondo: amarillo (#F5C400) · texto negro · 1 fila 5 columnas                ║
║                                                                              ║
║  [📡 GPS]        [🕐 24/7]      [👥 17 Pax]    [📍 Lima+]    [5 Años]    ║
║  Monitoreo      Disponible     Un vehículo     Ica, Pisco     Empresa       ║
║  en tiempo real  365 días      hasta 17 pax    y Huacho       formal        ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 3 — SERVICIOS                                                      ║
║  Fondo: blanco · 5 tarjetas en fila                                         ║
║                                                                              ║
║  Título sección: "Nuestros servicios de transporte"  (H2 centrado negro)    ║
║  Subtítulo: "Movilidad corporativa y privada en Lima y regiones"            ║
║                                                                              ║
║  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐    ║
║  │[🏢 ícono]│  │[💼 ícono]│  │[✈ ícono] │  │[🌄 ícono]│  │[👥 ícono]│    ║
║  │Transporte│  │Transport │  │Traslado  │  │Transport │  │Transport │    ║
║  │Personal  │  │Corporat. │  │Aeropuerto│  │Turístico │  │Grupos    │    ║
║  │          │  │          │  │          │  │          │  │          │    ║
║  │70% ingr. │  │Ejecutivos│  │Jorge     │  │Lima,     │  │Hasta 17  │    ║
║  │B2B core  │  │Eventos   │  │Chávez    │  │Paracas,  │  │pasajeros │    ║
║  │          │  │          │  │24/7      │  │Ica       │  │un viaje  │    ║
║  │[→ Ver]   │  │[→ Ver]   │  │[→ Ver]   │  │[→ Ver]   │  │[→ Ver]   │    ║
║  └──────────┘  └──────────┘  └──────────┘  └──────────┘  └──────────┘    ║
║  [★ destacada con borde amarillo la primera tarjeta]                        ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 4 — DIFERENCIADORES                                                ║
║  Fondo: #F5F5F5 · grid 3x2                                                  ║
║                                                                              ║
║  Título: "¿Por qué Mayhil Express?"  (H2 centrado)                         ║
║                                                                              ║
║  ┌──────────────────────┐  ┌──────────────────────┐  ┌──────────────────┐  ║
║  │ [📡] GPS en tiempo   │  │ [👥] Hasta 17        │  │ [🕐] 24/7 · 365  │  ║
║  │ real — control       │  │ colaboradores en un  │  │ días — turnos    │  ║
║  │ total de rutas y     │  │ solo vehículo,       │  │ rotativos y      │  ║
║  │ puntualidad          │  │ sin dividir el equipo│  │ servicios nocturn│  ║
║  └──────────────────────┘  └──────────────────────┘  └──────────────────┘  ║
║                                                                              ║
║  ┌──────────────────────┐  ┌──────────────────────┐  ┌──────────────────┐  ║
║  │ [📍] Lima completa + │  │ [📋] Sin permanencia │  │ [🌐] Atención   │  ║
║  │ Ica, Pisco y Huacho  │  │ mínima — por viaje,  │  │ bilingüe ES/EN  │  ║
║  │ cobertura regional   │  │ sin compromisos      │  │ multinacionales  │  ║
║  └──────────────────────┘  └──────────────────────┘  └──────────────────┘  ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 5 — SOCIAL PROOF "EMPRESAS QUE CONFÍAN"                           ║
║  Fondo: negro (#111) · texto blanco · logos en escala de grises             ║
║  [CONDICIONAL — activar si se obtiene autorización]                         ║
║                                                                              ║
║  Título: "Empresas que confían en Mayhil Express"  (H2 blanco centrado)    ║
║  Subtítulo: "Del sector telecomunicaciones y servicios públicos en Perú"    ║
║                                                                              ║
║         ┌──────────┐      ┌──────────┐      ┌──────────┐                   ║
║         │[SEDAPAL  │      │[CLARO    │      │[MOVISTAR │                   ║
║         │ logo]    │      │ logo]    │      │ logo]    │                   ║
║         └──────────┘      └──────────┘      └──────────┘                   ║
║                                                                              ║
║  Fallback (sin autorización):                                               ║
║  "Empresas del sector telecomunicaciones y servicios públicos con           ║
║   operaciones en Lima han confiado en nosotros para el transporte           ║
║   de su personal."                                                          ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 6 — FORMULARIO DE COTIZACIÓN B2B                                  ║
║  Fondo: blanco · max-width 800px centrado                                   ║
║                                                                              ║
║  [Badge: 📋 COTIZACIÓN EMPRESARIAL]                                         ║
║  Título: "Solicita tu cotización en minutos"  (H2 centrado)                ║
║  Subtítulo: "Sin permanencia mínima · Respuesta en menos de 24 horas"      ║
║                                                                              ║
║  ┌────────────────────────────────────────────────────────────────────┐     ║
║  │                                                                    │     ║
║  │  Nombre de empresa *    [________________________]                 │     ║
║  │  Nombre del responsable [________________________]                 │     ║
║  │  Cargo                  [________________________]                 │     ║
║  │                                                                    │     ║
║  │  Email corporativo *    [________________________]                 │     ║
║  │  Teléfono *             [________________________]                 │     ║
║  │                                                                    │     ║
║  │  Cantidad de personas   [1-17 ▼]  Frecuencia [Diaria ▼]          │     ║
║  │                                                                    │     ║
║  │  Zona de recojo         [________________________]                 │     ║
║  │  Zona de destino        [________________________]                 │     ║
║  │  Horario aproximado     [________________________]                 │     ║
║  │                                                                    │     ║
║  │  Mensaje adicional      [                        ]                 │     ║
║  │                         [                        ]                 │     ║
║  │                                                                    │     ║
║  │         [→  ENVIAR SOLICITUD DE COTIZACIÓN  ]  ← botón amarillo  │     ║
║  │                                                                    │     ║
║  │  🔒 Tus datos están seguros. Solo los usamos para contactarte.    │     ║
║  └────────────────────────────────────────────────────────────────────┘     ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 7 — FLOTA                                                          ║
║  Fondo: #F5F5F5 · 2 columnas                                                ║
║                                                                              ║
║   ┌─────────────────────────────────┐   ┌────────────────────────────────┐ ║
║   │                                 │   │ Hyundai H350                   │ ║
║   │   ////  FOTO H350 INTERIOR //// │   │                                │ ║
║   │   ////  (pasajeros, GPS)   //// │   │ ✓ Hasta 17 pasajeros           │ ║
║   │   ////                     //// │   │ ✓ Monitoreo GPS en tiempo real │ ║
║   │                                 │   │ ✓ Aire acondicionado           │ ║
║   └─────────────────────────────────┘   │ ✓ WiFi a bordo                 │ ║
║                                         │ ✓ Maletero amplio              │ ║
║                                         │ ✓ Disponible 24 horas          │ ║
║                                         │                                │ ║
║                                         │ [→ SOLICITAR COTIZACIÓN]       │ ║
║                                         └────────────────────────────────┘ ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 8 — COBERTURA (TEASER)                                             ║
║  Fondo: amarillo (#F5C400) · texto negro                                    ║
║                                                                              ║
║  Título: "Cubrimos toda Lima y llegamos hasta donde tu empresa opera"       ║
║                                                                              ║
║  [📍 Lima Metropolitana]   [📍 Ica]   [📍 Pisco]   [📍 Huacho]             ║
║  Todos los distritos       y alrededor y alrededor  y alrededor              ║
║                                                                              ║
║                    [→ VER COBERTURA COMPLETA]                                ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN 9 — CTA FINAL B2C                                                  ║
║  Fondo: blanco · centrado · sección más pequeña                             ║
║                                                                              ║
║  Título: "¿Traslado al aeropuerto o tour privado?"  (H3)                   ║
║  Texto: "Para traslados individuales, cotiza rápido por WhatsApp"           ║
║                                                                              ║
║              [💬 CONSULTAR POR WHATSAPP]  ← botón verde                    ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  FOOTER                                                                     ║
║  Fondo: negro (#111) · texto gris claro                                     ║
║                                                                              ║
║  ┌────────────────┐  ┌────────────────┐  ┌────────────┐  ┌──────────────┐ ║
║  │ [LOGO blanco]  │  │ SERVICIOS      │  │ EMPRESA    │  │ CONTACTO     │ ║
║  │                │  │ · Personal     │  │ · Nosotros │  │ 941 747 096  │ ║
║  │ Movilidad      │  │ · Corporativo  │  │ · Cobertura│  │ servicio@... │ ║
║  │ corporativa    │  │ · Aeropuerto   │  │ · FAQ      │  │              │ ║
║  │ en Lima.       │  │ · Turístico    │  │ · Contacto │  │ [💬 WhatsApp]│ ║
║  │                │  │ · Grupos       │  │            │  │              │ ║
║  └────────────────┘  └────────────────┘  └────────────┘  └──────────────┘ ║
║                                                                              ║
║  ─────────────────────────────────────────────────────────────────────────  ║
║  © 2026 Mayhil Express · Lima, Perú · Política de Privacidad               ║
╚══════════════════════════════════════════════════════════════════════════════╝

[💬 WhatsApp flotante — esquina inferior derecha — siempre visible]
```

---

### 5.2 Mobile — HOME (390px)

```
╔════════════════════════════╗
║  HEADER MOBILE — sticky    ║
║  [LOGO]          [≡ menú] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  HERO MOBILE               ║
║  Fondo: negro              ║
║                            ║
║  [Badge: ★ 5 AÑOS EN LIMA] ║
║                            ║
║  Movilidad                 ║
║  corporativa               ║
║  con GPS                   ║
║  en Lima.      (H1 blanco) ║
║                            ║
║  ////  FOTO H350  ////     ║
║  ////  (ancho total) ////  ║
║                            ║
║  Cobertura Lima, Ica,      ║
║  Pisco y Huacho.           ║
║  Sin permanencia mínima.   ║
║                            ║
║  [→ SOLICITAR COTIZACIÓN ] ║
║  (botón amarillo · full w.)║
║                            ║
║  [💬 CONSULTAR WHATSAPP  ] ║
║  (botón verde · full w.)   ║
╚════════════════════════════╝

╔════════════════════════════╗
║  TRUST BAR — SCROLL HORIZ.║
║                            ║
║ [📡 GPS] [🕐 24/7] [👥17] ║
║ [📍Lima+] [5 años] →      ║
╚════════════════════════════╝

╔════════════════════════════╗
║  SERVICIOS — STACK VERTICAL║
║                            ║
║  ┌──────────────────────┐  ║
║  │ [🏢] Transporte      │  ║
║  │ Personal · B2B core  │  ║
║  │         [→ Ver]      │  ║
║  └──────────────────────┘  ║
║  ┌──────────────────────┐  ║
║  │ [✈] Traslado         │  ║
║  │ Aeropuerto           │  ║
║  │         [→ Ver]      │  ║
║  └──────────────────────┘  ║
║  ┌──────────────────────┐  ║
║  │ [💼] Corporativo     │  ║
║  │         [→ Ver]      │  ║
║  └──────────────────────┘  ║
║  ┌──────────────────────┐  ║
║  │ [🌄] Turístico       │  ║
║  │         [→ Ver]      │  ║
║  └──────────────────────┘  ║
║  ┌──────────────────────┐  ║
║  │ [👥] Grupos          │  ║
║  │         [→ Ver]      │  ║
║  └──────────────────────┘  ║
╚════════════════════════════╝

╔════════════════════════════╗
║  DIFERENCIADORES — 2 col   ║
║                            ║
║  ┌─────────┐  ┌─────────┐  ║
║  │[📡]GPS  │  │[👥]17px │  ║
║  │Control  │  │Un solo  │  ║
║  │total    │  │vehículo │  ║
║  └─────────┘  └─────────┘  ║
║  ┌─────────┐  ┌─────────┐  ║
║  │[🕐]24/7 │  │[📍]Lima │  ║
║  │Turnos   │  │+regiones│  ║
║  │rotativos│  │         │  ║
║  └─────────┘  └─────────┘  ║
║  ┌─────────┐  ┌─────────┐  ║
║  │[📋] Sin │  │[🌐] ES  │  ║
║  │contrato │  │/ EN     │  ║
║  │mínimo   │  │bilingüe │  ║
║  └─────────┘  └─────────┘  ║
╚════════════════════════════╝

╔════════════════════════════╗
║  SOCIAL PROOF — fondo negro║
║                            ║
║  Empresas que confían      ║
║  en Mayhil Express         ║
║                            ║
║  [LOGO 1] [LOGO 2] [LOGO 3]║
║  (scroll horizontal)       ║
╚════════════════════════════╝

╔════════════════════════════╗
║  FORMULARIO B2B — centrado ║
║                            ║
║  Solicita tu cotización    ║
║                            ║
║  [Nombre empresa         ] ║
║  [Responsable            ] ║
║  [Cargo                  ] ║
║  [Email corporativo      ] ║
║  [Teléfono               ] ║
║  [Cantidad personas   ▼  ] ║
║  [Frecuencia          ▼  ] ║
║  [Zona recojo            ] ║
║  [Zona destino           ] ║
║  [Horario                ] ║
║  [Mensaje         ↕      ] ║
║                            ║
║  [→ ENVIAR SOLICITUD     ] ║
║  (full width · amarillo)   ║
╚════════════════════════════╝

╔════════════════════════════╗
║  FLOTA — stack vertical    ║
║  ////  FOTO H350   ////   ║
║  ✓ 17 pasajeros            ║
║  ✓ GPS en tiempo real      ║
║  ✓ A/C · WiFi              ║
║  ✓ 24 horas                ║
╚════════════════════════════╝

╔════════════════════════════╗
║  COBERTURA TEASER — amari. ║
║  Lima · Ica · Pisco        ║
║  Huacho y periferias       ║
║  [VER COBERTURA COMPLETA ] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  CTA FINAL B2C             ║
║  ¿Aeropuerto o tour?       ║
║  [💬 WHATSAPP            ] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  FOOTER MOBILE             ║
║  [LOGO blanco]             ║
║  Movilidad corporativa     ║
║  en Lima, Perú.            ║
║  ─────────────────────     ║
║  SERVICIOS                 ║
║  · Transporte Personal     ║
║  · Aeropuerto              ║
║  · Corporativo             ║
║  ─────────────────────     ║
║  941 747 096               ║
║  servicio@mayhilexpress.com║
║  [💬 WhatsApp]             ║
║  ─────────────────────     ║
║  © 2026 Mayhil Express     ║
╚════════════════════════════╝

[💬 Flotante — der. abajo — siempre visible — 56px]
```

---

## 6. Wireframes — TRANSPORTE DE PERSONAL (`/servicios/transporte-de-personal/`)

*Página de mayor inversión. Recibe el tráfico B2B principal.*

### 6.1 Desktop

```
╔══════════════════════════════════════════════════════════════════════════════╗
║  [HEADER GLOBAL — sticky]                                                   ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  BREADCRUMB: Inicio > Servicios > Transporte de Personal                   ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  HERO — fondo negro · 60vh                                                  ║
║                                                                              ║
║   Transporte de personal para empresas                                       ║
║   en Lima, Ica, Pisco y Huacho.          (H1 blanco · grande)              ║
║                                                                              ║
║   Eliminamos el ausentismo causado por el transporte público.                ║
║   GPS en tiempo real · 24/7 · 17 pasajeros · Sin permanencia mínima.       ║
║                                           (párrafo blanco)                  ║
║                                                                              ║
║   [→ SOLICITAR COTIZACIÓN EMPRESARIAL]    (amarillo · grande)              ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — PROPUESTA DE VALOR · 3 columnas                                  ║
║  Fondo: #F5F5F5                                                             ║
║                                                                              ║
║  ┌────────────────────────┐  ┌────────────────────────┐  ┌───────────────┐ ║
║  │ [✓] Sin ausentismo     │  │ [✓] Control total      │  │ [✓] Sin       │ ║
║  │ Tu personal llega      │  │ Monitoreo GPS de cada  │  │ permanencia   │ ║
║  │ a tiempo, todos        │  │ ruta en tiempo real.   │  │ Solicita      │ ║
║  │ los días.              │  │ Tú decides y controlas.│  │ viaje a viaje.│ ║
║  └────────────────────────┘  └────────────────────────┘  └───────────────┘ ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN GPS — DIFERENCIADOR CENTRAL                                        ║
║  Fondo: negro · 2 columnas                                                  ║
║                                                                              ║
║  ┌──────────────────────────────────┐   ┌───────────────────────────────┐  ║
║  │                                  │   │ [📡] Monitoreo GPS            │  ║
║  │   ////  MOCKUP / FOTO GPS ////   │   │ en tiempo real                │  ║
║  │   ////  dashboard / ruta   ////  │   │                               │  ║
║  │   ////                     ////  │   │ Cada servicio que realizamos  │  ║
║  │                                  │   │ es trazado en tiempo real.    │  ║
║  └──────────────────────────────────┘   │ Tú sabes dónde está tu        │  ║
║                                         │ personal en todo momento.     │  ║
║                                         │                               │  ║
║                                         │ ✓ Registro de rutas           │  ║
║                                         │ ✓ Control de puntualidad      │  ║
║                                         │ ✓ Alertas de llegada          │  ║
║                                         │ ✓ Reportes de servicio        │  ║
║                                         └───────────────────────────────┘  ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN COBERTURA                                                          ║
║  Fondo: blanco · 2 columnas                                                 ║
║                                                                              ║
║  ┌──────────────────────────────────┐   ┌───────────────────────────────┐  ║
║  │ Cobertura en Lima y regiones     │   │   [Embed Google Maps o        │  ║
║  │                                  │   │    ilustración de cobertura]  │  ║
║  │ Lima Metropolitana:              │   │                               │  ║
║  │ Todos los distritos              │   │   ////  MAPA / ILUSTRACIÓN /  │  ║
║  │                                  │   │                               │  ║
║  │ Regiones:                        │   └───────────────────────────────┘  ║
║  │ · Ica y alrededores              │                                        ║
║  │ · Pisco y alrededores            │                                        ║
║  │ · Huacho y alrededores           │                                        ║
║  │                                  │                                        ║
║  │ Empresas con operaciones fuera   │                                        ║
║  │ de Lima nos eligen por nuestra   │                                        ║
║  │ cobertura regional única.        │                                        ║
║  │                                  │                                        ║
║  │ [→ VER COBERTURA COMPLETA]       │                                        ║
║  └──────────────────────────────────┘                                        ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN SOCIAL PROOF — "EMPRESAS QUE CONFÍAN"                             ║
║  Fondo: amarillo (#F5C400) · texto negro · centrado                         ║
║                                                                              ║
║  "Empresas que ya confían en Mayhil Express"                                ║
║                                                                              ║
║     [LOGO SEDAPAL]       [LOGO CLARO]       [LOGO MOVISTAR]                ║
║                                                                              ║
║  [Condicional — ver nota del Brief sobre autorización]                      ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — ¿CÓMO FUNCIONA? · 3 pasos                                       ║
║  Fondo: #F5F5F5                                                             ║
║                                                                              ║
║  Paso 1              Paso 2                  Paso 3                         ║
║  [1]                 [2]                     [3]                            ║
║  Solicita            Recibimos tu            Primer servicio                ║
║  tu cotización       solicitud y             sin compromiso                 ║
║  en este formulario  preparamos              de permanencia                 ║
║                      tu propuesta            mínima                         ║
║                      en 24 horas                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — FORMULARIO DE COTIZACIÓN B2B (embebido)                         ║
║  [Mismo componente global que en Home · max-width 800px centrado]           ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — FAQ TEASER · 4 preguntas B2B con accordion                      ║
║  Fondo: blanco                                                              ║
║                                                                              ║
║  [▸] ¿Tienen que firmar un contrato mínimo para empezar?                   ║
║  [▸] ¿Qué información necesitan para preparar una cotización?               ║
║  [▸] ¿El vehículo incluye monitoreo GPS en cada servicio?                  ║
║  [▸] ¿Pueden cubrir zonas fuera de Lima?                                   ║
║                                                                              ║
║               [→ VER TODAS LAS PREGUNTAS FRECUENTES]                       ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  [FOOTER GLOBAL]                                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 6.2 Mobile — Transporte de Personal

```
╔════════════════════════════╗
║  [HEADER STICKY]           ║
╚════════════════════════════╝

╔════════════════════════════╗
║  HERO                      ║
║  Transporte de personal    ║
║  para empresas en Lima.    ║
║  (H1 blanco · 36px)        ║
║                            ║
║  GPS · 24/7 · 17 pax       ║
║  Sin permanencia mínima.   ║
║                            ║
║  [→ SOLICITAR COTIZACIÓN ] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  PROPUESTA DE VALOR — stack║
║  [✓] Sin ausentismo        ║
║  [✓] Control GPS total     ║
║  [✓] Sin permanencia       ║
╚════════════════════════════╝

╔════════════════════════════╗
║  GPS — DESTACADO           ║
║  Fondo negro               ║
║  ////  FOTO GPS  ////      ║
║                            ║
║  [📡] GPS en tiempo real   ║
║  ✓ Registro de rutas       ║
║  ✓ Control de puntualidad  ║
║  ✓ Alertas de llegada      ║
╚════════════════════════════╝

╔════════════════════════════╗
║  COBERTURA                 ║
║  Lima · Ica · Pisco        ║
║  Huacho y periferias       ║
║  [VER COBERTURA COMPLETA ] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  SOCIAL PROOF — amarillo   ║
║  Empresas que confían:     ║
║  [L1] [L2] [L3] → scroll  ║
╚════════════════════════════╝

╔════════════════════════════╗
║  CÓMO FUNCIONA — vertical  ║
║  [1] Solicita cotización   ║
║  [2] Propuesta en 24h      ║
║  [3] Primer servicio       ║
╚════════════════════════════╝

╔════════════════════════════╗
║  FORMULARIO B2B            ║
║  [campos · full width]     ║
║  [→ ENVIAR SOLICITUD     ] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  FAQ ACCORDION — 4 items   ║
║  [▸] ¿Contrato mínimo?     ║
║  [▸] ¿Qué necesitan?       ║
║  [▸] ¿GPS incluido?        ║
║  [▸] ¿Fuera de Lima?       ║
╚════════════════════════════╝

╔════════════════════════════╗
║  [FOOTER GLOBAL]           ║
╚════════════════════════════╝
```

---

## 7. Wireframes — NOSOTROS (`/nosotros/`)

### 7.1 Desktop

```
╔══════════════════════════════════════════════════════════════════════════════╗
║  [HEADER GLOBAL]                                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  HERO — fondo negro · 50vh                                                  ║
║                                                                              ║
║   5 años garantizando que el personal                                        ║
║   de las empresas llega a tiempo.      (H1 blanco)                         ║
║                                                                              ║
║   Empresa de movilidad corporativa fundada en Lima, Perú.                   ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — HISTORIA · 2 columnas                                            ║
║  Fondo: blanco                                                              ║
║                                                                              ║
║  ┌──────────────────────────────────┐   ┌───────────────────────────────┐  ║
║  │ Quiénes somos                    │   │                               │  ║
║  │                                  │   │   ////  FOTO EQUIPO /         │  ║
║  │ Mayhil Express nació en Lima     │   │   ////  O VEHÍCULO  /         │  ║
║  │ con la misión de garantizar que  │   │   ////             /         │  ║
║  │ el personal de las empresas      │   │                               │  ║
║  │ llegue a tiempo, seguro y bajo   │   └───────────────────────────────┘  ║
║  │ control.                         │                                        ║
║  │                                  │                                        ║
║  │ 5 años de operación · Lima,      │                                        ║
║  │ Perú · Transporte corporativo    │                                        ║
║  │ y privado de pasajeros.          │                                        ║
║  └──────────────────────────────────┘                                        ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — VALORES · 4 columnas                                             ║
║  Fondo: #F5F5F5                                                             ║
║                                                                              ║
║  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐           ║
║  │[🕐]        │  │[🛡️]        │  │[📡]        │  │[⭐]        │           ║
║  │Puntualidad │  │Seguridad   │  │Control     │  │Compromiso  │           ║
║  │            │  │            │  │            │  │            │           ║
║  │Cada servicio│ │Conductores │  │GPS en cada │  │24/7 · 365  │           ║
║  │a tiempo,   │  │verificados │  │servicio    │  │días del año│           ║
║  │siempre.    │  │y uniformes.│  │para ti.    │  │            │           ║
║  └────────────┘  └────────────┘  └────────────┘  └────────────┘           ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — FLOTA · ficha técnica · 2 columnas                              ║
║  Fondo: negro                                                               ║
║                                                                              ║
║  ┌──────────────────────────────────┐   ┌───────────────────────────────┐  ║
║  │  Nuestra flota                   │   │                               │  ║
║  │                                  │   │  ////  FOTO H350 EXTERIOR /   │  ║
║  │  Hyundai H350                    │   │  ////  FOTO H350 INTERIOR /   │  ║
║  │  La unidad que garantiza         │   │  [galería de 2-3 fotos]       │  ║
║  │  seguridad y confort.            │   │                               │  ║
║  │                                  │   └───────────────────────────────┘  ║
║  │  ✓ Hasta 17 pasajeros            │                                        ║
║  │  ✓ GPS monitoreo tiempo real     │                                        ║
║  │  ✓ Aire acondicionado            │                                        ║
║  │  ✓ WiFi a bordo                  │                                        ║
║  │  ✓ Maletero amplio               │                                        ║
║  │  ✓ Mantenimiento preventivo      │                                        ║
║  └──────────────────────────────────┘                                        ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — DIFERENCIADORES · fondo blanco · igual que en Home               ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  CTA FINAL — fondo amarillo · centrado                                      ║
║                                                                              ║
║  ¿Necesitas transportar a tu personal?                                       ║
║  Solicita una cotización sin compromiso.                                     ║
║                                                                              ║
║              [→ SOLICITAR COTIZACIÓN EMPRESARIAL]                           ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  [FOOTER GLOBAL]                                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 7.2 Mobile — Nosotros

```
╔════════════════════════════╗
║  [HEADER STICKY]           ║
╚════════════════════════════╝

╔════════════════════════════╗
║  HERO — negro              ║
║  5 años garantizando       ║
║  que tu personal           ║
║  llega a tiempo.           ║
╚════════════════════════════╝

╔════════════════════════════╗
║  HISTORIA                  ║
║  ////  FOTO  ////          ║
║  Quiénes somos             ║
║  [texto 2 párrafos]        ║
╚════════════════════════════╝

╔════════════════════════════╗
║  VALORES — 2x2 grid        ║
║  ┌─────────┐  ┌─────────┐  ║
║  │[🕐]Punt.│  │[🛡️]Seg. │  ║
║  └─────────┘  └─────────┘  ║
║  ┌─────────┐  ┌─────────┐  ║
║  │[📡]GPS  │  │[⭐]24/7 │  ║
║  └─────────┘  └─────────┘  ║
╚════════════════════════════╝

╔════════════════════════════╗
║  FLOTA — fondo negro       ║
║  ////  FOTOS H350  ////    ║
║  Hyundai H350              ║
║  ✓ 17 pax  ✓ GPS          ║
║  ✓ A/C     ✓ WiFi         ║
╚════════════════════════════╝

╔════════════════════════════╗
║  CTA FINAL — amarillo      ║
║  ¿Necesitas transportar    ║
║  a tu personal?            ║
║  [→ SOLICITAR COTIZACIÓN ] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  [FOOTER GLOBAL]           ║
╚════════════════════════════╝
```

---

## 8. Wireframes — CONTACTO (`/contacto/`)

### 8.1 Desktop

```
╔══════════════════════════════════════════════════════════════════════════════╗
║  [HEADER GLOBAL]                                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  HERO — fondo negro · 40vh                                                  ║
║                                                                              ║
║   Solicita tu cotización de transporte                                       ║
║   o escríbenos por WhatsApp.           (H1 blanco)                         ║
║                                                                              ║
║   Respondemos en menos de 24 horas · Disponibles 24/7                      ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN PRINCIPAL — 2 columnas 60/40                                       ║
║  Fondo: blanco                                                              ║
║                                                                              ║
║  ┌──────────────────────────────────────────┐   ┌─────────────────────┐    ║
║  │ [Badge: 📋 EMPRESAS — COTIZACIÓN B2B]    │   │ ¿Traslado privado o │    ║
║  │                                          │   │ turismo?            │    ║
║  │ Formulario de cotización empresarial     │   │                     │    ║
║  │                                          │   │ Escríbenos directo  │    ║
║  │ [Nombre empresa         ]                │   │ por WhatsApp:       │    ║
║  │ [Responsable            ]                │   │                     │    ║
║  │ [Cargo                  ]                │   │ [💬 WHATSAPP      ] │    ║
║  │ [Email corporativo      ]                │   │                     │    ║
║  │ [Teléfono               ]                │   │ ──────────────────  │    ║
║  │ [Cant. personas ▼] [Frec. ▼]            │   │                     │    ║
║  │ [Zona recojo            ]                │   │ 📞 +51 941 747 096  │    ║
║  │ [Zona destino           ]                │   │                     │    ║
║  │ [Horario                ]                │   │ ✉ servicio@         │    ║
║  │ [Mensaje          ↕     ]                │   │ mayhilexpress.com   │    ║
║  │                                          │   │                     │    ║
║  │ [→ ENVIAR SOLICITUD DE COTIZACIÓN]       │   │ ⏰ Disponibles 24/7 │    ║
║  │                                          │   │                     │    ║
║  │ 🔒 Tus datos están seguros.             │   │ 📍 Lima, Perú       │    ║
║  └──────────────────────────────────────────┘   │ (dirección pendiente│    ║
║                                                  │  de validación)     │    ║
║                                                  └─────────────────────┘    ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — COBERTURA REMINDER                                               ║
║  Fondo: amarillo                                                            ║
║                                                                              ║
║  "Cubrimos Lima completa y llegamos a Ica, Pisco, Huacho y periferias."    ║
║                                                                              ║
║              [→ VER ZONAS DE COBERTURA]                                     ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SECCIÓN — MAPA (opcional)                                                  ║
║  Fondo: #F5F5F5                                                             ║
║                                                                              ║
║  [Google Maps embed — Lima, Perú]                                           ║
║  [Activar cuando se confirme dirección física]                              ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  [FOOTER GLOBAL]                                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 8.2 Mobile — Contacto

```
╔════════════════════════════╗
║  [HEADER STICKY]           ║
╚════════════════════════════╝

╔════════════════════════════╗
║  HERO — negro              ║
║  Solicita cotización       ║
║  o escríbenos por WA.      ║
╚════════════════════════════╝

╔════════════════════════════╗
║  B2C PRIMERO — mobile      ║
║  (los B2C buscan en móvil) ║
║  ¿Aeropuerto o turismo?    ║
║  [💬 WHATSAPP           ] ║
║  ────────────────────────  ║
║  📞 +51 941 747 096        ║
║  ✉ servicio@...com         ║
║  ⏰ 24 horas               ║
╚════════════════════════════╝

╔════════════════════════════╗
║  B2B — FORMULARIO          ║
║  [Badge: EMPRESAS]         ║
║  Cotización empresarial    ║
║                            ║
║  [Nombre empresa         ] ║
║  [Responsable            ] ║
║  [Cargo                  ] ║
║  [Email corporativo      ] ║
║  [Teléfono               ] ║
║  [Personas            ▼  ] ║
║  [Frecuencia          ▼  ] ║
║  [Zona recojo            ] ║
║  [Zona destino           ] ║
║  [Horario                ] ║
║  [Mensaje         ↕      ] ║
║                            ║
║  [→ ENVIAR SOLICITUD     ] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  COBERTURA — amarillo      ║
║  Lima · Ica · Pisco        ║
║  Huacho y periferias       ║
║  [VER ZONAS DE COBERTURA ] ║
╚════════════════════════════╝

╔════════════════════════════╗
║  [FOOTER GLOBAL]           ║
╚════════════════════════════╝
```

> **Nota mobile — Contacto:** En mobile, el bloque B2C (WhatsApp) aparece **antes** que el formulario B2B. La razón: los usuarios B2C típicamente buscan desde el móvil y su acción natural es el WhatsApp. Los decisores B2B suelen rellenar formularios desde desktop. Sin embargo, el formulario está igualmente disponible en mobile.

---

## 9. Wireframes — Páginas de Servicio Secundarias

*Estructura replicada para: Traslado Aeropuerto, Transporte Turístico, Transporte Grupos, Transporte Corporativo.*

### Estructura base (Desktop)

```
╔══════════════════════════════════════════════════════════════════════════════╗
║  [HEADER GLOBAL]                                                            ║
║  BREADCRUMB: Inicio > Servicios > [Nombre del servicio]                    ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  HERO — fondo negro · headline específico del servicio                      ║
║  [Keyword principal del servicio en H1] · subtítulo · CTA                  ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  DESCRIPCIÓN DEL SERVICIO · 2 columnas                                      ║
║  Texto descriptivo izq · Foto H350 der                                      ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  CARACTERÍSTICAS / BENEFICIOS · lista con íconos · 3 columnas              ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  CTA PRINCIPAL:                                                              ║
║  B2B → [→ SOLICITAR COTIZACIÓN] → formulario abajo / enlace a contacto     ║
║  B2C → [💬 RESERVAR POR WHATSAPP] → WhatsApp                               ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  SERVICIOS RELACIONADOS · 2-3 tarjetas de otros servicios                   ║
╚══════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════╗
║  [FOOTER GLOBAL]                                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Diferenciación por CTA según audiencia

| Página | CTA primario | CTA secundario |
|--------|-------------|----------------|
| Transporte Personal | Formulario B2B (embebido) | WhatsApp |
| Transporte Corporativo | Formulario B2B (enlace a contacto) | WhatsApp |
| Traslado Aeropuerto | WhatsApp (reserva inmediata) | Formulario |
| Transporte Turístico | WhatsApp (reserva inmediata) | Formulario |
| Transporte Grupos | Formulario (cant. personas) | WhatsApp |

---

## 10. Jerarquía Visual — Resumen por sección Home

| Prioridad | Elemento | Por qué |
|-----------|----------|---------|
| 1° | H1 del Hero | Lo que ves en 2 segundos — debe hablar B2B |
| 2° | Botón "Solicitar cotización" amarillo | Acción deseada inmediata |
| 3° | Trust bar amarilla | Confirma en 3 segundos que es serio (GPS, 24/7, 17 pax) |
| 4° | Logos SEDAPAL/CLARO/MOVISTAR | El mayor elemento de confianza B2B disponible |
| 5° | Formulario de cotización | Captura el lead sin necesidad de ir a /contacto/ |
| 6° | Cobertura regional | Resuelve la objeción "¿cubren mi zona?" antes de que la hagan |
| 7° | WhatsApp B2C | Visible pero no dominante — para el segmento secundario |

---

## 11. Recomendaciones Elementor Pro

| Elemento | Recomendación |
|----------|--------------|
| Estructura | Usar **Contenedores Flexbox** (no columnas clásicas) — más flexible y más rápido |
| Estilos globales | Configurar **Global Colors** y **Global Fonts** antes de diseñar ninguna página |
| Header | Construir en **Theme Builder → Header** — sticky, fondo negro, logo + menú + CTA |
| Footer | Construir en **Theme Builder → Footer** — reutilizable en todas las páginas |
| Formulario | Usar **Fluent Forms** — conectar directamente al widget Elementor Form |
| WhatsApp | Plugin **WP Social Chat** — configurar mensajes diferenciados por URL de página |
| Imágenes | Convertir a **WebP** antes de subir — usar Imagify o ShortPixel |
| Plantillas de página | Crear template de "Página de servicio" reutilizable para las 5 páginas de servicio |
| Animaciones | Mínimas — solo fade-in sutil en secciones. Sin parallax pesado (Core Web Vitals) |
| Sección social proof | Crear como **Global Widget** para reusar en Home y Transporte Personal sin duplicar |
| Formulario B2B | Crear como **Global Widget** en Elementor — reusar en Home, Transporte Personal y Contacto |
| Menú mobile | Usar **Elementor Nav Menu** — hamburguesa con drawer · incluir "Cotizar" como CTA |
| Breakpoints | Configurar breakpoints: 1200px (desktop) · 768px (tablet) · 390px (mobile) |
| Modo oscuro | No implementar — mantener paleta fija negro/amarillo/blanco |

---

## 12. Prompt Stitch / Figma

```
Diseña un sitio web corporativo B2B para "Mayhil Express", empresa de 
transporte de personal para empresas en Lima, Perú.

ESTILO VISUAL:
- Corporativo · Premium · B2B · Funcional
- Paleta: Negro (#111111) · Amarillo (#F5C400) · Blanco (#FFFFFF)
- Tipografía: Inter ExtraBold para títulos · Inter Regular para cuerpo
- Sin ilustraciones · íconos lineales simples · fotografías reales del vehículo Hyundai H350
- Tono: sólido, profesional, confiable — como una empresa de logística líder

PÚBLICO OBJETIVO:
- Primario: Gerentes de RRHH, Administración y Logística de empresas en Lima
- Secundario: Turistas, viajeros, familias que necesitan traslados

PÁGINA A DISEÑAR: Home (1200px desktop)

ESTRUCTURA DE SECCIONES:
1. Header sticky negro: logo amarillo izq + menú central + botón CTA "Solicitar cotización" amarillo der
2. Hero full-width negro: H1 blanco sobre imagen H350 · CTA amarillo grande "Solicitar cotización" + CTA verde secundario "WhatsApp"
3. Trust bar amarilla: 5 íconos con texto (GPS · 24/7 · 17 pax · Lima+regiones · 5 años)
4. Grid de servicios: 5 tarjetas blancas con ícono + título + descripción 2 líneas + link amarillo (Transporte Personal destacada con borde amarillo)
5. Diferenciadores: 6 bloques gris claro 3x2 con ícono amarillo + título + texto
6. Social proof: fondo negro, 3 logos de empresas (SEDAPAL, CLARO, MOVISTAR) en escala de grises sobre negro
7. Formulario cotización B2B: centrado max 800px · 11 campos · botón amarillo "Enviar solicitud"
8. Flota: 2 columnas · foto H350 izq · lista de specs der sobre fondo gris claro
9. Cobertura teaser: fondo amarillo · 4 zonas · botón ghost "Ver cobertura completa"
10. CTA B2C: blanco · headline H3 · botón verde WhatsApp
11. Footer negro: 4 columnas · logo + descripción / servicios / empresa / contacto

JERARQUÍA CRÍTICA:
- El CTA "Solicitar cotización" (amarillo) debe ser el elemento visualmente dominante en Hero y Formulario
- El GPS como diferenciador debe verse en Trust Bar Y en diferenciadores
- Los logos de empresas (social proof) son el segundo elemento de mayor peso visual después del Hero

RESTRICCIONES:
- No usar slides/carousels con autoplay
- No parallax pesado
- Botones con borde-radius 4px (no pill)
- Mobile-first: todos los grids colapsan a 1 columna en móvil
```

---

## 13. Checklist UX/UI

- [x] La propuesta de valor B2B se entiende en menos de 5 segundos (Hero H1)
- [x] El CTA principal (formulario cotización) es visible en el Hero y en el cuerpo de la página
- [x] Existe jerarquía visual clara: H1 → Trust bar → Servicios → Social proof → Formulario
- [x] El usuario B2B sabe exactamente qué hacer: rellenar el formulario de cotización
- [x] El usuario B2C sabe exactamente qué hacer: clic en WhatsApp
- [x] Hay elementos de confianza en la primera pantalla (trust bar)
- [x] Hay prueba social (SEDAPAL/CLARO/MOVISTAR) — Sección 5
- [x] Hay CTA intermedios (en secciones 3, 4, 7, 8)
- [x] Hay CTA final (footer + sección B2C)
- [x] El formulario B2B está embebido en Home — no requiere ir a otra página
- [x] La estructura mobile está definida con orden correcto
- [x] Los botones tienen tamaño mínimo de 44px en mobile (touch target)
- [x] El menú mobile es hamburguesa con drawer
- [x] El WhatsApp flotante es siempre visible sin obstruir contenido crítico
- [x] La navegación es clara: menú + breadcrumbs en subpáginas
- [x] Los formularios son simples: labels arriba, campos grandes, botón claro
- [x] El diseño favorece la conversión B2B (formulario) sin sacrificar B2C (WhatsApp)
- [x] Componentes reutilizables definidos para Elementor
- [x] Design system inicial definido (colores, tipografía, espaciado, tokens)
- [x] Recomendaciones de Elementor Pro documentadas
- [x] Prompt Stitch / Figma generado

---

*Documento producido por 04_UX_UI_DESIGNER · IA-WEB-STUDIO-OS · Mayhil Express · 2026-06-17 · Versión 1.0*

*Próximo agente: 05_COPYWRITER_WEB — Copy Home, Transporte Personal, FAQ, CTAs, versión EN*
