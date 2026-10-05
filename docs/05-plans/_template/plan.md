# [WORK_ID] — Plan

Se crea en CLASSIFY con `Work Item`, `Work Type` y `Lifecycle Applicability`; el resto se completa en IMPLEMENTATION PLAN. Referencias canónicas: `docs/00-governance/work-types.md` (applicability y triggers) y `docs/00-governance/quality-gates.md` (Plan Gate). Rutas escritas desde la raíz del repositorio para que sigan siendo válidas al copiar la plantilla.

## Work Item
| Field | Value |
|---|---|
| ID | [WORK_ID] |
| Title | [WORK_TITLE] |
| Project Profile | [PROJECT_PROFILE] |
| Spec | `docs/03-specs/[WORK_ID]-[SLUG]/spec.md` o `—` |
| Owner | [OWNER] |
| Created | [DATE] |

## Work Type
[WORK_TYPE]

## Objective
Resultado verificable del trabajo, vinculado a FR/AC o a la motivación técnica.

## Lifecycle Applicability
Valores: `REQUIRED`, `CONDITIONAL`, `N/A`. IDEA y CLASSIFY se cumplen al crear este archivo. Todo `N/A` indica los triggers evaluados y el motivo. `Approved By` solo se completa al marcar `N/A` una etapa con triggers activos (o Security Review / Architecture en perfil `CRITICAL`).

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

## Components Affected
Componentes y contenedores afectados según `docs/04-architecture/components.md`.

## Approach
Estrategia de implementación y alternativas descartadas. Decisiones relevantes en `decisions.md`; las arquitectónicas, en ADR.

## Data Changes
Cambios al modelo de datos, o `Ninguno`.

## Contract Changes
Contratos creados o modificados y su compatibilidad, o `Ninguno`.

## Migrations
Migraciones de datos o configuración, orden de ejecución y reversibilidad, o `Ninguna`.

## Security Impact
Resultado de evaluar los Security Review triggers y controles requeridos.

## Observability Impact
Logs, métricas, trazas y alertas nuevas o modificadas.

## Testing Strategy
Tipos de prueba y evals por AC, según `docs/06-quality/test-strategy.md`.

## Deployment Impact
Entornos afectados, activación progresiva, ventanas y dependencias de despliegue.

## Rollback Strategy
Cómo revertir y en qué condiciones, según `docs/07-operations/rollback.md`.

## Risks
Resumen; detalle en `risks.md` (`[WORK_ID]/R001`).

## Assumptions
Supuestos propios del trabajo; los globales viven en `docs/01-discovery/assumptions.md`.
