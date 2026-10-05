# Learning

**Covers (canonical):** Feedback Flywheel y organización de `docs/08-learning/`.

## Feedback Flywheel

Todo incidente, bug relevante o fallo repetitivo debe analizar si revela una carencia en spec, architecture, tests, evals, quality gates, skills, agent instructions, documentation, observability o applicability triggers. Cuando corresponda, mejorar el harness. Los cambios relevantes al harness pasan por el [Harness Change Gate](../00-governance/quality-gates.md#harness-change-gate).

El objetivo no es solo corregir el error, sino mejorar el sistema que produce software.

```text
SIGNAL (incident, bug, repeated failure, retrospective)
→ ANALYZE (root cause + harness gap)
→ IMPROVE HARNESS
→ VERIFY (sensor, test o eval que detectaría la recurrencia)
→ RECORD (lessons-learned.md)
```

## Harness Gap Categories

| Category | Typical Improvement |
|---|---|
| Spec | Nuevo AC, edge case o regla aclarada |
| Architecture | Regla `AR-XXX`, ADR o boundary explícito |
| Tests / Evals | Regression test o caso de eval |
| Quality Gates | Nueva condición bloqueante o evidencia |
| Skills / Agent Instructions | Paso, check o condición de escalamiento |
| Documentation | Documento corregido o enlazado |
| Observability | Métrica, log o alerta faltante |
| Applicability Triggers | Trigger nuevo o redefinido |
| Feedback Sensors | Sensor nuevo o pasado a bloqueante |

## When to Run

- Después de todo incidente y de todo `HOTFIX`.
- Al cerrar un `BUG` relevante o detectar un fallo repetido.
- En cada retrospectiva (cierre de release o hito).

## Contents

| Path | Purpose |
|---|---|
| [incidents/](incidents/_template.md) | Un archivo por incidente: `INC-XXX-[SLUG].md` |
| [retrospectives/](retrospectives/_template.md) | Un archivo por retrospectiva: `[DATE]-[SLUG].md` |
| [lessons-learned.md](lessons-learned.md) | Lecciones consolidadas con enlace a su origen |
| [tech-debt.md](tech-debt.md) | Registro de deuda técnica y origen de los `TD-XXX` |
