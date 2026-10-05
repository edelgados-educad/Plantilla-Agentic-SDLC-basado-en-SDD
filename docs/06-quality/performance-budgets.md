# Performance Budgets

Status: Draft · Owner: [OWNER]

Límites concretos y medibles derivados de los NFR de performance ([non-functional-requirements.md](../02-product/non-functional-requirements.md)). Todo budget referencia un `NFR-XXX`; sin NFR no hay budget.

| Budget | Metric | Threshold | Load Conditions | NFR | Verification | Status |
|---|---|---|---|---|---|---|

- `Verification`: test de performance, sensor o monitoreo en producción.
- `Status`: `Proposed`, `Active`, `Deprecated`.
- Superar un budget `Active` bloquea el Verification Gate si su sensor es bloqueante ([feedback-sensors.md](feedback-sensors.md)).
