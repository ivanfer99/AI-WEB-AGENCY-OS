# PRD — Mayhil Express

**Tipo de proyecto:** Web Corporativa
**Cliente:** Mayhil Express
**Dominio:** mayhilexpress.com
**Fecha:** 2026-06-17
**Estado:** Borrador — Pendiente aprobación del cliente
**Basado en:** 01_BRIEF_CLIENTE.md

---

## 1. Resumen Ejecutivo

Mayhil Express necesita un sitio web corporativo que funcione como canal principal de captación de clientes. El objetivo no es informar: es **convertir visitas en contactos por WhatsApp**.

La web debe transmitir seguridad, puntualidad y profesionalismo. El visitante debe entender en menos de 5 segundos qué ofrece Mayhil Express, para quién es y cómo contratar el servicio. El CTA dominante en todo el sitio es un único mensaje claro: **"Cotiza por WhatsApp"**.

Arquitectura objetivo:

```
Visita orgánica (Google / referido)
        ↓
    Home / Página de servicio
        ↓
    CTA: Cotiza por WhatsApp
        ↓
    Conversación WhatsApp → Lead calificado
```

---

## 2. Objetivos del Proyecto

### Objetivo principal
Generar solicitudes de cotización y contactos directos vía WhatsApp (+51 941 747 096).

### Objetivos secundarios
| Objetivo | Cómo se resuelve en el sitio |
|----------|------------------------------|
| Mejorar imagen profesional | Diseño corporativo moderno, fotos reales, copy orientado a confianza |
| Posicionar en Google | SEO on-page con Rank Math, páginas por servicio, keywords locales |
| Captar turistas | Versión en inglés del sitio, keywords turísticas |
| Captar empresas | Sección de Transporte Corporativo destacada, tono B2B |
| Generar confianza | Diferenciadores, vehículo, atención 24/7, datos de contacto visibles |

---

## 3. Público Objetivo

| Segmento | Necesidad principal | Canal de llegada esperado |
|----------|--------------------|-----------------------------|
| Turistas internacionales | Traslado seguro desde el aeropuerto | Google (EN), recomendación de hotel |
| Turistas nacionales | Traslado cómodo sin complicaciones | Google (ES), redes sociales |
| Familias | Espacio para equipaje, seguridad | Google, recomendación |
| Ejecutivos y profesionales | Puntualidad, imagen, privacidad | Google, directorio empresarial |
| Empresas y áreas de RRHH | Contrato recurrente para movilidad de personal | Google, referidos |
| Hoteles y agencias de viaje | Proveedor confiable para sus clientes | Contacto directo, directorio |

---

## 4. Alcance del Proyecto

### Dentro del alcance

- Sitio web corporativo bilingüe (ES / EN)
- 9 páginas (ver Sección 5)
- Widget de WhatsApp flotante
- Formulario de contacto
- SEO on-page básico con Rank Math
- Optimización responsive (mobile-first)
- Integración con Google Analytics 4 y Search Console

### Fuera del alcance

- Ecommerce o tienda online
- Pasarela de pago
- Sistema de reservas automático
- Área privada o login de clientes
- CRM
- Blog (queda como módulo opcional de fase 2)

---

## 5. Sitemap

```
/                                      → Inicio
/nosotros/                             → Nosotros
/servicios/                            → Servicios (hub)
  /servicios/traslado-aeropuerto/      → Traslado al Aeropuerto
  /servicios/transporte-corporativo/   → Transporte Corporativo
  /servicios/transporte-turistico/     → Transporte Turístico
  /servicios/transporte-grupos/        → Transporte para Grupos
/preguntas-frecuentes/                 → Preguntas Frecuentes
/contacto/                             → Contacto
```

**Total: 9 páginas en español.**

Versión en inglés (prefijo de idioma vía plugin):

```
/en/
/en/about/
/en/services/
  /en/services/airport-transfer/
  /en/services/corporate-transport/
  /en/services/tourist-transport/
  /en/services/group-transport/
/en/faq/
/en/contact/
```

---

## 6. Páginas — Especificación de Contenido

### 6.1 Inicio (`/`)

**Objetivo:** Captar la atención del visitante y dirigirlo al CTA en menos de 5 segundos.

| Sección | Contenido | CTA |
|---------|-----------|-----|
| Hero | Headline principal + subheadline + foto del Hyundai H350 | "Cotiza por WhatsApp" |
| Barra de confianza | Íconos: 24/7 · Puntualidad · Seguridad · WiFi | — |
| Servicios (resumen) | 4 tarjetas de servicio con ícono y enlace | "Ver servicio" |
| ¿Por qué Mayhil Express? | 4–5 diferenciadores con íconos | — |
| Flota destacada | Foto real del H350 + características (17 pax, A/C, WiFi, equipaje) | "Solicitar traslado" |
| Testimonios | Pendiente — reservar sección para fase 2 | — |
| CTA final | Bloque de cierre con número y botón WhatsApp | "Cotiza ahora por WhatsApp" |

