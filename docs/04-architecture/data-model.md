# Data Model

Status: Draft · Owner: [OWNER]

Entidades, relaciones y ciclo de vida de los datos de [SYSTEM_NAME]. Un cambio estructural activa el Architecture trigger 4 ([work-types.md](../00-governance/work-types.md#applicability-triggers)).

## Entities

| Entity | Description | Owner Component | Lifecycle | Classification | Sensitive Data |
|---|---|---|---|---|---|

- `Lifecycle`: creación, actualización, archivado, retención y eliminación.
- `Classification`: `Public`, `Internal`, `Confidential`, `Restricted`.
- `Sensitive Data`: campos personales o regulados; su tratamiento se define en [security.md](security.md).

## Relationships

| From | To | Cardinality | Rule |
|---|---|---|---|

## Ownership

Cada entidad tiene un único componente dueño que la escribe; los demás acceden mediante contratos.
