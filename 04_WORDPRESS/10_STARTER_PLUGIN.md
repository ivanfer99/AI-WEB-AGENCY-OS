# Codebreak Core Plugin

## Nombre Oficial

Codebreak Core

Slug:

codebreak-core

---

# Objetivo

Centralizar toda la lógica personalizada desarrollada por la agencia.

Evitar:

- functions.php gigantes
- snippets dispersos
- plugins pequeños duplicados

---

# Filosofía

Todo desarrollo personalizado debe vivir aquí o derivarse de esta arquitectura.

---

# Casos de Uso

## WordPress

- Shortcodes
- Widgets
- CPT
- Meta Fields

---

## WooCommerce

- Checkout
- Cupones
- Reglas comerciales

---

## SEO

- Schema
- Metadatos
- Sitemaps

---

## Formularios

- Validaciones
- Integraciones

---

## APIs

- CRM
- WhatsApp
- ERP
- Home Assistant
- MQTT

---

# Arquitectura Oficial

codebreak-core/

codebreak-core.php

src/

Admin/
Api/
Services/
Repositories/
Integrations/
Helpers/
Modules/

assets/

css/
js/

languages/

templates/

logs/

tests/

---

# Bootstrap

El archivo principal solamente:

- carga clases
- registra hooks
- inicializa módulos

Nada más.

---

# Namespaces

Obligatorio.

Ejemplo:

namespace Codebreak\Core;

---

# Prefijos

cbp_

Ejemplos:

cbp_send_lead()

cbp_create_booking()

cbp_sync_order()

---

# Módulos

Cada funcionalidad importante debe ser independiente.

---

## Ejemplo

Modules/

SEO/

Bookings/

WooCommerce/

CRM/

MQTT/

Analytics/

---

# Integraciones

Cada integración externa tendrá su propia carpeta.

---

## Ejemplo

Integrations/

Hubspot/

Pipedrive/

WhatsApp/

HomeAssistant/

MQTT/

---

# Configuración

Nunca hardcodear:

- API Keys
- Passwords
- Tokens

---

# Logs

Toda integración crítica debe registrar:

- Errores
- Eventos
- Excepciones

---

# Testing

Toda funcionalidad importante debe incluir pruebas.

---

# Versionado

SemVer

v1.0.0

v1.1.0

v2.0.0

---

# IA Development Rules

Cuando ChatGPT
Claude Code
Codex

generen código para este plugin:

Deben respetar:

- Coding Standards
- Seguridad
- Namespaces
- Arquitectura Modular

---

# Checklist

Antes de aprobar un módulo:

- [ ] Namespace correcto
- [ ] Prefijos correctos
- [ ] Seguridad
- [ ] Logs
- [ ] Documentación
- [ ] Compatible WordPress
- [ ] Compatible Elementor
- [ ] Compatible WooCommerce

---

# Objetivo a Largo Plazo

Convertir Codebreak Core en la plataforma base utilizada por todos los proyectos desarrollados por la agencia.