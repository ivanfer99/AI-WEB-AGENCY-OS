# Deployment Workflow

## Objetivo

Definir el flujo oficial de desarrollo, pruebas y despliegue utilizado por la agencia.

Todo proyecto WordPress debe seguir este proceso.

---

# Filosofía

Nunca trabajar directamente en producción.

Todo cambio debe:

1. Versionarse
2. Revisarse
3. Probarse
4. Aprobarse
5. Publicarse

---

# Herramientas Oficiales

## Desarrollo

* Visual Studio Code
* Git
* GitHub
* Claude Code
* ChatGPT
* Codex

---

## Infraestructura

* Cloudflare
* Hosting
* VPS
* SiteGround
* Cloudways

---

# Arquitectura

```text
Local
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
```

---

# Entornos

## Local

Objetivo:

Desarrollo.

Permitido:

* PHP
* Elementor
* Plugins
* CSS
* JS

---

## Staging

Objetivo:

Validación.

Debe ser una copia realista del sitio.

---

## Producción

Objetivo:

Sitio activo.

Nunca desarrollar aquí.

---

# Git Workflow

## Main

Producción.

---

## Develop

Pruebas.

---

## Feature

Nuevas funcionalidades.

Ejemplos:

feature/booking-system

feature/seo-module

feature/checkout-optimization

---

## Hotfix

Correcciones urgentes.

Ejemplo:

hotfix/payment-error

---

# Flujo de Trabajo

## Paso 1

Crear rama feature.

---

## Paso 2

Desarrollar.

---

## Paso 3

Commit.

Formato:

feat:
fix:
docs:
refactor:
perf:

---

## Paso 4

Push a GitHub.

---

## Paso 5

Pull Request.

---

## Paso 6

Deploy a Staging.

---

## Paso 7

QA.

---

## Paso 8

Merge a Main.

---

## Paso 9

Deploy Producción.

---

# Checklist Pre Deploy

* [ ] Código revisado
* [ ] Sin errores PHP
* [ ] QA aprobado
* [ ] Backup realizado
* [ ] Cliente aprobado

---

# Checklist Post Deploy

* [ ] Home funciona
* [ ] Formularios funcionan
* [ ] WhatsApp funciona
* [ ] Analytics funciona
* [ ] SEO correcto
* [ ] WooCommerce correcto

---

# Rollback

Todo despliegue debe tener:

* Backup archivos
* Backup BD
* Plan de reversión

---

# Claude Code Workflow

## Permitido

* Crear código
* Refactorizar
* Documentar

---

## No permitido

* Deploy directo a producción
* Modificar credenciales
* Saltar QA

---

# Codex Workflow

## Permitido

* Plugins
* PHP
* CSS
* JS
* Automatizaciones

---

# Seguridad

Nunca almacenar:

* Contraseñas
* Tokens
* API Keys

en repositorios públicos.

---

# Versionado

## Releases

v1.0.0

v1.1.0

v1.2.0

v2.0.0

---

# Entregables

Todo proyecto debe incluir:

* Repositorio Git
* README
* Deployment Notes
* Backup Plan
* Rollback Plan

```
```
