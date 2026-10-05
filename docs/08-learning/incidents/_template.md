# INC-XXX — [INCIDENT_TITLE]

Copiar como `INC-XXX-[SLUG].md`. Redacción sin culpables: describir hechos y sistemas, no personas.

## Incident ID
INC-XXX

## Summary
Qué pasó, en dos o tres frases.

## Severity
| Value | Meaning |
|---|---|
| `CRITICAL` | Servicio crítico caído, datos comprometidos o impacto regulatorio. Habilita el Emergency Change Procedure. |
| `HIGH` | Degradación severa de una funcionalidad principal. |
| `MEDIUM` | Funcionalidad no crítica afectada, con workaround. |
| `LOW` | Impacto menor o cosmético. |

## Impact
Usuarios, procesos, datos y duración afectados. Si hubo datos personales comprometidos, escalar según la normativa aplicable.

## Timeline
| Time | Event |
|---|---|

## Root Cause
Causa raíz técnica y de proceso (p. ej., cinco porqués).

## Detection
¿Qué sensor, alerta o persona lo detectó? ¿Por qué no se detectó antes?

## Resolution
Mitigación y corrección aplicadas, con sus work items (`HOT-XXX`, `BUG-XXX`).

## Harness Gap
Carencia del harness que permitió el incidente, según las categorías del [Feedback Flywheel](../README.md).

## Corrective Actions
| Action | Owner | Work Item |
|---|---|---|

## Preventive Actions
| Action | Owner | Work Item |
|---|---|---|

## Related Work Items
Work items relacionados con enlace a su carpeta en `docs/05-plans/`.
