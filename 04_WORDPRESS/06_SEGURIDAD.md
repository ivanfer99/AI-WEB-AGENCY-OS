# Seguridad WordPress

## Objetivo

Definir el estándar de seguridad oficial para todos los proyectos de la agencia.

---

# Filosofía

Prioridades:

1. Prevención
2. Detección
3. Recuperación

---

# Regla Principal

Nunca confiar en:

* Usuarios
* Formularios
* Plugins externos
* APIs externas

Validar siempre.

---

# Infraestructura

## Cloudflare

Obligatorio.

Configuraciones mínimas:

* SSL Full Strict
* Bot Protection
* Rate Limiting
* WAF

---

## Hosting

Requisitos:

* PHP actualizado
* Backups automáticos
* SSL
* Firewall

---

# WordPress

## Usuario Admin

Evitar:

admin

---

## Roles

Aplicar principio de mínimo privilegio.

---

## Contraseñas

Obligatorio:

* 12+ caracteres
* Gestor de contraseñas

---

## MFA

Recomendado para:

* Administradores
* Clientes

---

# Plugins

## Regla

Solo plugins aprobados.

---

## Prohibido

* Plugins nulled
* Plugins abandonados

---

## Auditoría

Revisar:

* Última actualización
* Compatibilidad
* Vulnerabilidades

---

# Formularios

## Obligatorio

* Honeypot
* Validación
* Sanitización

---

## Opcional

* reCAPTCHA
* Cloudflare Turnstile

---

# PHP

## Sanitización

Siempre:

sanitize_text_field()
sanitize_email()
sanitize_key()

---

## Escape

Siempre:

esc_html()
esc_attr()
esc_url()

---

## Nonces

Obligatorios.

---

# Base de Datos

## Consultas

Siempre:

$wpdb->prepare()

---

## Prohibido

SQL dinámico sin preparar.

---

# APIs

## Tokens

Nunca hardcodear.

---

## Almacenamiento

Usar:

wp-config.php

Variables entorno

---

# Archivos

## Permisos

Archivos:

644

Directorios:

755

---

# wp-config.php

Proteger.

---

# XML-RPC

Deshabilitar salvo necesidad específica.

---

# REST API

Restringir endpoints sensibles.

---

# WooCommerce

## Checkout

Validar:

* Pagos
* Cupones
* Formularios

---

## Correos

Verificar SPF

Verificar DKIM

Verificar DMARC

---

# Backups

## Obligatorio

Diarios

---

## Retención

30 días mínimo

---

## Restauración

Probar trimestralmente

---

# Monitoreo

## Uptime

Obligatorio

---

## Logs

Revisar errores críticos

---

# Incidentes

## Prioridad Crítica

Sitio caído

Hackeo

Pago comprometido

---

## Prioridad Alta

Formulario roto

Checkout roto

---

# Checklist Seguridad

* [ ] SSL activo
* [ ] Cloudflare activo
* [ ] Backups activos
* [ ] Plugins auditados
* [ ] Usuarios revisados
* [ ] MFA habilitado
* [ ] Formularios protegidos
* [ ] WooCommerce revisado
* [ ] APIs protegidas
* [ ] Logs revisados

---

# Stack Oficial Seguridad

* Cloudflare
* Wordfence
* Solid Security
* UpdraftPlus
* FluentSMTP

```
```
