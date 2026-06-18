# Decisiones Arquitectónicas

## Objetivo

Registrar las decisiones técnicas principales del sistema IA-WEB-STUDIO-OS para mantener coherencia, evitar cambios impulsivos y facilitar el uso futuro del sistema.

Este documento responde:

- Qué usamos
- Por qué lo usamos
- Qué alternativas descartamos
- Cuándo revisar la decisión

---

# Principios Generales

## 1. Priorizar construcción sobre venta

Este sistema no está diseñado para gestionar ventas, propuestas comerciales o contratos.

Está diseñado para:

- Diseñar proyectos web
- Crear arquitectura
- Generar wireframes
- Construir en WordPress
- Implementar SEO técnico
- Crear ecommerce WooCommerce
- Usar IA para acelerar producción

---

## 2. Mantener el sistema simple

No agregar carpetas o documentos si no ayudan directamente a construir mejores proyectos web.

Evitar:

- Documentación innecesaria
- Procesos comerciales excesivos
- Carpetas que no se usarán
- Duplicación de información

---

## 3. Usar IA como equipo técnico

La IA debe actuar como:

- Jefe de proyecto técnico
- Arquitecto web
- UX/UI
- SEO técnico
- WordPress Developer
- WooCommerce Developer
- QA
- DevOps

No como reemplazo del criterio humano.

---

# Decisión 01 — WordPress como CMS principal

## Decisión

Usar WordPress como CMS principal.

## Motivo

WordPress permite crear sitios web, landings, ecommerce, blogs, reservas y catálogos de manera rápida y flexible.

## Alternativas consideradas

- Webflow
- Shopify
- Laravel
- Next.js
- Wix
- Squarespace

## Justificación

WordPress es ideal para el tipo de proyectos que se construirán:

- Webs corporativas
- Landings
- Ecommerce
- SEO local
- Reservas
- Catálogos
- Blogs
- Sitios administrables por clientes

## Estado

Aceptado.

---

# Decisión 02 — Elementor Pro como constructor visual

## Decisión

Usar Elementor Pro como constructor visual oficial.

## Motivo

Permite construir interfaces profesionales de forma rápida, visual y reutilizable.

## Alternativas consideradas

- Gutenberg
- Bricks
- Oxygen
- Divi
- WPBakery

## Justificación

Elementor Pro es compatible con el flujo de trabajo del usuario y permite construir proyectos visuales sin depender completamente de código.

## Regla

Elementor se usa para diseño visual.

PHP se usa para lógica personalizada.

## Estado

Aceptado.

---

# Decisión 03 — Crocoblock / JetEngine como sistema dinámico

## Decisión

Usar Crocoblock / JetEngine como herramienta oficial para contenido dinámico avanzado.

## Motivo

El usuario cuenta con Crocoblock completo y JetEngine permite construir estructuras avanzadas sin crear todo desde cero en PHP.

## Usos permitidos

- Custom Post Types
- Campos personalizados
- Listings
- Filtros
- Directorios
- Catálogos
- Reservas
- Dashboards
- WooCommerce avanzado

## Alternativas consideradas

- ACF
- Meta Box
- Pods
- CPT UI

## Justificación

JetEngine se integra muy bien con Elementor y reduce tiempo de desarrollo en proyectos dinámicos.

## Estado

Aceptado.

---

# Decisión 04 — WooCommerce para ecommerce

## Decisión

Usar WooCommerce como sistema ecommerce oficial.

## Motivo

WooCommerce permite crear tiendas online flexibles dentro de WordPress.

## Usos

- Productos físicos
- Productos digitales
- Catálogos
- Cupones
- Checkout
- Pasarelas de pago
- Integraciones
- Reservas si corresponde

## Alternativas consideradas

- Shopify
- Tiendanube
- Magento
- Prestashop

## Justificación

WooCommerce se integra con Elementor, JetWooBuilder, SEO y PHP personalizado.

## Estado

Aceptado.

---

# Decisión 05 — PHP personalizado mediante plugin propio

## Decisión

La lógica personalizada debe ir preferentemente en un plugin propio, no en `functions.php`.

## Motivo

Evitar sitios difíciles de mantener.

## Regla

No crear `functions.php` gigantes.

Usar:

- Plugin propio
- MU Plugin
- Codebreak Core Plugin

## Usos

- Shortcodes
- Hooks
- Integraciones
- Validaciones
- APIs
- Automatizaciones
- Reglas WooCommerce

## Estado

Aceptado.

---

# Decisión 06 — GitHub como control de versiones

## Decisión

Usar GitHub como repositorio principal.

## Motivo

Permite versionar documentación, código, estructura y decisiones.

## Regla

Todo cambio importante debe pasar por Git.

## Flujo recomendado

VS Code  
↓  
Git  
↓  
GitHub  
↓  
Staging  
↓  
QA  
↓  
Producción

