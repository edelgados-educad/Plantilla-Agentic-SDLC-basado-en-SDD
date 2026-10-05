# [WORK_ID] — Change Record

Para `BUG`, `HOTFIX`, `REFACTOR`, `TECH_DEBT` y `DOCUMENTATION`. Referencia canónica: `docs/00-governance/work-types.md`.

## Work Item
| Field | Value |
|---|---|
| ID | [WORK_ID] |
| Title | [WORK_TITLE] |
| Project Profile | [PROJECT_PROFILE] |
| Owner | [OWNER] |
| Created | [DATE] |

## Work Type
[WORK_TYPE]

`HOTFIX`: registrar `Emergency approved by: [APPROVER]` y `Date: [DATE]` antes de cualquier cambio.

## Summary
Qué cambia, en una o dos frases.

## Motivation
Defecto, incidente, deuda o necesidad que origina el cambio.

## Affected FR/AC
FR/AC existentes afectados en forma completa (p. ej., `FEAT-001/FR-002`), o `Ninguno` si no hay impacto funcional.

| FR/AC | Impact | Verifying Test |
|---|---|---|

## Lifecycle Applicability
Completar solo si el trabajo no tiene `plan.md`. Mismas reglas que la tabla de `plan.md`.

| Stage | Applicability | Triggers Evaluated | Reason | Approved By |
|---|---|---|---|---|
| ASSESS | | — | | |
| CONSTITUTION | | — | | |
| DISCOVERY | | — | | |
| PRODUCT SPEC | | — | | |
| FEATURE SPEC | | — | | |
| CLARIFY | | — | | |
| ARCHITECTURE | | Architecture 1–5 | | |
| CONTRACTS | | Contracts 1–3 | | |
| IMPLEMENTATION PLAN | | — | | |
| TASK DAG | | — | | |
| AGENT EXECUTION | | — | | |
| FEEDBACK SENSORS | | — | | |
| REVIEW | | — | | |
| REVIEW: Security | | Security Review 1–8 | | |
| CONVERGENCE | | — | | |
| RELEASE | | — | | |
| OBSERVABILITY | | — | | |
| LEARNING | | — | | |
| HARNESS IMPROVEMENT | | — | | |

## Changes
Archivos, componentes o documentos modificados.

## Risk
Riesgos del cambio y mitigación.

## Rollback
Cómo revertir y en qué condiciones.

## Verification
Test que verifica la corrección o la preservación del comportamiento, y evidencia de sensores.

| Sensor / Test | Result (Pass/Fail) | Date | Evidence |
|---|---|---|---|

## Related Incident
`INC-XXX` con enlace, o `—`. En `HOTFIX` es obligatorio y se completa la post-incident completion del Emergency Change Procedure.
