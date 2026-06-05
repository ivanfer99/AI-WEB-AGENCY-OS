# WordPress + GitHub

```mermaid
flowchart TD

A[VS Code]

A --> B[Claude Code]

A --> C[Codex]

B --> D[Git]

C --> D

D --> E[GitHub]

E --> F[Pull Request]

F --> G[Staging]

G --> H[QA]

H --> I[Producción]