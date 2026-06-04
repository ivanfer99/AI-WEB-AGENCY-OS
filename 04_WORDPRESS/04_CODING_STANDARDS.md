# Coding Standards

## Objetivo

Definir los estándares oficiales de programación de la agencia para WordPress, WooCommerce y desarrollos personalizados.

Todo código generado por:

* ChatGPT
* Claude Code
* Codex
* Gemini
* Desarrolladores

debe seguir estas reglas.

---

# Filosofía

Prioridades:

1. Legibilidad
2. Mantenibilidad
3. Seguridad
4. Rendimiento
5. Escalabilidad

---

# Principio Fundamental

El código será leído más veces de las que será escrito.

Escribir para humanos.

No para máquinas.

---

# PHP

## Versión

PHP 8.2+

---

## Reglas

### Activar Tipado Estricto

```php
declare(strict_types=1);
```

---

### Tipar Parámetros

Correcto:

```php
function get_product(int $id): array
{
    return [];
}
```

Incorrecto:

```php
function get_product($id)
{
}
```

---

### Return Types Obligatorios

Siempre declarar retorno.

---

### Una Responsabilidad

Una función = una tarea.

---

### Evitar Funciones Gigantes

Máximo recomendado:

50 líneas.

---

### Early Return

Preferir:

```php
if (!$user) {
    return;
}
```

---

# WordPress

## Prefijos

Todo debe llevar prefijo.

Ejemplo:

```php
cbp_get_booking()
cbp_create_order()
cbp_render_timer()
```

---

## Namespaces

Obligatorio para plugins propios.

Ejemplo:

```php
namespace Codebreak\Booking;
```

---

## Hooks

Separar:

* Actions
* Filters

---

## No usar código inline

Evitar:

```php
add_action('init', function(){});
```

Preferir clases.

---

# Arquitectura de Plugins

## Estructura Oficial

```text
plugin-name/

plugin-name.php

src/

Admin/
Frontend/
Api/
Services/
Helpers/

assets/

css/
js/

languages/

templates/
```

---

# Clases

## Regla

Una clase por archivo.

---

## Nombres

Correcto:

```php
BookingService
OrderRepository
LeadController
```

---

# Base de Datos

## Regla

No hacer consultas repetidas.

---

## Preparadas

Siempre:

```php
$wpdb->prepare()
```

---

# Seguridad

## Escapar Salidas

```php
esc_html()
esc_attr()
esc_url()
```

---

## Sanitizar Entradas

```php
sanitize_text_field()
sanitize_email()
sanitize_key()
```

---

## Nonces

Obligatorio en formularios.

---

## Capacidades

Validar permisos siempre.

---

# CSS

## Metodología

BEM Simplificado

---

## Ejemplo

```css
.card {}
.card__title {}
.card__button {}
```

---

## No usar IDs

Evitar:

```css
#header
```

Preferir clases.

---

# JavaScript

## Versión

ES6+

---

## Preferir

```javascript
const
let
```

---

## Evitar

```javascript
var
```

---

## Funciones Cortas

Una responsabilidad.

---

# AJAX

## WordPress

Preferir:

* REST API
* wp_ajax

---

# Elementor

## Reglas

No modificar Elementor Core.

---

## Widgets

Usar widgets personalizados cuando exista reutilización.

---

## CSS

Centralizar estilos.

No abusar de CSS personalizado por página.

---

# WooCommerce

## Reglas

No modificar core.

---

## Hooks

Utilizar:

```php
woocommerce_before_checkout_form
woocommerce_after_single_product
```

---

# Git

## Branches

main

develop

feature/nombre-funcionalidad

hotfix/error

---

## Commits

Formato:

```text
feat:
fix:
docs:
refactor:
perf:
```

---

# Documentación

Toda funcionalidad importante debe incluir:

* Objetivo
* Dependencias
* Ejemplos

---

# IA Coding Rules

Cuando ChatGPT, Claude Code o Codex generen código:

## Deben entregar

### Análisis

### Arquitectura

### Código

### Riesgos

### Próximos pasos

---

## Nunca generar

* Código inseguro
* Credenciales hardcodeadas
* SQL sin preparar
* Código sin comentarios críticos

---

# Checklist Final

Antes de aprobar código:

* [ ] Seguridad
* [ ] Performance
* [ ] Compatibilidad WordPress
* [ ] Compatibilidad WooCommerce
* [ ] Compatibilidad Elementor
* [ ] Responsive
* [ ] Documentado
* [ ] Versionado
