# Prompt Visual — Stitch / Figma · Mayhil Express Home

**Agente responsable:** 04_UX_UI_DESIGNER
**Fecha:** 2026-06-17
**Versión:** 1.0
**Estado:** Listo para usar en Stitch o Figma AI
**Basado en:** Brief v3.1 · PRD v3.0 · SEO Plan · Wireframes v1.0 · Copy v1.0

---

## Instrucciones de uso

1. Copiar el bloque de prompt entre las líneas `---PROMPT INICIO---` y `---PROMPT FIN---`
2. Pegarlo directamente en Stitch (stitch.withgoogle.com) o en Figma AI / Figma Make
3. Si el resultado no incluye alguna sección, regenerar especificando la sección faltante
4. Las versiones desktop y mobile pueden generarse como prompts independientes

**Recomendación:** Generar primero el desktop, luego el mobile referenciando el diseño anterior.

---

---PROMPT INICIO---

# Diseño de sitio web corporativo — Mayhil Express

## Contexto del proyecto

Diseña la página de inicio (Home) de **Mayhil Express**, empresa peruana de **transporte de personal para empresas** con 5 años de operación en Lima. El servicio principal (70% de ingresos) es el traslado de colaboradores corporativos con monitoreo GPS en tiempo real. Opera en todos los distritos de Lima y llega hasta Ica, Pisco y Huacho.

El sitio debe transmitir **solidez institucional B2B**, no turismo ni taxi. El visitante principal es un Gerente de RRHH o Jefe de Logística que busca un proveedor confiable, formal y con trazabilidad.

---

## Sistema de diseño — Referencia obligatoria

### Paleta de colores

```
Primario — Amarillo Mayhil:    #F5C400  → CTAs, botones, acentos, trust bar
Fondo oscuro — Negro Mayhil:   #111111  → Hero, header, footer, secciones premium
Blanco:                        #FFFFFF  → Fondos de sección, texto sobre negro
Gris claro:                    #F5F5F5  → Secciones alternadas, diferenciadores
Texto párrafo:                 #444444  → Cuerpo de texto
Texto secundario:              #888888  → Labels, metadata
WhatsApp verde:                #25D366  → Botón WhatsApp únicamente
Bordes:                        #E5E5E5  → Tarjetas, inputs del formulario
```

### Tipografía — Inter (Google Fonts)

```
H1 — Hero headline:      Inter ExtraBold 800  · 56px desktop / 34px mobile · blanco sobre negro
H2 — Títulos de sección: Inter Bold 700       · 38px desktop / 28px mobile · negro sobre blanco
H3 — Subtítulos / cards: Inter SemiBold 600   · 24px desktop / 20px mobile
Cuerpo texto:            Inter Regular 400    · 17px desktop / 16px mobile · #444444
Labels / Badges:         Inter SemiBold 600   · 13px · todo en mayúsculas
Botones:                 Inter Bold 700       · 16px
```

### Botones

```
Botón primario:
  → Fondo: #F5C400 amarillo
  → Texto: #111111 negro · bold
  → Padding: 14px 32px
  → Border-radius: 4px (NO pill, NO redondeado)
  → Hover: #D4A900 (amarillo más oscuro) + sombra sutil
  → Texto ejemplo: "→ SOLICITAR COTIZACIÓN EMPRESARIAL"

Botón WhatsApp:
  → Fondo: #25D366 verde
  → Texto: #FFFFFF blanco · bold
  → Ícono WhatsApp a la izquierda del texto
  → Mismo padding y border-radius
  → Texto ejemplo: "💬 CONSULTAR POR WHATSAPP"

Botón ghost / outline (sobre fondos oscuros):
  → Fondo: transparente
  → Borde: 1.5px solid #F5C400
  → Texto: #F5C400
  → Hover: rellena en #F5C400 con texto negro
```

### Tarjeta de servicio

```
→ Fondo: #FFFFFF
→ Border-radius: 8px
→ Sombra: 0 2px 16px rgba(0,0,0,0.08)
→ Padding: 24px
→ Ícono: 48px · línea · color #111111 o #F5C400
→ Título H3: negro
→ Descripción: 2 líneas · #444444
→ Link: "→ Ver servicio" · color #F5C400
→ Hover: borde superior 3px #F5C400 + sombra más pronunciada
→ Primera tarjeta (Transporte Personal): destacada con borde izquierdo 4px #F5C400
```

### Bloque diferenciador

