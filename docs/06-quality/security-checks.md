# Security Checks

Status: Draft · Owner: [OWNER]

**Covers:** checklist operacional de verificaciones de seguridad.
**Delegates:** diseño de seguridad a [security.md](../04-architecture/security.md); cuándo aplica Security Review a los [Applicability Triggers](../00-governance/work-types.md#applicability-triggers).

## Every Change

| Check | Automated | Tool/Command | Evidence |
|---|---|---|---|
| Sin secretos en código, configuración ni documentación | | | |
| Sin datos sensibles en logs | | | |
| Dependencias nuevas justificadas | | | |

## When Security Review Applies

| Check | Automated | Tool/Command | Evidence |
|---|---|---|---|
| Autenticación y autorización verificadas por rol y recurso | | | |
| Validación de entradas y consultas o comandos parametrizados | | | |
| Dependencias sin vulnerabilidades conocidas críticas o altas | | | |
| Manejo de secretos y cifrado según `security.md` | | | |
| Trust boundaries y superficie de ataque actualizados | | | |
| Datos personales: finalidad, minimización y retención | | | |
| Permisos de infraestructura y entornos con mínimo privilegio | | | |

## Before Release

| Check | Automated | Tool/Command | Evidence |
|---|---|---|---|
| Escaneo de seguridad sin hallazgos `BLOCKER` o `HIGH` abiertos | | | |
| Configuración de seguridad de PRODUCTION revisada | | | |

`Automated`: `Yes` o `No`. Los hallazgos se registran en `review.md` con su severidad.