---

### 6.2 Nosotros (`/nosotros/`)

**Objetivo:** Generar confianza y humanizar la marca.

| Sección | Contenido |
|---------|-----------|
| Historia | 5 años en el mercado, origen y misión de la empresa |
| Misión y valores | Seguridad · Puntualidad · Confort · Atención personalizada |
| Nuestra flota | Hyundai H350 — ficha técnica, fotos reales, capacidad, equipamiento |
| Por qué elegirnos | Diferenciadores en formato visual |
| CTA | "¿Listo para reservar? Contáctanos por WhatsApp" |

---

### 6.3 Servicios — Hub (`/servicios/`)

**Objetivo:** Orientar al visitante hacia la subpágina de su servicio específico.

- 4 tarjetas de servicio con imagen, descripción breve y enlace
- CTA global al final: WhatsApp

---

### 6.4 Traslado al Aeropuerto (`/servicios/traslado-aeropuerto/`)

**Keyword principal:** `traslado aeropuerto lima` / `van aeropuerto lima`

| Sección | Contenido |
|---------|-----------|
| Hero | Headline enfocado en el servicio + CTA |
| Descripción | Traslado al y desde el Aeropuerto Internacional Jorge Chávez |
| Cómo funciona | Proceso simple: reserva → confirmación → recojo puntual |
| Características | H350, 17 pasajeros, equipaje amplio, A/C, WiFi |
| ¿Para quién es? | Familias, grupos, ejecutivos, turistas |
| Cobertura | Lima y distritos (Pendiente definir con cliente) |
| CTA | "Cotiza tu traslado por WhatsApp" |

---

### 6.5 Transporte Corporativo (`/servicios/transporte-corporativo/`)

**Keyword principal:** `transporte corporativo lima`

| Sección | Contenido |
|---------|-----------|
| Hero | Propuesta de valor B2B + CTA |
| ¿Qué incluye? | Movilidad para personal, eventos corporativos, reuniones |
| Ventajas para empresas | Puntualidad, disponibilidad 24/7, atención personalizada |
| Tipo de cliente | Empresas, RRHH, ejecutivos, hoteles |
| CTA | "Solicita una propuesta por WhatsApp" |

---

### 6.6 Transporte Turístico (`/servicios/transporte-turistico/`)

**Keyword principal:** `transporte turístico lima`

| Sección | Contenido |
|---------|-----------|
| Hero | Explora Lima con seguridad y comodidad + CTA |
| ¿Qué incluye? | City tours, visitas a destinos, recorridos personalizados |
| Ventajas | Vehículo privado, WiFi, A/C, capacidad para grupos |
| Destinos frecuentes | Pendiente confirmar con cliente |
| CTA | "Planifica tu recorrido por WhatsApp" |

---

### 6.7 Transporte para Grupos (`/servicios/transporte-grupos/`)

**Keyword principal:** `transporte privado grupos lima`

| Sección | Contenido |
|---------|-----------|
| Hero | Hasta 17 pasajeros, un solo vehículo + CTA |
| ¿Para quién? | Familias grandes, grupos de amigos, equipos corporativos |
| Ventajas | Sin dividir el grupo, equipaje amplio, precio único |
| CTA | "Cotiza para tu grupo por WhatsApp" |

---

### 6.8 Preguntas Frecuentes (`/preguntas-frecuentes/`)

**Objetivo:** Reducir fricción, resolver objeciones y aportar contenido SEO de cola larga.

Preguntas propuestas (a validar con el cliente):

1. ¿Con cuánta anticipación debo reservar mi traslado?
2. ¿El servicio funciona las 24 horas?
3. ¿Cuánto equipaje puedo llevar?
4. ¿Atienden grupos grandes?
5. ¿Cómo confirmo mi reserva?
6. ¿El vehículo tiene WiFi y aire acondicionado?
7. ¿Hacen traslados fuera de Lima?
8. ¿Tienen atención en inglés?

---

### 6.9 Contacto (`/contacto/`)

**Objetivo:** Ofrecer múltiples canales de contacto con fricción mínima.

| Elemento | Detalle |
|----------|---------|
| Botón WhatsApp principal | +51 941 747 096 con mensaje preconfigurado |
| Formulario de contacto | Nombre · Teléfono · Servicio de interés · Mensaje |
| Email visible | servicio@mayhilexpress.com |
| Horario de atención | 24/7 |
| Mapa | Ubicación en Lima (Pendiente confirmar dirección) |