```
→ Fondo: #FFFFFF
→ Border-radius: 8px
→ Padding: 24px
→ Ícono: 40px · color #F5C400
→ Título: Inter SemiBold · negro
→ Descripción: 2 líneas · #444444
→ Sin sombra
```

### Badge / Etiqueta

```
→ Forma: pill (border-radius: 100px)
→ Fondo: #F5C400 amarillo
→ Texto: #111111 negro · SemiBold · 12px · MAYÚSCULAS
→ Padding: 6px 14px
→ Ejemplo: "★ 5 AÑOS EN LIMA"
```

### Campo de formulario

```
→ Label: arriba del campo · Inter SemiBold · 13px · #444444
→ Input: altura 48px · borde 1px #E5E5E5 · border-radius 4px · padding 12px 16px
→ Focus: borde 2px #F5C400 (amarillo)
→ Placeholder: #888888 gris medio
→ Requerido: asterisco junto al label
→ Select/Dropdown: mismo estilo · flecha chevron derecha
```

---

## DISEÑO DESKTOP — 1440px de ancho · 1200px contenedor máximo

---

### SECCIÓN 0 — HEADER

```
Posición: fixed (sticky al hacer scroll) · z-index: 9999
Fondo: #111111 negro
Altura: 72px
Padding horizontal: 80px

Layout horizontal [space-between · align-center]:

  [LOGO] Mayhil Express
         → Logo en amarillo #F5C400 sobre negro
         → Ancho: 160px

  [MENÚ NAV] — centrado
         → Links: Servicios ▼  |  Nosotros  |  Cobertura  |  Preguntas Frecuentes
         → Fuente: Inter Medium 15px · color: #FFFFFF
         → Hover: color #F5C400
         → "Servicios" tiene dropdown indicator ▼

  [CTA HEADER]
         → Botón primario amarillo: "SOLICITAR COTIZACIÓN"
         → Padding reducido: 10px 24px

Separador inferior: línea 1px #222222
```

---

### SECCIÓN 1 — HERO

```
Fondo: #111111 negro
Altura: 90vh (mínimo 700px)
Padding horizontal: 80px

Layout 2 columnas [60% izquierda · 40% derecha · gap 64px · align-center]:

COLUMNA IZQUIERDA:
  [Badge]
    "★ 5 AÑOS TRANSPORTANDO EMPRESAS EN LIMA"
    → Pill amarillo · texto negro · margin-bottom 24px

  [H1 — principal]
    "Tu personal llega
    a tiempo.
    Tú sabes exactamente
    por qué."
    → Inter ExtraBold 800 · 56px · color #FFFFFF · line-height 1.1
    → Margin-bottom: 24px

  [Párrafo]
    "Transportamos hasta 17 colaboradores en un solo vehículo con
    monitoreo GPS en tiempo real. Cubrimos todos los distritos de Lima
    y llegamos hasta Ica, Pisco y Huacho. Disponibles las 24 horas,
    todos los días del año. Sin permanencia mínima."
    → Inter Regular 400 · 18px · color #CCCCCC · max-width 520px · line-height 1.6
    → Margin-bottom: 40px

  [CTAs — stack horizontal con gap 16px]
    Botón 1: "→ SOLICITAR COTIZACIÓN EMPRESARIAL" → amarillo #F5C400 · texto negro
    Botón 2: "💬 CONSULTAR POR WHATSAPP" → verde #25D366 · texto blanco

  [Microconfianza debajo de los botones]
    "Sin permanencia mínima · Respuesta en menos de 24 horas"
    → Inter Regular · 13px · color #888888 · margin-top 16px

COLUMNA DERECHA:
  [Imagen del vehículo Hyundai H350]
    → Fotografía real del Hyundai H350 exterior
    → Ángulo 3/4 frontal · sin marcos · sin bordes
    → Se funde con el fondo negro de la sección
    → Overlay gradiente negro-transparente desde la izquierda
    → Altura imagen: 500px · object-fit: cover
```

---

### SECCIÓN 2 — TRUST BAR

```
Fondo: #F5C400 amarillo
Padding: 20px 80px
Altura: ~90px

Layout: 5 columnas iguales [space-evenly · align-center]
Separadores verticales: 1px #D4A900 entre columnas

Columna 1: [📡 ícono negro] "GPS en tiempo real" / "Trazabilidad total"
Columna 2: [🕐 ícono negro] "Disponible 24/7" / "Los 365 días del año"
Columna 3: [👥 ícono negro] "Hasta 17 pasajeros" / "En un solo vehículo"
Columna 4: [📍 ícono negro] "Lima · Ica · Pisco" / "y Huacho"
Columna 5: [✓  ícono negro] "5 años de" / "operación formal"

Tipografía:
  → Línea 1: Inter Bold 700 · 14px · #111111
  → Línea 2: Inter Regular 400 · 13px · #333333
```

