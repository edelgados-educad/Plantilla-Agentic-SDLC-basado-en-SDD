# Test Strategy

Status: Draft · Owner: [OWNER]

Tipos de verificación del proyecto, cuándo son obligatorios y dónde viven. Su ejecución automática se registra como feedback sensor ([feedback-sensors.md](feedback-sensors.md)).

| Type | Purpose | When Required | Location |
|---|---|---|---|
| Unit | Verificar lógica aislada y determinista | Toda lógica nueva o modificada | `tests/unit/` |
| Integration | Verificar la interacción entre componentes y con dependencias | Persistencia, integraciones o flujos entre componentes | `tests/integration/` |
| Contract | Verificar compatibilidad entre productor y consumidor | Contracts triggers activos | `tests/contract/` |
| Architecture | Verificar reglas `AR-XXX` automatizables | Toda regla con `Automated: Yes` | `tests/architecture/` |
| End-to-End | Verificar journeys críticos completos | AC con `Verification Type: e2e` | Definida por el proyecto |
| Regression | Evitar que un defecto reaparezca | Todo `BUG` y `HOTFIX` | Tipo correspondiente en `tests/` y `evals/regression/` |
| Security | Detectar vulnerabilidades y fugas | Security Review triggers activos y cada release | [security-checks.md](security-checks.md), `evals/security/` |
| Performance | Verificar performance budgets | NFR de performance afectados | [performance-budgets.md](performance-budgets.md) |
| AI Evals | Medir calidad de comportamiento no determinista | El producto incluye IA | `evals/ai/` |

## Principles

- Las pruebas se derivan de AC, examples y edge cases ([acceptance-tests.md](acceptance-tests.md)).
- Preferir pruebas rápidas y deterministas; aislar tiempo, red y aleatoriedad.
- Un test inestable se corrige o se registra como tech debt; nunca se desactiva en silencio.
- Datos de prueba sintéticos o anonimizados; nunca datos personales reales.

## Coverage Expectations

Objetivo acordado por tipo y forma de medirlo, o `N/A` con motivo.

| Type | Target | Measured By |
|---|---|---|