**Mensaje preconfigurado de WhatsApp:**
```
Hola, me gustaría cotizar un servicio de transporte con Mayhil Express.
```

---

## 7. Funcionalidades

| Funcionalidad | Prioridad | Herramienta |
|---------------|-----------|-------------|
| Widget WhatsApp flotante | Alta | WP Social Chat o similar |
| Formulario de contacto | Alta | Fluent Forms |
| Multiidioma ES / EN | Alta | WPML o Polylang |
| Galería de fotos del vehículo | Media | Elementor Gallery |
| SEO on-page | Alta | Rank Math |
| Responsive / mobile-first | Alta | Elementor Pro |
| Google Analytics 4 | Alta | GTM |
| Google Tag Manager | Alta | Plugin GTM |
| Blog | No — fase 2 | — |
| Ecommerce | No | — |
| Reservas automáticas | No | — |
| Área privada | No | — |
| Pasarela de pago | No | — |

---

## 8. Branding y Diseño

### Paleta de colores

| Rol | Color | Uso |
|-----|-------|-----|
| Primario | Amarillo (confirmar hex con logo) | CTAs, acentos, botones, íconos |
| Secundario | Negro (`#111111`) | Fondos oscuros, navbar, texto principal |
| Neutro | Blanco (`#FFFFFF`) | Fondos, tarjetas, espaciado |
| Texto cuerpo | Gris oscuro (`#333333`) | Párrafos, descripciones |

### Tipografía sugerida

| Rol | Tipografía | Tipo |
|-----|-----------|------|
| Títulos (H1–H2) | Montserrat Bold o Inter Bold | Sans-serif moderna |
| Cuerpo | Open Sans o Inter Regular | Legible, neutra |

*Ajustar si el cliente tiene tipografías definidas en su identidad de marca.*

### Estilo visual
- Profesional · Corporativo · Moderno · Confiable
- Fotografías reales del H350 como activo visual principal
- Íconos lineales o filled — sin ilustraciones
- Espaciado generoso, sin saturación de información
- Botones de CTA en amarillo sobre negro para máximo contraste

---

## 9. SEO On-Page

### Keywords por página

| Página | Keyword principal | Keywords secundarias |
|--------|-------------------|----------------------|
| Inicio | transporte privado lima | servicio de transporte lima, movilidad lima |
| Traslado Aeropuerto | traslado aeropuerto lima | van aeropuerto lima, transporte aeropuerto jorge chávez |
| Corporativo | transporte corporativo lima | movilidad empresarial lima |
| Turístico | transporte turístico lima | tour privado lima, city tour lima privado |
| Grupos | transporte grupos lima | van privada grupos lima |
| FAQ | — | Long-tail informacional |

### Configuración técnica (Rank Math)

- Título y meta description únicos por página
- Schema markup: `LocalBusiness` + `TransportService`
- Open Graph para redes sociales
- Sitemap XML generado y enviado a Search Console
- Breadcrumbs en subpáginas de servicios
- Alt text en todas las imágenes

---

## 10. Stack Tecnológico

| Capa | Herramienta |
|------|-------------|
| CMS | WordPress |
| Page Builder | Elementor Pro |
| SEO | Rank Math |
| Formularios | Fluent Forms |
| Multiidioma | WPML o Polylang |
| WhatsApp widget | WP Social Chat (o similar) |
| Analytics | Google Analytics 4 (vía GTM) |
| Tag Manager | Google Tag Manager |
| CDN / Seguridad | Cloudflare (plan gratuito) |
| Caché / Performance | LiteSpeed Cache o WP Rocket |
| Hosting | Pendiente confirmar con cliente |

---

## 11. Integraciones

| Integración | Estado | Requiere acción del cliente |
|-------------|--------|-----------------------------|
| Google Analytics 4 | Pendiente | Sí — crear cuenta o dar acceso |
| Google Search Console | Pendiente | Sí — verificar dominio |
| Google Business Profile | Pendiente confirmar si existe | Sí |
| Google Tag Manager | Pendiente | Sí — crear contenedor |
| WhatsApp Business | Confirmar número activo | Confirmar +51 941 747 096 |
| Meta Pixel | Fuera de alcance fase 1 | — |

---

## 12. Contenido Requerido del Cliente

El cliente debe proveer los siguientes materiales **antes del inicio del diseño**:

| Material | Estado | Prioridad |
|----------|--------|-----------|
| Logo en alta resolución (PNG / SVG) | Disponible | Alta |
| Fotografías reales del Hyundai H350 (exterior e interior) | Disponible | Alta |
| Textos por servicio (o validación de los redactados por la agencia) | Pendiente | Alta |
| Dirección física o zona de operación en Lima | Pendiente | Media |
| Precios o rango de tarifas (opcional, para FAQ) | Pendiente | Media |
| Testimonios de clientes | Pendiente | Media |
| Destinos turísticos frecuentes | Pendiente | Media |
| Videos del vehículo o del servicio | Pendiente | Baja |
| Manual de marca o tipografía definida | Pendiente | Baja |

---

## 13. KPIs y Criterios de Éxito

### KPIs de conversión

| KPI | Meta mes 1 | Meta mes 3 |
|-----|-----------|-----------|
| Clics al botón WhatsApp | ≥ 20 | ≥ 60 |
| Envíos de formulario de contacto | ≥ 5 | ≥ 20 |
| Tasa de conversión visitas → contacto | ≥ 3% | ≥ 5% |

### KPIs de SEO

| KPI | Meta mes 3 |
|-----|-----------|
| Keywords en top 10 de Google | ≥ 2 |
| Tráfico orgánico mensual | ≥ 200 sesiones |
| Core Web Vitals — LCP | < 2.5s |

### Criterios de éxito del proyecto

El proyecto se considera exitoso si:

1. El sitio genera al menos 1 contacto real por WhatsApp durante los primeros 7 días post-lanzamiento
2. El sitio posiciona en Google para al menos 2 keywords objetivo en los primeros 90 días
3. El diseño es percibido como profesional y confiable por el cliente y su equipo
4. El sitio es 100% funcional en móvil (iOS y Android)
5. Google PageSpeed Score > 70 en móvil

---

## 14. Restricciones y Dependencias

| Item | Detalle |
|------|---------|
| Tecnología obligatoria | WordPress + Elementor Pro + Rank Math |
| Tecnología excluida | Ecommerce, reservas automáticas, área privada, pasarela de pago |
| Idiomas | Español (principal) + Inglés (secundario) |
| País objetivo | Lima, Perú |
| Dominio | mayhilexpress.com |
| Hosting | Pendiente confirmar |
| Presupuesto | Pendiente |
| Fecha de entrega | Pendiente |

---

## 15. Entregables

| Entregable | Fase |
|-----------|------|
| Sitio web corporativo — 9 páginas en español | 1 |
| Versión en inglés — 9 páginas | 1 |
| Widget WhatsApp flotante configurado | 1 |
| Formulario de contacto funcional | 1 |
| SEO on-page con Rank Math | 1 |
| Sitemap XML enviado a Search Console | 1 |
| Google Analytics 4 + GTM instalados | 1 |
| Sitio responsive y mobile-first | 1 |
| Blog con posts iniciales | 2 — opcional |
| Landing page para Ads | 2 — opcional |

---

## 16. Tiempo Estimado

| Fase | Actividad | Días hábiles |
|------|-----------|--------------|
| 1 | Setup WordPress + Elementor + plugins base | 1 |
| 2 | Diseño: Home + Nosotros + Contacto | 3 |
| 3 | Diseño: 4 subpáginas de servicio + FAQ | 3 |
| 4 | Multiidioma — versión EN | 2 |
| 5 | SEO on-page + schema + sitemap | 1 |
| 6 | Integraciones: GA4, GTM, WhatsApp, Search Console | 1 |
| 7 | QA · Responsive · Velocidad · Cross-browser | 1 |
| 8 | Correcciones y entrega final | 1 |
| **Total** | | **~13 días hábiles** |

---

## 17. Riesgos

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Cliente no entrega materiales a tiempo | Alta | Alto | Solicitar todos los materiales antes de iniciar diseño |
| Textos incompletos o sin validar | Media | Medio | Redactar desde la agencia y pedir validación por escrito |
| Sin testimonios en el lanzamiento | Alta | Medio | Lanzar sin ellos; añadir en fase 2 |
| Problemas de dominio o hosting | Baja | Alto | Confirmar accesos y credenciales antes de comenzar |
| Cambios fuera del alcance | Media | Medio | Documentar scope y gestionar como cambio formal |
| SEO con resultados lentos | Alta | Bajo | Alinear expectativas: SEO orgánico tarda 3–6 meses |

---

## 18. Próximos Pasos

1. Validar este PRD con el cliente y obtener aprobación formal
2. Recopilar materiales pendientes (textos, dirección, hosting, precios)
3. Confirmar acceso al dominio mayhilexpress.com
4. Crear o dar acceso a cuentas Google (Analytics, Search Console, GTM)
5. Iniciar setup de WordPress y primer borrador de Home

---

*Documento generado por IA-WEB-STUDIO-OS · Proyecto: Mayhil Express · 2026-06-17*
