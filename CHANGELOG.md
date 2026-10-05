# Changelog

Registro de cambios de la plantilla **Agentic SDLC basado en SDD**. Formato simple compatible con [Semantic Versioning](https://semver.org/lang/es/).

Este changelog pertenece **solo a la plantilla**. Los proyectos derivados no heredan `VERSION` ni este archivo: registran su origen en `Template Version` y sus cambios de harness o Constitution mediante ADR o en su propio changelog. Niveles MAJOR / MINOR / PATCH y reglas de alcance: [Template Versioning](README.md#template-versioning).

## Unreleased

Sin cambios pendientes.

## 1.4.0 - 2026-10-04

Versión MINOR: agrega un documento visual sin cambiar la metodología.

### Added

- `PROCESS-FLOW.md`: diagramas del proceso (vista general, lifecycle con gates y roles, ruta por Work Type, applicability, Emergency Path, estados de tareas y specs, Feedback Flywheel) y tabla de roles, como refuerzo visual para compartir la plantilla.

### Changed

- README: enlaza `PROCESS-FLOW.md` desde `Lifecycle` y `Repository Structure`.

## 1.3.0 - 2026-10-04

Versión MINOR: agrega una carpeta para material fuente sin cambiar la metodología.

### Added

- `docs/references/`: índice de material fuente (referencias visuales, reglas de despliegue de otros sistemas, normativa) con ID `REF-001`; las reglas se resumen en texto en el documento que las usa.

### Changed

- README (IDs y estructura), AGENTS.md (mapa), GLOSSARY.md y `create-spec`: incluyen las referencias.

## 1.2.0 - 2026-10-04

Versión MINOR: agrega un documento de referencia sin cambiar la metodología.

### Added

- `GLOSSARY.md`: glosario de términos técnicos y de la metodología, organizado en 10 secciones, con enlace a la ubicación canónica de cada concepto.

### Changed

- `docs/01-discovery/glossary.md`: queda solo para términos del proyecto; delega los de la metodología a `GLOSSARY.md` y deja de repetir sus acrónimos.
- README, AGENTS.md y `adopt-existing-project`: incluyen `GLOSSARY.md` en la estructura, el mapa y las reglas de adopción.

## 1.1.1 - 2026-10-04

Versión PATCH: solo documentación; el flujo de la metodología no cambia.

### Changed

- README: la sección `Adoption` se reemplaza por `Quick Start`, ubicada al inicio, con pasos concretos para proyectos nuevos y existentes.
- `bootstrap-project`: la conversión del README elimina `Quick Start` en lugar de `Adoption`.

## 1.1.0 - 2026-10-04

Versión MINOR: agrega dos skills y un concepto sin cambiar la metodología ni la estructura de carpetas.

### Added

- Skill `bootstrap-project`: deja un proyecto nuevo listo para Discovery (placeholders de nivel proyecto, versión de origen, Project Profile, documentos `N/A` por perfil y README del proyecto).
- Skill `adopt-existing-project`: incorpora la metodología en un repositorio existente sin sobrescribir archivos, con ASSESS acotado al área afectada y primer work item.
- Concepto Harness Root y placeholder `[HARNESS_ROOT]`.
- Niveles de placeholders (proyecto y trabajo) en el registro del README.

### Changed

- README: el onboarding greenfield/brownfield se reemplaza por la sección `Adoption`, que enlaza a las nuevas skills; campo `Created` en `Project`.
- AGENTS.md: regla de Harness Root y nuevas skills en el mapa.
- work-types.md: `PROJECT` y la adopción de repositorios existentes enlazan a las nuevas skills.

## 1.0.0 - 2026-10-04

### Added

- Lifecycle canónico de 20 etapas con Lifecycle Mapping (Stage, Artifact, Gate, Owner Role).
- Project Profiles (`LITE`, `STANDARD`, `CRITICAL`), Work Types, Lifecycle Applicability, Applicability Triggers y Emergency Change Procedure.
- Governance: Constitution, Engineering Principles, Definition of Done y 15 Quality Gates.
- Plantillas de Discovery, Product, Feature Spec, Architecture (incluye ADR), Plans, Quality, Operations y Learning.
- Siete agentes y siete skills agnósticos de proveedor.
- Estructura de `evals/` y `tests/`.
- Puntos de entrada `AGENTS.md`, `ARCHITECTURE.md` y `README.md`.
