# [WORK_ID] — [FEATURE_NAME]

Reemplazar texto guía y placeholders; no eliminar encabezados (lo que no aplique se marca `N/A` con motivo). Perfil `LITE`: ver [LITE Minimum Spec](../../00-governance/work-types.md#lite-minimum-spec). `Status` admite `Draft`, `Clarification`, `Approved`, `Implementing`, `Validating`, `Done`, `Deprecated`; `Approved` exige registrar debajo `Approved by: [APPROVER]` y `Date: [DATE]`.

## Work Type
`FEATURE` o `CHANGE` ([work-types.md](../../00-governance/work-types.md#work-types)).

## Status
Draft

## Owner
[OWNER]

## Approver
[APPROVER]

## Created
[DATE]

## Last Updated
[DATE]

## Context
Situación actual y motivo de la feature. Enlazar [product-spec.md](../../02-product/product-spec.md) en lugar de copiarlo.

## Problem
Describe el problema que la feature resuelve y a quién afecta.

## Objective
Resultado verificable esperado.

## Scope
### In Scope
Comportamientos incluidos.
### Out of Scope
Exclusiones explícitas.

## Actors
Usuarios, roles o sistemas que interactúan con la feature.

## Preconditions
Condiciones que deben cumplirse antes del flujo principal.

## Functional Requirements
| ID | Requirement | Source |
|---|---|---|
| FR-001 | El sistema debe [DESCRIPTION]. | |

Cada FR es verificable. Evitar términos sin criterio medible: "rápido", "fácil", "adecuado", "intuitivo", "etc.", "según corresponda", "cuando sea necesario".

## Business Rules
| ID | Rule | Source |
|---|---|---|
| BR-001 | [DESCRIPTION] | |

Solo reglas propias de la feature. Las globales se enlazan desde [business-rules.md](../../02-product/business-rules.md), no se copian.

## User Flow
1. Paso observable del actor o respuesta del sistema.

## Alternative Flows
| Flow | Trigger | Expected Behavior | Related FR |
|---|---|---|---|

## Error Scenarios
| Scenario | Expected Behavior | Related FR |
|---|---|---|

## Edge Cases
Resumen breve; detalle en [edge-cases.md](edge-cases.md).

## Dependencies
Specs, sistemas, datos o decisiones de los que depende la feature.

## Contracts
Interfaces creadas o modificadas, o `Ninguno`. Detalle en [contracts/](contracts/README.md).

## Security Considerations
Autenticación, autorización, validación de entradas y amenazas relevantes. Diseño de referencia: [security.md](../../04-architecture/security.md).

## Privacy Considerations
Datos personales tratados, finalidad, retención y restricciones de logging.

## Observability Requirements
Logs, métricas, trazas y alertas que demuestran que la feature funciona.

## Non-functional Requirements
NFR globales aplicables ([non-functional-requirements.md](../../02-product/non-functional-requirements.md)) y umbrales propios de la feature.

## Acceptance Criteria
Resumen breve; detalle en [acceptance-criteria.md](acceptance-criteria.md).

## Open Questions
| ID | Question | Criticality | Status |
|---|---|---|---|
| Q-001 | | Critical | Open |

`Criticality`: `Critical` o `Normal`. `Status`: `Open` o `Answered`. La spec no pasa a `Approved` con preguntas `Critical` en `Open`.

## Clarifications Log
| Question | Answer | Answered By | Date | Spec Changes |
|---|---|---|---|---|

## Change History
| Change ID | Date | Summary | Approved By |
|---|---|---|---|

## References
ADR, journeys, documentos de discovery y fuentes externas relacionadas.
