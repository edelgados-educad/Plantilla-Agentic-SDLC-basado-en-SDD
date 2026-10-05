# Quality Gates

**Covers:** condiciones para avanzar entre etapas del lifecycle y la definición canónica de Convergence.
**Delegates:** condiciones para declarar un trabajo terminado a [definition-of-done.md](definition-of-done.md).

Los gates aplicables dependen del Project Profile, del Work Type y de la Lifecycle Applicability del plan ([work-types.md](work-types.md)). El gate de una etapa `N/A` no se evalúa; su justificación la verifica el Reviewer. La evidencia se referencia en los artefactos del trabajo, nunca solo en una conversación.

## Assessment Gate
### Entry Criteria
ASSESS ejecutado: [current-state.md](../01-discovery/current-state.md) y [constraints.md](../01-discovery/constraints.md) completos para el alcance del trabajo.
### Blocking Conditions
Se desconoce el estado actual (brownfield) o las restricciones principales (greenfield).
### Approver
Orchestrator; Human en `PROJECT` y en la adopción brownfield.
### Evidence
`current-state.md`, `constraints.md` y riesgos iniciales registrados.
## Governance Gate
### Entry Criteria
[constitution.md](constitution.md) revisada para el proyecto y Project Profile propuesto.
### Blocking Conditions
No existe Constitution, las reglas relevantes no son conocidas o hay excepciones no identificadas.
### Approver
Human.
### Evidence
Constitution vigente, tabla de Amendments actualizada y `Project Profile` declarado en el README.
## Discovery Gate
### Entry Criteria
Archivos de `docs/01-discovery/` completos según el Project Profile.
### Blocking Conditions
Problema ambiguo, objetivo ausente, scope inexistente o contradicciones críticas.
### Approver
Human (owner funcional definido en `stakeholders.md`).
### Evidence
`problem.md`, `objectives.md` y `scope.md` en `Status: Approved`; resto según perfil.
## Product Gate
### Entry Criteria
Discovery Gate aprobado y `docs/02-product/` completo.
### Blocking Conditions
Usuarios no definidos, comportamiento principal ambiguo, reglas globales críticas sin resolver o NFR críticos ausentes.
### Approver
Human (owner funcional).
### Evidence
`product-spec.md`, `business-rules.md` con fuente por regla y NFR con métrica, umbral y verificación.
## Spec Gate
### Entry Criteria
Spec con FR, AC, examples y edge cases; `Open Questions` críticas en `Answered`.
### Blocking Conditions
Reglas ambiguas, faltan AC, existen `Open Questions` críticas o no hay aprobación humana.
### Approver
Human (registra `Approved by:` y `Date:` en la spec).
### Evidence
`spec.md` en `Approved`, `acceptance-criteria.md` y `Clarifications Log` actualizado.
## Architecture Gate
### Entry Criteria
Spec aprobada y etapa ARCHITECTURE aplicable según la Lifecycle Applicability de `plan.md`.
### Blocking Conditions
Componentes o integraciones afectados desconocidos, riesgos arquitectónicos críticos pendientes o riesgos de seguridad no evaluados.
### Approver
Architect; Human si el cambio arquitectónico es relevante.
### Evidence
Documentos de `docs/04-architecture/` actualizados y ADR cuando aplica.
## Contract Gate
### Entry Criteria
Etapa CONTRACTS aplicable según la Lifecycle Applicability de `plan.md`.
### Blocking Conditions
Una interfaz requerida no está definida.
### Approver
Architect; Human para cambios incompatibles.
### Evidence
`contracts/` de la spec con versión y análisis de compatibilidad.
## Plan Gate
### Entry Criteria
`plan.md` completo y Lifecycle Applicability resuelta según [work-types.md](work-types.md#lifecycle-applicability).
### Blocking Conditions
No hay estrategia, riesgos evaluados, testing strategy, applicability justificada o rollback cuando aplica.
### Approver
Orchestrator + Architect; Human si hay `N/A` con triggers activos.
### Evidence
`plan.md` y `risks.md`.
## Implementation Gate
### Entry Criteria
Plan Gate aprobado; `tasks.md` y `dependencies.md` creados.
### Blocking Conditions
Falta spec aprobada (cuando aplica), arquitectura necesaria, plan, tasks o dependencies.
### Approver
Orchestrator.
### Evidence
Tasks con `Covers:` y `Verified by:`; DAG sin ciclos con `Parallel Groups`.
## Verification Gate
### Entry Criteria
Tareas en `REVIEW` y feedback sensors ejecutados.
### Blocking Conditions
Fallan feedback sensors bloqueantes ([feedback-sensors.md](../06-quality/feedback-sensors.md)).
### Approver
Tester.
### Evidence
Resultados de sensores en `progress.md` o `change-record.md`.
## Review Gate
### Entry Criteria
Verification Gate aprobado; Security Review ejecutado cuando aplica.
### Blocking Conditions
Hay `BLOCKER` o `HIGH` abiertos, o justificaciones de `N/A` no verificadas.
### Approver
Reviewer; Security cuando aplica.
### Evidence
`review.md` con hallazgos, verificación de `N/A` y `Definition of Done Check`.
## Convergence Gate
### Entry Criteria
Review Gate aprobado.
### Blocking Conditions
Existe divergencia (ver [Convergence](#convergence)) o traceability incompleta.
### Approver
Orchestrator; Human para excepciones de traceability.
### Evidence
`traceability.md` completo, o FR/AC afectados y test en `change-record.md`.
## Release Gate
### Entry Criteria
Convergence Gate aprobado.
### Blocking Conditions
No se cumple Definition of Done, no hay rollback o falta aprobación humana.
### Approver
Human.
### Evidence
`Release Ready` en `review.md`, [rollback.md](../07-operations/rollback.md) y registro en [deployment.md](../07-operations/deployment.md).
## Production Ready Gate
### Entry Criteria
Release ejecutado en producción.
### Blocking Conditions
Deployment no verificado, observabilidad, SLO, alerts o runbook ausentes.
### Approver
Human / Operations.
### Evidence
`observability.md`, `slo.md` y `runbook.md` de `docs/07-operations/` actualizados.
## Harness Change Gate
### Entry Criteria
Propuesta de cambio en agents, skills, gates, evals, Constitution o metodología.
### Blocking Conditions
Cambio relevante sin motivación, impacto, compatibilidad, aprobación humana o ADR cuando sea arquitectónicamente significativo.
### Approver
Human.
### Evidence
Propuesta con motivación, impacto y compatibilidad; ADR o changelog del proyecto ([Template Versioning](../../README.md#template-versioning)).

## Convergence

Un trabajo converge cuando:
```text
SPEC = IMPLEMENTATION = TESTS = DOCUMENTATION = OBSERVED BEHAVIOR
```
Si existe divergencia, el trabajo no está terminado. Nunca alterar automáticamente los demás artefactos para coincidir con uno incorrecto: primero determinar cuál representa la intención válida, siguiendo la precedencia de [Source of Truth](constitution.md#source-of-truth).
