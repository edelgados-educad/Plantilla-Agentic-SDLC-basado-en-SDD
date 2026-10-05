# Contracts

Contratos de la feature: APIs, events, messages, schemas e interfaces entre componentes. El formato es libre siempre que sea versionable y verificable; la plantilla no impone tecnología.

- Un archivo por contrato, con nombre, versión y consumidores conocidos.
- Los cambios incompatibles requieren análisis de impacto, versionado, aprobación humana y contract tests cuando corresponda.
- Contract tests en `tests/contract/`. Gate: [Contract Gate](../../../00-governance/quality-gates.md#contract-gate).