---

### SECCIÓN 3 — SERVICIOS

```
Fondo: #FFFFFF blanco
Padding: 80px 80px

[Header de sección — centrado]
  Título H2: "Nuestros servicios de transporte"
  Subtítulo: "Movilidad corporativa y privada en Lima y regiones"
  → Inter Regular 400 · 18px · #444444 · margin-top 12px

[Grid de 5 tarjetas — gap 24px · margin-top 48px]

TARJETA 1 — TRANSPORTE DE PERSONAL (DESTACADA)
  → Borde izquierdo 4px #F5C400
  → Badge "SERVICIO PRINCIPAL" → amarillo pequeño arriba
  → Ícono: personas entrando a edificio corporativo · 48px · negro
  → Título H3: "Transporte de Personal"
  → Descripción: "Para empresas que no pueden permitirse tardanzas. GPS en tiempo real, cobertura en Lima y regiones, 24/7."
  → Link: "→ Ver servicio" · #F5C400

TARJETA 2 — TRANSPORTE CORPORATIVO
  → Ícono: maletín ejecutivo · 48px
  → Título H3: "Transporte Corporativo"
  → Descripción: "Movilidad ejecutiva para reuniones, eventos y visitas de clientes. Imagen profesional garantizada."
  → Link: "→ Ver servicio"

TARJETA 3 — TRASLADO AEROPUERTO
  → Ícono: avión o terminal · 48px
  → Título H3: "Traslado al Aeropuerto"
  → Descripción: "Sin estrés, sin sorpresas. Al Aeropuerto Jorge Chávez a tiempo, con espacio para todo el equipaje."
  → Link: "→ Ver servicio"

TARJETA 4 — TRANSPORTE TURÍSTICO
  → Ícono: montaña o destino · 48px
  → Título H3: "Transporte Turístico"
  → Descripción: "Lima, Paracas, Huacachina e Ica en vehículo privado. Hasta 17 personas, en un solo viaje."
  → Link: "→ Ver servicio"

TARJETA 5 — TRANSPORTE PARA GRUPOS
  → Ícono: grupo de personas · 48px
  → Título H3: "Transporte para Grupos"
  → Descripción: "Hasta 17 pasajeros en una sola unidad. Sin dividir el grupo. Un precio, un vehículo."
  → Link: "→ Ver servicio"
```

---

### SECCIÓN 4 — DIFERENCIADORES

```
Fondo: #F5F5F5 gris claro
Padding: 80px 80px

[Header — centrado]
  Título H2: "¿Por qué elegir Mayhil Express?"
  Subtítulo: "Lo que nos diferencia de otros proveedores de transporte en Lima"

[Grid 3 columnas × 2 filas — gap 24px · margin-top 48px]
Fondo de cada bloque: #FFFFFF · border-radius 8px · padding 28px

BLOQUE 1: [📡 amarillo] "GPS en tiempo real"
  "Cada ruta trazada. Tú sabes dónde está tu personal en todo momento. Control y puntualidad garantizados."

BLOQUE 2: [👥 amarillo] "Hasta 17 colaboradores"
  "En un solo vehículo. Sin dividir al equipo ni coordinar varios autos. Una sola operación, un solo costo."

BLOQUE 3: [🕐 amarillo] "24/7 · 365 días"
  "Turnos rotativos, servicios nocturnos, días feriados. Siempre disponibles para tus operaciones."

BLOQUE 4: [📍 amarillo] "Lima completa + Ica, Pisco y Huacho"
  "Cobertura regional única en el mercado. Operamos donde tu empresa necesita llegar."

BLOQUE 5: [📋 amarillo] "Sin permanencia mínima"
  "Contratación por viaje. Prueba el servicio sin compromisos. Sin letras pequeñas."

BLOQUE 6: [🌐 amarillo] "Atención bilingüe ES / EN"
  "Para empresas multinacionales con personal o visitantes internacionales en Lima."

Estilo de cada bloque:
  → Ícono: 40px · color #F5C400
  → Título: Inter SemiBold 600 · 18px · negro · margin: 16px 0 8px
  → Texto: Inter Regular · 15px · #444444 · line-height 1.6
```

