# Quality Score

Status: Draft · Owner: [OWNER]

Señal periódica y simple del estado del producto y del harness. No es una fórmula: cada dimensión se puntúa por separado para orientar mejoras.

## Scale

| Score | Meaning |
|---|---|
| 0 | Ausente |
| 1 | Inicial: existe, pero es manual o incompleto |
| 2 | Gestionado: consistente y mayormente verificado |
| 3 | Automatizado: verificado por sensores y estable |

## Dimensions

| Dimension | What Is Evaluated | Source |
|---|---|---|
| Traceability | FR con AC, Task y Test/Eval completos | `traceability.md` de cada spec |
| Verification | AC verificados por pruebas automáticas | [acceptance-tests.md](acceptance-tests.md) |
| Feedback Sensors | Sensores disponibles y bloqueantes | [feedback-sensors.md](feedback-sensors.md) |
| Architecture Conformance | Reglas `AR-XXX` automatizadas y en verde | [architecture-rules.md](architecture-rules.md) |
| Security | Hallazgos abiertos y checks automatizados | [security-checks.md](security-checks.md) |
| Convergence | Trabajos cerrados sin divergencias | `docs/05-plans/completed/` |
| Tech Debt | Tendencia de ítems `High` abiertos | [tech-debt.md](../08-learning/tech-debt.md) |
| Documentation | Documentos con `Status` vigente y `N/A` justificados | `docs/` |

## Frequency

Al cerrar cada release y, como mínimo, una vez por trimestre (ajustable por proyecto).

## Interpretation

Una dimensión en 0 o 1 genera una acción en la retrospectiva o un ítem de tech debt. Una caída respecto de la evaluación anterior se analiza en el [Feedback Flywheel](../08-learning/README.md).

## History

| Date | Scope | Scores by Dimension | Actions |
|---|---|---|---|
