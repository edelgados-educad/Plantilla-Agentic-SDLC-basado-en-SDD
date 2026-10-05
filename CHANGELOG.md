# Changelog

Registro de cambios de la plantilla **Agentic SDLC basado en SDD**. Formato simple compatible con [Semantic Versioning](https://semver.org/lang/es/).

Este changelog pertenece **solo a la plantilla**. Los proyectos derivados no heredan `VERSION` ni este archivo: registran su origen en `Template Version` y sus cambios de harness o Constitution mediante ADR o en su propio changelog. Niveles MAJOR / MINOR / PATCH y reglas de alcance: [Template Versioning](README.md#template-versioning).

## Unreleased

Sin cambios pendientes.

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
