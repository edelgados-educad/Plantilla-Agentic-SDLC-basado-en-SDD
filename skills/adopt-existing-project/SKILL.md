---
name: adopt-existing-project
description: Incorpora el Agentic SDLC basado en SDD en un repositorio que ya tiene código, sin sobrescribir archivos existentes, documentando solo el área que se va a modificar y creando el primer work item.
---

# Purpose

Aplicar la metodología donde se va a trabajar sin detener el proyecto para documentarlo entero. No se documenta todo el sistema, solo el área que se va a modificar: la gobernanza se adopta donde se trabaja y crece con cada cambio.

# When to Use

- Se quiere aplicar la metodología en un repositorio con código existente y hay un cambio concreto por realizar.
- Para un repositorio nuevo, usar [bootstrap-project](../bootstrap-project/SKILL.md).

# Inputs

- Ruta al repositorio de la plantilla (versión a aplicar, leída de su `VERSION`).
- Repositorio destino: el agente trabaja dentro de él.
- Descripción breve del cambio que se va a realizar.
- Project Profile propuesto por el agente a partir de lo observado y confirmado por el humano ([Project Profiles](../../docs/00-governance/work-types.md#project-profiles)).

# Process

1. **Inventario previo, sin escribir nada.** Listar los elementos del destino que colisionan con la estructura de la plantilla: `README.md`, `AGENTS.md`, `ARCHITECTURE.md`, `docs/`, `agents/`, `skills/`, `evals/`, `tests/`, `scripts/`, `src/`, `infra/`. Conservar el inventario para la validación.
2. **Plan de adopción.** Proponer, por cada elemento, la acción y la ruta final según la tabla `Adoption Rules`, junto con el Project Profile sugerido. Pedir aprobación humana; sin aprobación no se escribe nada.
3. **Harness Root.** Si la metodología no queda en las rutas por defecto (Harness Root distinto de `docs/`, README de la metodología fuera de la raíz, o `agents/`, `skills/`, `evals/` reubicados):
   - registrar `Harness Root: [HARNESS_ROOT]` al inicio de `AGENTS.md` (p. ej., `Harness Root: docs/harness`);
   - actualizar las rutas que referencian la estructura en `AGENTS.md`, `README.md`, `agents/` y `skills/`, y en todo otro archivo copiado que enlace a `docs/` (p. ej., `ARCHITECTURE.md`, `evals/`), además de los enlaces de los documentos de la metodología hacia archivos de la raíz;
   - comprobar que todo enlace interno resuelva a un archivo existente.
4. **Aplicar el perfil** con los pasos 1 a 3 de [bootstrap-project](../bootstrap-project/SKILL.md): placeholders de nivel proyecto, documentos `N/A` por perfil, `Template Version` y Project Profile registrados.
5. **ASSESS acotado** ([assess-codebase](../assess-codebase/SKILL.md), limitado al área afectada):
   - completar [feedback-sensors.md](../../docs/06-quality/feedback-sensors.md) detectando lo que ya existe (tests, linter, formatter, type checker, CI, security scanning), con comando y ubicación reales;
   - redactar [current-state.md](../../docs/01-discovery/current-state.md) solo del área afectada: componentes involucrados, dependencias, tests existentes en esa zona, riesgos y problemas conocidos;
   - registrar cada regla de negocio implícita como pregunta abierta (`Implicit Rules` con `Decision: Open` y, si el work item tiene spec, en su tabla `Open Questions`); nunca como regla confirmada;
   - no reconstruir la arquitectura completa ni escribir specs de funcionalidades que no se van a tocar.
6. **Primer work item.** Clasificarlo según [work-types.md](../../docs/00-governance/work-types.md) (`CHG-001`, `BUG-001`, `FEAT-001`, etc.), registrarlo en `docs/05-plans/index.md` y crear su `change-record.md` o carpeta de plan ([create-plan](../create-plan/SKILL.md)). Si su Work Type requiere spec y el área no tiene una, crearla solo para el comportamiento afectado ([create-spec](../create-spec/SKILL.md)).

## Adoption Rules

| Element in target | Rule |
|---|---|
| `README.md` existe | No reemplazar. Agregar al final `## Engineering Harness` con Project Profile, `Template Version` y enlace a `AGENTS.md`. El README de la metodología se ubica en `[HARNESS_ROOT]/README.md`. |
| `AGENTS.md` existe | Fusionar: conservar el contenido existente y agregar el mapa de la metodología. Mostrar la propuesta antes de escribir. |
| `ARCHITECTURE.md` existe | No reemplazar. Agregar un enlace a la documentación de arquitectura de la metodología. |
| `docs/` existe con contenido | Ubicar la metodología en `docs/harness/` (Harness Root). |
| `agents/`, `skills/` o `evals/` existen con otro uso | Proponer una ubicación alternativa bajo el Harness Root y pedir confirmación. |
| `tests/`, `src/`, `infra/`, `scripts/` | No crear carpetas nuevas. Respetar la estructura existente y registrar las ubicaciones reales en `feedback-sensors.md` y `test-strategy.md`. |
| `VERSION`, `CHANGELOG.md` de la plantilla | No se copian (misma decisión que `bootstrap-project`). |
| Sin colisión | Copiar desde la plantilla. |

Los archivos de configuración de herramientas o adaptadores que ya existan en el destino no se modifican.

# Outputs

- Metodología instalada sin sobrescribir archivos existentes.
- `Harness Root` registrado en `AGENTS.md` cuando aplica.
- Feedback sensors inventariados con comandos y ubicaciones reales.
- `current-state.md` del área afectada y preguntas abiertas pendientes de confirmación humana.
- Primer work item creado y registrado.

# Validation

- Ningún archivo preexistente fue reemplazado o eliminado (comparar contra el inventario del paso 1).
- Enlaces internos de la metodología válidos desde el Harness Root.
- `AGENTS.md` sigue en 100 líneas o menos tras la fusión; si no, mover el contenido previo a un documento enlazado y pedir confirmación.
- Ninguna regla de negocio registrada como confirmada sin fuente humana.
- Project Profile y `Template Version` coinciden en `AGENTS.md`, `## Engineering Harness` y el README de la metodología.

# Failure Conditions

- El humano no aprueba el plan de adopción: detenerse sin escribir.
- Colisiones sin resolver: detenerse y escalar.
- El cambio a realizar no está descrito: pedirlo antes de iniciar el ASSESS.