---

### SECCIÓN 5 — SOCIAL PROOF

```
Fondo: #111111 negro
Padding: 60px 80px

[Header — centrado]
  Título H2: "Empresas que confían en Mayhil Express"
  → Inter Bold 700 · 36px · color #FFFFFF
  Subtítulo: "Del sector telecomunicaciones y servicios públicos en Perú"
  → Inter Regular · 17px · color #888888 · margin-top 12px

[Logos — centrados · gap 80px · margin-top 40px]
  [Logo SEDAPAL] — escala de grises · ancho 160px · altura 48px · object-fit: contain · opacity 0.7
  [Logo CLARO]   — escala de grises · ancho 140px · altura 48px · object-fit: contain · opacity 0.7
  [Logo MOVISTAR]— escala de grises · ancho 160px · altura 48px · object-fit: contain · opacity 0.7

[Cita de apoyo — centrada · margin-top 32px]
  "Más de 5 años siendo el proveedor de confianza para el transporte
  de personal de empresas líderes en Lima y regiones."
  → #666666 · 15px · centrado
```

---

### SECCIÓN 6 — HYUNDAI H350 (FLOTA)

```
Fondo: #F5F5F5 gris claro
Padding: 80px 80px

Layout 2 columnas [50/50 · gap 64px · align-center]:

COLUMNA IZQUIERDA — Imagen:
  → Fotografía Hyundai H350 interior o exterior lateral
  → Border-radius: 12px
  → Sombra: 0 8px 40px rgba(0,0,0,0.12)
  → Altura: 480px · object-fit: cover

COLUMNA DERECHA — Contenido:
  [Chip] "NUESTRA FLOTA" → amarillo · margin-bottom 16px

  [Título H2]
    "Hyundai H350"
    "La unidad que garantiza seguridad y confort"
    → Negro · 36px · line-height 1.2

  [Párrafo · 17px · #444444 · margin: 20px 0 32px]
    "Contamos con la Hyundai H350, diseñada para el transporte
    colectivo corporativo. Capacidad, comodidad y tecnología
    para garantizar que tu personal llegue en las mejores condiciones."

  [Lista de especificaciones — íconos ✓ en amarillo]
    ✓ Hasta 17 pasajeros en un solo vehículo
    ✓ Monitoreo GPS en tiempo real
    ✓ Aire acondicionado
    ✓ WiFi a bordo
    ✓ Maletero amplio para equipaje
    ✓ Disponible 24 horas, todos los días
    ✓ Mantenimiento preventivo certificado
    → 16px negro · gap 12px entre ítems

  [CTA · margin-top 32px]
    Botón primario amarillo: "→ SOLICITAR COTIZACIÓN EMPRESARIAL"
```

---

### SECCIÓN 7 — TRANSPORTE DE PERSONAL B2B (DETALLE)

```
Fondo: #111111 negro
Padding: 80px 80px

Layout 2 columnas [50/50 · gap 64px · align-center]:

COLUMNA IZQUIERDA — Texto:
  [Chip] "SERVICIO PRINCIPAL" → amarillo

  [Título H2 blanco]
    "Movilidad corporativa
    con control total"
    → 40px · line-height 1.2

  [Párrafo · 17px · #CCCCCC · line-height 1.6]
    "Sabemos que el ausentismo causado por el transporte público le
    cuesta a tu empresa tiempo y dinero. Mayhil Express elimina ese
    problema: GPS en cada servicio, 17 colaboradores en un solo
    vehículo y cobertura donde tu empresa opera."

  [3 propuestas de valor — stack vertical · gap 20px · margin-top 32px]
  Cada bloque: fondo #1A1A1A · border-radius 8px · padding 20px · flex row con gap 16px

    BLOQUE A: [✓ amarillo] → Título blanco "Sin ausentismo por transporte"
    Texto #CCCCCC 15px "Tu personal llega a tiempo, todos los días. Garantizado."

    BLOQUE B: [📡 amarillo] → Título blanco "GPS en cada ruta"
    Texto #CCCCCC "Tú decides las rutas. Nosotros las ejecutamos y trazamos en tiempo real."

    BLOQUE C: [📋 amarillo] → Título blanco "Sin permanencia mínima"
    Texto #CCCCCC "Solicita el servicio viaje a viaje. Sin contratos que te aten."

  [CTA · margin-top 40px]
    Botón amarillo: "→ VER SERVICIO DE TRANSPORTE DE PERSONAL"

COLUMNA DERECHA — Visual GPS:
  → Mockup de dashboard GPS mostrando una ruta trazada sobre el mapa de Lima
  → Estilo: dark mode UI · fondo oscuro · línea de ruta en amarillo #F5C400
  → O: mapa oscuro de Lima con pines de ubicación y ruta conectando puntos
  → Border-radius: 12px
  → Sombra amarilla sutil: 0 0 40px rgba(245,196,0,0.15)
  → Altura: 460px
```