## Estado

Aceptado.

---

# Decisión 07 — VS Code como centro de trabajo

## Decisión

Usar Visual Studio Code como entorno principal.

## Motivo

VS Code permite trabajar con:

- Markdown
- PHP
- CSS
- JavaScript
- Git
- GitHub
- Claude Code
- Codex
- Mermaid

## Estado

Aceptado.

---

# Decisión 08 — Claude Code y Codex como asistentes de desarrollo

## Decisión

Usar Claude Code y Codex como asistentes para desarrollo, refactorización y documentación técnica.

## Motivo

Permiten acelerar:

- Creación de plugins
- Código PHP
- Refactorización
- Documentación
- Revisión técnica
- Arquitectura

## Regla

La IA no debe publicar directo a producción.

Todo código generado debe revisarse.

## Estado

Aceptado.

---

# Decisión 09 — Rank Math como plugin SEO oficial

## Decisión

Usar Rank Math como plugin SEO principal.

## Motivo

Permite gestionar SEO on-page, schema, sitemaps y metadatos de forma eficiente.

## Alternativas consideradas

- Yoast SEO
- SEOPress
- All in One SEO

## Regla

No usar múltiples plugins SEO en un mismo proyecto.

## Estado

Aceptado.

---

# Decisión 10 — SEO técnico como parte del desarrollo

## Decisión

El SEO no se tratará como un servicio comercial dentro del sistema, sino como una capa técnica obligatoria del desarrollo web.

## Motivo

Todo sitio debe construirse correctamente desde el inicio.

## Incluye

- URLs limpias
- Titles
- Meta descriptions
- H1
- Schema
- Sitemap
- Robots
- Performance
- Mobile
- Search Console
- Core Web Vitals

## Estado

Aceptado.

---

# Decisión 11 — Ads limitado a tracking técnico

## Decisión

El sistema no se enfocará en gestión comercial de Ads.

## Motivo

Las ventas y campañas son responsabilidad del usuario.

## Se mantiene

- Tracking
- Conversiones
- GTM
- GA4
- Meta Pixel
- Landing Ads si aplica

## Se reduce o archiva

- Estrategias comerciales de Google Ads
- Estrategias comerciales de Meta Ads
- Remarketing avanzado
- Propuestas Ads

## Estado

Aceptado.

---

# Decisión 12 — Mermaid como lenguaje visual de arquitectura

## Decisión

Usar Mermaid para documentar flujos y arquitectura.

## Motivo

Permite visualizar procesos complejos de forma simple y versionable dentro de GitHub.

## Usos

- Flujo del cliente
- Arquitectura web
- SEO
- WooCommerce
- WordPress + GitHub
- Agentes IA
- Pipeline de proyecto

## Estado

Aceptado.

---

# Decisión 13 — Stitch / Figma para exploración visual

## Decisión

Usar Stitch o Figma como apoyo para generar propuestas visuales.

## Motivo

Permiten pasar de wireframes a una referencia visual antes de construir en Elementor.

## Regla

Stitch/Figma no reemplazan WordPress.

Solo ayudan a visualizar.

## Estado

Aceptado.

---

# Decisión 14 — Eliminar enfoque de agencia comercial

## Decisión

Eliminar o archivar módulos enfocados en ventas, servicios comerciales y propuestas.

## Motivo

El sistema debe estar enfocado en diseño, arquitectura, desarrollo y SEO técnico.

## Módulos a eliminar o archivar

- 12_CLIENTE_ACTIVO
- 13_SERVICIOS_AGENCIA
- 14_PROPUESTAS_COMERCIALES

## Estado

Aceptado.

---

# Decisión 15 — Mantener blueprints por tipo de proyecto

## Decisión

Mantener `11_TIPOS_DE_PROYECTO`.

## Motivo

Los blueprints ayudan a elegir la arquitectura correcta según el tipo de proyecto.

## Tipos

- Landing Page
- Web Corporativa
- Ecommerce
- SEO Local
- Generación de Leads
- Reservas Online
- Membresías
- Marketplace
- SaaS

## Estado

Aceptado.

---

# Decisión 16 — No sobre-documentar

## Decisión

No agregar más documentos salvo que sean necesarios para ejecutar proyectos reales.

## Motivo

El sistema debe ser usable, no solo extenso.

## Regla

Antes de crear un documento nuevo preguntar:

¿Esto me ayuda a construir mejor o más rápido?

Si la respuesta es no, no se crea.

## Estado

Aceptado.

---

# Estructura Final Recomendada

```text
00_SISTEMA
01_PROMPTS
03_PLANTILLAS
04_WORDPRESS
05_WOOCOMMERCE
06_SEO
07_ADS
08_WIREFRAMES
09_MERMAID
11_TIPOS_DE_PROYECTO