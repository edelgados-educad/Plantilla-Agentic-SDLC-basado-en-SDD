# Architecture Rules

Status: Draft · Owner: [OWNER]

**Covers:** reglas arquitectónicas verificables y preferentemente automatizables.
**Delegates:** principios a [Architecture Principles](../00-governance/constitution.md#architecture-principles).

| ID | Description | Rationale | Automated | Verification | Status |
|---|---|---|---|---|---|
| AR-001 | [DESCRIPTION] | | No | | Proposed |

- `Automated`: `Yes` (verificada por un test en `tests/architecture/` o por un sensor) o `No` (verificada en REVIEW).
- `Status`: `Proposed`, `Active`, `Deprecated`.
- Toda regla `Active` con `Automated: No` es candidata a automatización en [tech-debt.md](../08-learning/tech-debt.md).

## Rule Categories

Tipos de regla habituales: dirección de dependencias entre capas o módulos ([components.md](../04-architecture/components.md)), ausencia de ciclos, acceso a datos solo a través del componente dueño, integraciones externas solo mediante adaptadores y ausencia de secretos en el repositorio.