---

### SECCIÓN 8 — FORMULARIO DE COTIZACIÓN B2B

```
Fondo: #FFFFFF blanco
Padding: 80px 80px

[Header — centrado]
  [Chip] "📋 COTIZACIÓN EMPRESARIAL GRATUITA"
  Título H2: "Solicita tu cotización en minutos"
  Subtítulo: "Sin permanencia mínima · Respuesta garantizada en menos de 24 horas"
  → #444444 · 18px

[Card del formulario — max-width 760px · centrado · margin-top 48px]
  Fondo: #FFFFFF
  Borde: 1px solid #E5E5E5
  Border-radius: 12px
  Padding: 48px
  Sombra: 0 4px 32px rgba(0,0,0,0.08)

  [FILA 1 — 2 columnas gap 20px]
    Nombre de empresa *          |    Nombre del responsable *

  [FILA 2 — 2 columnas]
    Cargo                        |    Email corporativo *

  [FILA 3 — 2 columnas]
    Teléfono *                   |    Cantidad de personas * [Select ▼]
                                       Opciones: 1-10 / 11-17 / Más de 17 / Por definir

  [FILA 4 — 2 columnas]
    Frecuencia [Select ▼]        |    Horario aproximado
    Diario/Semanal/Puntual/Def.

  [FILA 5 — 2 columnas]
    Zona de recojo               |    Zona de destino

  [FILA 6 — 1 columna]
    Mensaje adicional [Textarea 3 líneas]

  [CTA — full width · margin-top 8px]
    Botón amarillo grande: "→ ENVIAR SOLICITUD DE COTIZACIÓN"
    → Altura 52px · full width · Inter Bold 700 · 17px

  [Texto de tranquilidad — centrado · margin-top 16px]
    "🔒 Tus datos están seguros. Solo los usamos para preparar tu propuesta."
    → 13px · #888888

  [Indicadores de confianza — 3 ítems horizontales · margin-top 20px]
    ⏱ Respuesta en 24h   ·   🔒 Datos protegidos   ·   ✓ Sin compromiso
    → 13px · #888888 · centrados
```

---

### SECCIÓN 9 — COBERTURA (TEASER)

```
Fondo: #F5C400 amarillo
Padding: 64px 80px

[Header — centrado]
  Título H2 negro: "Cubrimos toda Lima y llegamos hasta donde tu empresa opera"

[Grid 4 zonas — centrado · gap 48px · margin-top 40px]
Separadores verticales: 1px negro con 30% opacidad

ZONA 1: [📍 ícono negro 40px] "Lima Metropolitana" / "Todos los distritos"
ZONA 2: [📍 ícono negro 40px] "Ica" / "y alrededores · agroindustria"
ZONA 3: [📍 ícono negro 40px] "Pisco" / "y alrededores · pesca"
ZONA 4: [📍 ícono negro 40px] "Huacho" / "y periferias · industria"

Cada zona: centrado · ícono arriba · nombre bold arriba · descripción gris abajo

[CTA — centrado · margin-top 40px]
  Botón outline negro: "→ VER COBERTURA COMPLETA"
  → Borde negro · texto negro · fondo transparente
  → Hover: fondo negro · texto amarillo
```

---

### SECCIÓN 10 — CTA WHATSAPP (B2C)

```
Fondo: #FFFFFF blanco
Padding: 64px 80px · centrado

[Contenido — max-width 600px · centrado]
  Título H3 negro: "¿Necesitas un traslado al aeropuerto o un tour privado?"
  Párrafo 17px #444444:
    "Para traslados individuales, aeropuerto o turismo, cotiza rápido
    y fácil directo por WhatsApp. Respondemos al instante."

  [CTA — centrado · margin-top 32px]
    Botón verde: "💬 CONSULTAR POR WHATSAPP" · padding 16px 40px

  Texto bajo botón:
    "También por: +51 941 747 096 · servicio@mayhilexpress.com"
    → 14px · #888888 · centrado · margin-top 16px
```

---

### SECCIÓN 11 — FOOTER

