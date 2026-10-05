# Business Rules

Status: Draft · Owner: [OWNER]

Reglas de negocio globales del producto. Las reglas propias de una feature viven en su spec (`[WORK_ID]/BR-001`) y no se copian aquí.

| ID | Rule | Source | Date | Applies To | Status |
|---|---|---|---|---|---|
| BR-001 | [DESCRIPTION] | | [DATE] | | Proposed |

Estados: `Proposed`, `Active`, `Deprecated`.

- Toda regla tiene `Source` verificable (rol humano, norma o documento). Sin fuente no es regla: es una `Open Question` en la spec que la necesita.
- Solo las reglas `Active` obligan a specs e implementación. Pasar a `Active` requiere aprobación del owner funcional.
- `Applies To` lista capabilities o specs afectadas.
- Una regla `Deprecated` no se borra: se indica en `Applies To` la regla que la reemplaza.
