---
name: bootstrap-project
description: Inicializa un repositorio recién creado desde la plantilla. Reemplaza los placeholders de nivel proyecto, registra versión de origen y Project Profile, marca los documentos N/A por perfil y deja el proyecto listo para Discovery.
---

# Purpose

Convertir una copia de la plantilla en un proyecto listo para Discovery en minutos, con origen y perfil registrados y sin perder la estructura de la metodología.

# When to Use

- Inmediatamente después de crear un repositorio nuevo desde la plantilla (CLASSIFY del Work Type `PROJECT`).
- Si el repositorio ya tiene código, usar [adopt-existing-project](../adopt-existing-project/SKILL.md).

# Inputs

Solicitar al humano en un solo bloque de preguntas:

1. `[PROJECT_NAME]`, `[PROJECT_DESCRIPTION]` y `[OWNER]` (rol responsable).
2. Project Profile (`LITE`, `STANDARD` o `CRITICAL`), mostrando como ayuda la tabla `When to Use` de [Project Profiles](../../docs/00-governance/work-types.md#project-profiles).
3. ¿El proyecto procesará datos personales o regulados? (Sí / No).

Si la respuesta 3 es "Sí" y el perfil elegido es `LITE` (o `STANDARD`), aplicar los [Profile Escalation Triggers](../../docs/00-governance/work-types.md#profile-escalation-triggers), proponer subir de perfil y esperar la decisión humana antes de continuar.

# Process

1. **Placeholders de nivel proyecto.** Reemplazar `[PROJECT_NAME]`, `[PROJECT_DESCRIPTION]`, `[OWNER]`, `[PROJECT_PROFILE]` y `[TEMPLATE_VERSION]` en todo el repositorio, con dos excepciones:
   - templates (`_template/` y `_template.md`), que conservan todos sus placeholders hasta copiarse;
   - menciones entre backticks, que documentan el formato (p. ej., el registro de `## Placeholders`).

   Los placeholders de nivel trabajo (`[WORK_ID]`, `[FEATURE_NAME]`, `[SLUG]`, etc.) se mantienen. `[HARNESS_ROOT]` no aplica: en un proyecto nuevo la metodología vive en las rutas por defecto. Niveles en [Placeholders](../../README.md#placeholders).
2. **Origen y perfil.** En `## Project` del README registrar `Template Version` (contenido de `VERSION`), `Project Profile` y `Created` (fecha actual, `YYYY-MM-DD`).
3. **Documentos `N/A`.** Según [Profile Requirements](../../docs/00-governance/work-types.md#profile-requirements), reemplazar la línea `Status:` de cada documento que el perfil no exige por `Status: N/A (Profile [PROJECT_PROFILE])` con el perfil elegido. En `LITE`: discovery salvo `problem.md` y `scope.md`, product, architecture y operations. No borrar archivos.
4. **README del proyecto.** Convertir el README de la plantilla según la tabla `README Conversion`.
5. **`VERSION` y `CHANGELOG.md`.** Eliminarlos del proyecto. Es la decisión fija de esta skill: ambos pertenecen solo a la plantilla ([Template Versioning](../../README.md#template-versioning)) y el origen ya queda en `Template Version`. Si el proyecto necesita changelog propio, se crea nuevo; nunca se reutiliza el de la plantilla.
6. **Siguiente paso.** Indicar al humano que la próxima acción es completar [problem.md](../../docs/01-discovery/problem.md) (IDEA → DISCOVERY) y entregar el resumen de salida.

## README Conversion

| Section | Action |
|---|---|
| Título e introducción | Reemplazar por `[PROJECT_NAME]`, `[PROJECT_DESCRIPTION]` y una línea que indique que el proyecto usa el Agentic SDLC basado en SDD, con enlace a `AGENTS.md`. |
| `## Template Versioning` | Reducir a: versión de origen en `Project`; el proyecto no contiene `VERSION` ni `CHANGELOG.md` de la plantilla; cambios de harness o Constitution mediante ADR o changelog propio. Conservar el encabezado: otros documentos lo enlazan. |
| `## Quick Start` | Eliminar: describe cómo usar la plantilla, no el proyecto. |
| `## Repository Structure` | Eliminar la fila de `VERSION` y `CHANGELOG.md`. |
| Resto (`Project`, `Philosophy`, `Lifecycle`, `IDs and Traceability`, `How To`, `Placeholders`, etc.) | Conservar: son operativas y sus anchors están enlazados desde otros documentos. |

# Outputs

- Repositorio sin placeholders de nivel proyecto fuera de templates.
- `Template Version`, `Project Profile` y `Created` registrados en el README.
- Documentos no aplicables marcados `N/A` por perfil.
- Resumen para el humano: perfil, documentos `N/A`, escalation triggers evaluados y próximos pasos (Discovery, primer work item).

# Validation

- La búsqueda de `[PROJECT_NAME]`, `[PROJECT_DESCRIPTION]`, `[OWNER]`, `[PROJECT_PROFILE]` y `[TEMPLATE_VERSION]` no devuelve resultados fuera de templates y de menciones entre backticks.
- README con `Template Version`, `Project Profile` y `Created` completos.
- Ningún archivo de la estructura eliminado, salvo `VERSION` y `CHANGELOG.md` (paso 5).
- Enlaces internos válidos, incluidos los anchors del README enlazados desde governance.

# Failure Conditions

- El humano no define el Project Profile: detenerse sin modificar archivos.
- Respuestas contradictorias con los escalation triggers (p. ej., datos personales con perfil `LITE`) sin resolver: detenerse y escalar.
- `VERSION` ausente o ilegible: pedir la versión al humano; nunca inventarla.