```
Fondo: #111111 negro
Padding: 64px 80px 32px

[Grid 4 columnas — gap 48px · padding-bottom 48px]

COLUMNA 1: Logo blanco 160px + tagline
  "Movilidad corporativa y privada en Lima, Ica, Pisco y Huacho."
  → #888888 · 15px · max-width 220px

COLUMNA 2: SERVICIOS
  → Título: "SERVICIOS" · #F5C400 · 12px · SemiBold · letter-spacing 1px
  · Transporte de Personal
  · Transporte Corporativo
  · Traslado al Aeropuerto
  · Transporte Turístico
  · Transporte para Grupos
  → Links: #CCCCCC · 15px · gap 10px

COLUMNA 3: EMPRESA
  → Título: "EMPRESA" · mismo estilo
  · Nosotros · Cobertura · FAQ · Contacto

COLUMNA 4: CONTACTO
  → Título: "CONTACTO" · mismo estilo
  📞 +51 941 747 096 → blanco
  ✉ servicio@mayhilexpress.com → blanco
  [Botón WhatsApp verde pequeño] "💬 WhatsApp"

[Separador: 1px #222222]
[Barra inferior: padding-top 24px]
  "© 2026 Mayhil Express · Lima, Perú" ←izq  |  "Política de Privacidad" →der
  → 14px · #666666

[Widget WhatsApp flotante — fijo · esquina inferior derecha]
  → Circular · fondo #25D366 · 56px diámetro
  → Sombra: 0 4px 16px rgba(0,0,0,0.3)
  → 24px desde borde derecho y 24px desde borde inferior
  → Siempre visible en todas las páginas
```

---

## DISEÑO MOBILE — 390px de ancho (iPhone 15 Pro)

Los mismos colores, tipografía Inter y componentes del desktop.
Padding horizontal: 24px en todas las secciones.
Todo colapsa a 1 columna excepto donde se especifica grids de 2.

---

### HEADER MOBILE

```
Fondo: #111111 negro · altura 60px · padding 0 24px
[LOGO amarillo 140px] ←izq          [≡ 28px blanco] →der

Drawer al abrir: fondo #1A1A1A · links verticales con separadores · CTA al fondo
→ [SOLICITAR COTIZACIÓN] botón amarillo full-width en el drawer
```

---

### HERO MOBILE

```
Fondo: negro · padding: 88px 24px 60px (espacio para header fijo)

[Badge amarillo centrado] "★ 5 AÑOS EN LIMA"

[H1 blanco · centrado · 34px · ExtraBold]
  "Tu personal llega a tiempo.
  Tú sabes exactamente por qué."

[Imagen H350 — full-width · altura 220px · object-fit: cover · border-radius 8px · margin 24px 0]

[Párrafo blanco atenuado · 15px · centrado]
  "Hasta 17 personas · GPS real · Lima, Ica, Pisco y Huacho. Sin permanencia mínima."

[CTAs — stack vertical · gap 12px · margin-top 32px]
  [→ SOLICITAR COTIZACIÓN]  → amarillo · full-width · 52px altura
  [💬 WHATSAPP]             → verde   · full-width · 52px altura
```

---

### TRUST BAR MOBILE

```
Fondo: #F5C400 amarillo · padding 16px 0
Scroll horizontal (swipe) — 5 elementos · gap 8px · padding-left 24px

Cada elemento: 120px ancho mínimo · flex-shrink 0
[📡 GPS]       [🕐 24/7]      [👥 17 pax]     [📍 Lima+]     [✓ 5 años]
→ Texto 2 líneas · 12px negro bold / 11px regular
→ Indicador de scroll: puntos o fade en el borde derecho
```

---

### SERVICIOS MOBILE

```
Fondo: blanco · padding 48px 24px

Título H2 centrado 28px

[Stack vertical · 5 tarjetas · gap 16px · margin-top 32px]
Cada tarjeta: layout horizontal [ícono izq 40px · texto der]
→ Ícono + Título 16px bold + Descripción 14px 2 líneas + "→ Ver servicio" 14px amarillo
→ Padding 16px · border-radius 8px · borde 1px #E5E5E5

Primera tarjeta: borde izquierdo 4px #F5C400
```

---

### DIFERENCIADORES MOBILE

```
Fondo: #F5F5F5 · padding 48px 24px
Título H2 centrado

[Grid 2 columnas · 3 filas · gap 12px · margin-top 32px]
6 bloques pequeños · padding 16px · border-radius 8px · fondo blanco
Ícono 32px amarillo · Título 14px bold negro · Texto 13px #444444 2 líneas
```

