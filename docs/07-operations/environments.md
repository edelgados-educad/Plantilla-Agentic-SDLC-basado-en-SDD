# Environments

Status: Draft · Owner: [OWNER]

Acceso, datos y promoción por entorno. Propósito y topología conceptual en [04-architecture/deployment.md](../04-architecture/deployment.md).

| Environment | Access | Data Policy | Deployment Trigger | Owner |
|---|---|---|---|---|
| DEV | | Datos sintéticos | | |
| QA | | Sintéticos o anonimizados | | |
| STAGING | | Anonimizados | | |
| PRODUCTION | Restringido | Datos reales | Aprobación humana | |

## Configuration

Cómo se gestiona la configuración por entorno. Los secretos se obtienen de un gestor de secretos; nunca se documentan aquí ni se versionan.

## Promotion Rules

Condiciones para promover un artefacto al siguiente entorno (DEV → QA → STAGING → PRODUCTION).

## Access Management

Quién accede a cada entorno, cómo se solicita y con qué frecuencia se revisa.
