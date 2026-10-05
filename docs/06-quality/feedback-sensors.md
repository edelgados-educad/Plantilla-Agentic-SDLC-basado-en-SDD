# Feedback Sensors

Status: Draft · Owner: [OWNER]

**Covers (canonical):** definición, inventario y reglas de los feedback sensors del proyecto.

Un feedback sensor es una verificación automática que devuelve a humanos y agentes una señal objetiva (pass/fail o métrica) sobre un cambio, sin depender de juicio. Es el mecanismo principal del [Verification Gate](../00-governance/quality-gates.md#verification-gate).

> Si una regla puede verificarse automáticamente, se prefiere la verificación automática sobre la instrucción escrita.

## Inventory

| Sensor | Available | Command/Location | Blocking | Notes |
|---|---|---|---|---|
| Compiler | | | | |
| Type checker | | | | |
| Formatter | | | | |
| Linter | | | | |
| Unit tests | | | | |
| Integration tests | | | | |
| Contract tests | | | | |
| Architecture tests | | | | |
| Security scanning | | | | |
| Performance tests | | | | |
| Evals | | | | |

`Available`: `Yes`, `No`, `N/A`. `Blocking`: `Yes` o `No`. Se completa en ASSESS y se mantiene actualizado.

## Rules

- El Implementer ejecuta los sensores antes de mover una tarea a `REVIEW`; el Tester los ejecuta antes del Verification Gate.
- Un sensor bloqueante que falla detiene el avance; nunca se desactiva ni se debilita para pasar.
- Orden recomendado: del más rápido al más lento (formatter, linter, type checker, compiler, tests, scanning, performance, evals).
- Los resultados se registran en `Verification Evidence` de `progress.md` o en `Verification` de `change-record.md`.
- Un sensor ausente (`No`) se evalúa como posible Tech Debt en [tech-debt.md](../08-learning/tech-debt.md).
- Un defecto que ningún sensor detectó alimenta el [Feedback Flywheel](../08-learning/README.md).