---

### SOCIAL PROOF MOBILE

```
Fondo: #111111 negro · padding 48px 24px

Título H2 blanco centrado 26px

[Logos — scroll horizontal o stack vertical centrado]
SEDAPAL · CLARO · MOVISTAR
→ Escala de grises · altura 40px · opacity 0.7 · gap 32px
```

---

### HYUNDAI H350 MOBILE

```
Fondo: #F5F5F5 · padding 48px 24px

Stack vertical:

[Imagen H350 — full-width · altura 240px · border-radius 8px · object-fit cover]

[Chip amarillo] "NUESTRA FLOTA"
[Título H2 negro] "Hyundai H350" 28px

[Párrafo 15px #444444 · line-height 1.6]

[Lista specs · gap 10px]
✓ amarillo · texto negro 15px · 7 ítems

[Botón amarillo full-width] "→ SOLICITAR COTIZACIÓN"
```

---

### TRANSPORTE DE PERSONAL MOBILE

```
Fondo: #111111 negro · padding 48px 24px

Stack vertical:

[Visual GPS / mapa dark mode]
→ full-width · altura 200px · border-radius 8px · sombra amarilla sutil

[Chip amarillo] "SERVICIO PRINCIPAL"
[Título H2 blanco] "Movilidad corporativa con control total" 28px

[Párrafo #CCCCCC 15px · line-height 1.6]

[3 bloques propuesta de valor — stack vertical · gap 12px]
Cada bloque: fondo #1A1A1A · border-radius 8px · padding 16px · layout row
[Ícono amarillo 24px] + [Título blanco 15px bold · Texto #CCCCCC 14px]

[Botón amarillo full-width] "→ VER SERVICIO DE TRANSPORTE"
```

---

### FORMULARIO B2B MOBILE

```
Fondo: blanco · padding 48px 24px

Título H2 centrado 26px
Subtítulo 15px centrado

[Card formulario — full-width · border-radius 12px · padding 24px · sombra suave]

Todos los campos en stack vertical (1 columna):
  Nombre de empresa *
  Nombre del responsable *
  Cargo
  Email corporativo *
  Teléfono *
  Cantidad de personas [Select full-width ▼]
  Frecuencia [Select full-width ▼]
  Zona de recojo
  Zona de destino
  Horario aproximado
  Mensaje adicional [Textarea 4 líneas]

[Botón amarillo full-width · 52px altura]
"→ ENVIAR SOLICITUD DE COTIZACIÓN"

[Texto confianza centrado · 12px · #888888]
"🔒 Datos seguros · Sin compromiso"
```

---

### COBERTURA TEASER MOBILE

```
Fondo: #F5C400 amarillo · padding 48px 24px

Título H2 negro centrado

[Grid 2×2 · gap 12px · margin-top 32px]
[📍 Lima Metropolitana] | [📍 Ica y alrededores]
[📍 Pisco y alrededores]| [📍 Huacho y periferias]

Cada zona: fondo rgba(0,0,0,0.08) · padding 14px · border-radius 8px · centrado
→ Ícono + nombre bold + descripción 12px

[Botón outline negro full-width · margin-top 24px]
"→ VER COBERTURA COMPLETA"
```

---

### CTA WHATSAPP MOBILE

```
Fondo: blanco · padding 40px 24px · centrado

[Título H3 negro 22px centrado]
"¿Aeropuerto o tour privado?"

[Párrafo 15px #444444 centrado]
"Cotiza rápido por WhatsApp. Respondemos al instante."

[Botón verde full-width · 52px · margin-top 24px]
"💬 CONSULTAR POR WHATSAPP"

[Texto 14px #888888 centrado · margin-top 12px]
"+51 941 747 096"
```

---

### FOOTER MOBILE

```
Fondo: #111111 negro · padding 48px 24px 32px

[Logo blanco centrado · 160px]
["Movilidad corporativa en Lima, Perú." centrado · #888888 14px · margin-bottom 32px]

SERVICIOS — lista vertical · #CCCCCC 15px · gap 10px
EMPRESA   — lista vertical · mismo estilo
CONTACTO  — teléfono + email blanco · botón WhatsApp verde full-width

[Separador 1px #222222 · margin: 32px 0]
["© 2026 Mayhil Express · Lima, Perú" · 12px #666666 centrado]

[Widget WhatsApp flotante · inferior derecho · fijo · 56px]
```

