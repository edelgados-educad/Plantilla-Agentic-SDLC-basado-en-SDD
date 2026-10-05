# Deployment Architecture

Status: Draft · Owner: [OWNER]

**Covers:** qué se despliega y la topología conceptual por entorno.
**Delegates:** cómo se despliega, procedimiento y verificación a [07-operations/deployment.md](../07-operations/deployment.md).

Arquitectura conceptual, sin imponer tecnologías; las elecciones concretas se registran mediante ADR. Acceso y política de datos por entorno: [environments.md](../07-operations/environments.md).

| Environment | Purpose | Topology |
|---|---|---|
| DEV | Desarrollo e integración temprana | |
| QA | Verificación funcional | |
| STAGING | Validación previa, equivalente a PRODUCTION | |
| PRODUCTION | Operación real | |

## Deployable Units

| Unit | Container | Environments | Notes |
|---|---|---|---|

## Topology Notes

Redundancia, regiones, segmentación de red y dependencias de infraestructura por entorno. La definición ejecutable vive en `infra/`.
