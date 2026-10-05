# Components

Status: Draft · Owner: [OWNER]

Componentes internos de cada contenedor. Las dependencias permitidas se convierten en reglas verificables en [architecture-rules.md](../06-quality/architecture-rules.md). Copiar la sección `## [COMPONENT_NAME]` por componente.

## [COMPONENT_NAME]

| Field | Value |
|---|---|
| Container | |
| Responsibility | Una responsabilidad principal, en una frase. |
| Ownership | |
| Dependencies | Componentes y servicios que usa hoy. |
| Permitted Dependencies | Componentes de los que puede depender; lo no listado está prohibido. |
| Code Location | Ruta dentro de `src/`. |

## Dependency Rules

Dependencias permitidas entre componentes (p. ej., por capas o módulos). Modificarlas activa el Architecture trigger 3 ([work-types.md](../00-governance/work-types.md#applicability-triggers)).

| From | May Depend On | Must Not Depend On |
|---|---|---|
