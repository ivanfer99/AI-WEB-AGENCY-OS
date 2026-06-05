# IA-WEB-AGENCY-OS Enterprise

```mermaid
flowchart TD

CLIENTE[Cliente]

CLIENTE --> BRIEF

BRIEF[Brief]

BRIEF --> PRD

PRD --> SITEMAP

SITEMAP --> SEO

SEO --> WIREFRAMES

WIREFRAMES --> COPY

COPY --> DEV

DEV --> QA

QA --> PROD

PROD --> MANT

MANT --> CRO

CRO --> SEO

subgraph AGENTES_IA

JP[Jefe Proyecto]

EN[Estratega Negocio]

ARQ[Arquitecto Web]

UX[UX UI]

COPYIA[Copywriter]

SEOIA[SEO]

ADSIA[Ads]

WP[WP Developer]

WOO[Woo Developer]

QAIA[QA]

DEVOPS[DevOps]

CROIA[CRO]

AUTO[Automation]

end

JP --> BRIEF

EN --> PRD

ARQ --> SITEMAP

SEOIA --> SEO

UX --> WIREFRAMES

COPYIA --> COPY

WP --> DEV

WOO --> DEV

QAIA --> QA

DEVOPS --> PROD

CROIA --> CRO

AUTO --> MANT

subgraph TECNOLOGIA

VSCODE[VS Code]

CLAUDE[Claude Code]

CODEX[Codex]

GITHUB[GitHub]

ELEMENTOR[Elementor]

JETENGINE[JetEngine]

WOOCOMMERCE[WooCommerce]

end

VSCODE --> CLAUDE

VSCODE --> CODEX

CLAUDE --> GITHUB

CODEX --> GITHUB

GITHUB --> DEV

ELEMENTOR --> DEV

JETENGINE --> DEV

WOOCOMMERCE --> DEV