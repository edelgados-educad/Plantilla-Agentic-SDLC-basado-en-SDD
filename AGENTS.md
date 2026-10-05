# AGENTS.md

Punto de entrada neutral para cualquier agente o arnés de programación, y para humanos. Es un mapa, no una enciclopedia: cada línea enlaza a su fuente canónica. El repositorio es la fuente de verdad.

**Harness Root:** si al inicio de este archivo existe la línea `Harness Root: [HARNESS_ROOT]`, todas las rutas de la metodología son relativas a esa carpeta (`docs/...` se lee como `[HARNESS_ROOT]/...`).

# Mission

Construir [PROJECT_NAME] con el Agentic SDLC basado en SDD: especificar antes de implementar, verificar con mecanismos automáticos y dejar toda decisión significativa en el repositorio, nunca solo en una conversación.

# Repository Map

- **Governance:** [constitution](docs/00-governance/constitution.md) · [principles](docs/00-governance/engineering-principles.md) · [work types](docs/00-governance/work-types.md) · [definition of done](docs/00-governance/definition-of-done.md) · [quality gates](docs/00-governance/quality-gates.md)
- **Discovery:** [docs/01-discovery/](docs/01-discovery/problem.md) — problema, objetivos, alcance, restricciones, estado actual.
- **Product:** [docs/02-product/](docs/02-product/product-spec.md) — visión, journeys, business rules, NFR.
- **Specifications:** [docs/03-specs/index.md](docs/03-specs/index.md) — feature specs y plantilla.
- **Architecture:** [ARCHITECTURE.md](ARCHITECTURE.md) — mapa hacia `docs/04-architecture/` y ADR.
- **Plans:** [docs/05-plans/index.md](docs/05-plans/index.md) — registro de trabajos, planes y tareas.
- **Quality:** [docs/06-quality/](docs/06-quality/feedback-sensors.md) — feedback sensors, test strategy, reglas y checks.
- **Operations:** [docs/07-operations/](docs/07-operations/deployment.md) — despliegue, observabilidad, SLO, runbook, rollback.
- **Learning:** [docs/08-learning/](docs/08-learning/README.md) — Feedback Flywheel, incidentes, tech debt.
- **Agents:** [orchestrator](agents/orchestrator.md) · [analyst](agents/analyst.md) · [architect](agents/architect.md) · [implementer](agents/implementer.md) · [tester](agents/tester.md) · [reviewer](agents/reviewer.md) · [security](agents/security.md)
- **Skills:** [bootstrap-project](skills/bootstrap-project/SKILL.md) · [adopt-existing-project](skills/adopt-existing-project/SKILL.md) · [assess-codebase](skills/assess-codebase/SKILL.md) · [create-spec](skills/create-spec/SKILL.md) · [clarify-spec](skills/clarify-spec/SKILL.md) · [create-plan](skills/create-plan/SKILL.md) · [implement-feature](skills/implement-feature/SKILL.md) · [review-feature](skills/review-feature/SKILL.md) · [debug-issue](skills/debug-issue/SKILL.md)
- **Evals:** [evals/README.md](evals/README.md) — evaluaciones con datasets y umbrales.
- **Glossary:** [GLOSSARY.md](GLOSSARY.md) — definición breve de cada término técnico y de la metodología.

# Lifecycle

`IDEA → CLASSIFY → ASSESS → CONSTITUTION → DISCOVERY → PRODUCT SPEC → FEATURE SPEC → CLARIFY → ARCHITECTURE → CONTRACTS → IMPLEMENTATION PLAN → TASK DAG → AGENT EXECUTION → FEEDBACK SENSORS → REVIEW → CONVERGENCE → RELEASE → OBSERVABILITY → LEARNING → HARNESS IMPROVEMENT` — artefactos, gates y roles en [README.md](README.md#lifecycle).

# Work Types

Project Profile vigente: [PROJECT_PROFILE] (mismo valor que el README). Work Types: `PROJECT`, `FEATURE`, `CHANGE`, `BUG`, `HOTFIX`, `REFACTOR`, `TECH_DEBT`, `SPIKE`, `DOCUMENTATION` — ver [work-types.md](docs/00-governance/work-types.md).

# Mandatory Workflow

## Before Implementation

1. Leer la [Constitution](docs/00-governance/constitution.md).
2. Identificar el Project Profile vigente y evaluar profile escalation triggers.
3. Clasificar el Work Type según [work-types.md](docs/00-governance/work-types.md).
4. Leer el contexto de Product relevante.
5. Leer la spec y verificar estado `Approved` cuando corresponda.
6. Leer Architecture y ADRs aplicables.
7. Verificar Acceptance Criteria o FR/AC afectados.
8. Determinar Lifecycle Applicability evaluando triggers.
9. Crear o actualizar `plan.md` o `change-record.md`.
10. Identificar Tasks y Dependencies.

## Before Completion

1. Ejecutar Feedback Sensors ([feedback-sensors.md](docs/06-quality/feedback-sensors.md)).
2. Ejecutar Security Checks cuando apliquen ([security-checks.md](docs/06-quality/security-checks.md)).
3. Ejecutar Evals aplicables.
4. Verificar Acceptance Criteria.
5. Actualizar Traceability.
6. Actualizar Documentation y `progress.md`.
7. Comprobar [Convergence](docs/00-governance/quality-gates.md#convergence).

# Never

- Inventar reglas de negocio.
- Saltarse tests u ocultar tests fallidos.
- Exponer secretos.
- Cambiar arquitectura o contratos silenciosamente.
- Marcar `N/A` sin evaluar triggers.
- Ocultar fallos no resueltos.

# Escalate When

- Requirements en conflicto o comportamiento de negocio ambiguo.
- Operaciones destructivas.
- Riesgo de seguridad crítico.
- Cambio arquitectónico relevante.
- Trigger activo que se quiere marcar `N/A`.
- Profile escalation trigger detectado.
- Operación de emergencia en producción.

Quién aprueba: [Human Approval Rules](docs/00-governance/constitution.md#human-approval-rules).