---

## Restricciones de diseño — NO violar

```
❌ NO carruseles con autoplay
❌ NO parallax pesado
❌ NO border-radius > 12px en secciones principales
❌ NO ilustraciones genéricas — toda imagen referencia el vehículo H350 real
❌ NO colores fuera del sistema (morado, azul, rojo)
❌ NO tipografías distintas a Inter
❌ NO hacer WhatsApp el elemento visualmente dominante — es CTA secundario
❌ NO gradients multicolor — solo fondos sólidos del sistema

✅ Prioridad visual 1: H1 del Hero — legible en 2 segundos
✅ Prioridad visual 2: Botón "Solicitar cotización" amarillo — visible above the fold
✅ Prioridad visual 3: Trust bar amarilla — credibilidad inmediata
✅ Prioridad visual 4: Logos sociales proof (SEDAPAL/CLARO/MOVISTAR)
✅ Prioridad visual 5: Formulario B2B — herramienta profesional, no widget de contacto
✅ Botones: border-radius 4px exactamente (no pill, no cuadrado)
✅ El H350 aparece en Hero, Flota y Transporte Personal
✅ Espaciado entre secciones: 80px desktop / 48px mobile
✅ Contraste mínimo WCAG AA en todos los textos
```

---

## Tono visual de referencia

```
El sitio debe sentirse como:
  → Empresa de logística corporativa premium (DHL, G4S, Sodexo — tono B2B serio)
  → Empresa de servicios B2B formal en LATAM

NO debe sentirse como:
  → Agencia de viajes o tour operador
  → Aplicación de taxi o ride-hailing (minimalismo excesivo)
  → Microempresa o proveedor informal
```

---PROMPT FIN---

---

## Secciones incluidas en el prompt

| # | Sección | Desktop | Mobile |
|---|---------|:-------:|:------:|
| 0 | Header sticky | ✅ | ✅ |
| 1 | Hero con Hyundai H350 | ✅ | ✅ |
| 2 | Trust Bar (GPS · 24/7 · 17 pax · Lima+ · 5 años) | ✅ | ✅ |
| 3 | Servicios — 5 tarjetas B2B-first | ✅ | ✅ |
| 4 | Diferenciadores — 6 bloques | ✅ | ✅ |
| 5 | Social Proof (SEDAPAL / CLARO / MOVISTAR) | ✅ | ✅ |
| 6 | Hyundai H350 — flota y especificaciones | ✅ | ✅ |
| 7 | Transporte de Personal — detalle B2B | ✅ | ✅ |
| 8 | Formulario de cotización B2B (11 campos) | ✅ | ✅ |
| 9 | Cobertura Lima / Ica / Pisco / Huacho | ✅ | ✅ |
| 10 | CTA WhatsApp B2C | ✅ | ✅ |
| 11 | Footer con 4 columnas | ✅ | ✅ |
| — | Widget WhatsApp flotante | ✅ | ✅ |

---

## Notas para el diseñador

**Imágenes placeholder:**
Si no hay fotos reales del H350, usar imagen de minibus corporativo oscuro 17 pasajeros.
No usar imágenes de taxi, sedán ni vehículos genéricos.

**GPS mockup:**
Si no hay captura del sistema GPS real, usar Google Maps en dark mode con ruta dibujada sobre Lima, marcadores amarillos en origen/destino.

**Logos sociales proof:**
SEDAPAL, CLARO y MOVISTAR en escala de grises sobre negro. Opacity 0.7 en reposo.
Si no están disponibles, reemplazar con texto en cursiva entre comillas.

**Variante de headline:**
Este prompt usa la Variante A recomendada por el Copywriter.
Para testing: Variante B = "El ausentismo por transporte ya tiene solución."

**Accesibilidad:**
Negro #111111 sobre amarillo #F5C400 pasa WCAG AA.
Blanco #FFFFFF sobre negro #111111 pasa WCAG AAA.
Mantener siempre estos pares de contraste.

---

*Documento producido por 04_UX_UI_DESIGNER · IA-WEB-STUDIO-OS · Mayhil Express · 2026-06-17 · Versión 1.0*

*Uso: Copiar el bloque entre ---PROMPT INICIO--- y ---PROMPT FIN--- en Stitch o Figma AI*

*Documentos relacionados: 04_WIREFRAMES.md (estructura) · 05_COPY.md (textos) · 06_WORDPRESS_IMPLEMENTACION.md (desarrollo)*
