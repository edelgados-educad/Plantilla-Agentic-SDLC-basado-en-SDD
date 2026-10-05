# Plans Index

**Covers:** registro de todo trabajo en ejecución o cerrado, de cualquier Work Type.
**Delegates:** catálogo de especificaciones de comportamiento a [03-specs/index.md](../03-specs/index.md).

El Orchestrator agrega la fila en CLASSIFY. Los artefactos de cada trabajo se copian desde [_template/](_template/plan.md) a `active/[WORK_ID]-[SLUG]/` según [Artifacts by Work Type](../00-governance/work-types.md#artifacts-by-work-type); al cerrar, la carpeta se mueve a `completed/`.

| ID | Type | Title | Status | Owner | Spec | Plan |
|---|---|---|---|---|---|---|

Estados: `Planned`, `Active`, `Blocked`, `Done`, `Cancelled`. `Spec` enlaza la spec creada o afectada, o `—`. `Plan` enlaza la carpeta del trabajo.

Ejemplo de fila: `| FEAT-001 | FEATURE | [WORK_TITLE] | Active | [OWNER] | [spec](../03-specs/FEAT-001-[SLUG]/spec.md) | [plan](active/FEAT-001-[SLUG]/plan.md) |`
