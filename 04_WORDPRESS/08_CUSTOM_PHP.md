# Desarrollo PHP Personalizado

## Objetivo

Definir cuándo y cómo desarrollar funcionalidades personalizadas en PHP dentro del ecosistema WordPress.

---

# Filosofía

Antes de instalar un plugin preguntar:

1. ¿Elementor lo resuelve?
2. ¿JetEngine lo resuelve?
3. ¿WooCommerce lo resuelve?
4. ¿Podemos hacerlo con PHP?

---

# Regla Principal

Prioridad:

Elementor
↓
JetEngine
↓
WooCommerce
↓
PHP Propio
↓
Plugin Externo

---

# Casos Ideales para PHP

## Integraciones

- APIs
- CRM
- ERP
- MQTT
- Sistemas externos

---

## WooCommerce

- Checkout personalizado
- Reglas de negocio
- Cupones avanzados
- Automatizaciones

---

## SEO

- Schema personalizado
- Meta dinámicos
- Sitemaps especiales

---

## Formularios

- Validaciones
- Procesamiento
- Automatizaciones

---

# Ubicación del Código

## Nunca

functions.php gigante

---

## Permitido

Plugin propio

MU Plugin

---

# Arquitectura Recomendada

plugin-name/

src/

Admin/
Frontend/
Services/
Api/
Helpers/

---

# Naming Convention

Prefijo oficial:

cbp_

Ejemplos:

cbp_get_booking()

cbp_send_lead()

cbp_calculate_discount()

---

# Seguridad

Obligatorio:

- Sanitizar
- Escapar
- Validar permisos
- Nonces

---

# Base de Datos

Siempre:

$wpdb->prepare()

Nunca:

SQL directo

---

# APIs

Usar:

WP REST API

---

# Logs

Toda integración importante debe registrar:

- Errores
- Excepciones
- Eventos críticos

---

# Documentación

Toda función importante debe incluir:

- Objetivo
- Parámetros
- Retorno
- Ejemplo

---

# Checklist

- [ ] Tipado estricto
- [ ] Return types
- [ ] Seguridad
- [ ] Performance
- [ ] Documentación
- [ ] Compatible Elementor
- [ ] Compatible WooCommerce