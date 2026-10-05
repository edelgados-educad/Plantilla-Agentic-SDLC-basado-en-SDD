# [WORK_ID] — Traceability

Matriz de la cadena `Requirement → Acceptance Criterion → Task → Test / Eval` ([IDs and Traceability](../../../README.md#ids-and-traceability)). La columna `Task` usa la forma completa `[WORK_ID]/T001`; `Test/Eval` indica la ruta del test o eval.

| FR | AC | Task | Test/Eval | Status |
|---|---|---|---|---|
| FR-001 | AC-001 | [WORK_ID]/T001 | | Pending |

Estados: `Pending`, `Verified`, `Failed`, `Exception`. Perfil `LITE`: la columna `Task` puede omitirse.

## Checks

Antes del [Convergence Gate](../../00-governance/quality-gates.md#convergence-gate):

- [ ] Ningún FR sin AC.
- [ ] Ningún AC sin Task (salvo perfil `LITE`).
- [ ] Ninguna Task sin verificación (`Verified by:`).
- [ ] Ningún test o eval sin requirement relacionado.
- [ ] Ninguna fila obligatoria en `Pending` o `Failed`.

## Exceptions

Filas incompletas aceptadas. Requieren justificación, riesgo y aprobación humana; la fila queda en `Exception`.

| Row | Justification | Risk | Approved By | Date |
|---|---|---|---|---|
