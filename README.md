# Agentic SDLC basado en SDD

Plantilla reutilizable, versionada y agnóstica de proveedor de IA para desarrollar software con humanos y agentes. Combina Spec-Driven Development, Context Engineering, Harness Engineering, Architecture as Code, Feedback Sensors, Quality Gates, Evals, Human-in-the-loop y Continuous Learning.

Resuelve un problema concreto: cuando el conocimiento vive en conversaciones con modelos, el software pierde trazabilidad, verificabilidad y continuidad. Aquí el repositorio es la fuente de verdad y [AGENTS.md](AGENTS.md) es el punto de entrada neutral para cualquier agente. Sirve para proyectos greenfield y brownfield.

## Project

- Project Name: [PROJECT_NAME]
- Description: [PROJECT_DESCRIPTION]
- Project Profile: [PROJECT_PROFILE]
- Template Version: [TEMPLATE_VERSION]
- Owner: [OWNER]
- Created: [DATE]

## Quick Start

Ambas vías desembocan en el [lifecycle canónico](#lifecycle); después, cada tarea usa su skill ([How To](#how-to)). Lo que hace el agente en cada paso está detallado en la skill enlazada.

### New Project

1. En GitHub: **Use this template → Create a new repository** (privado si tendrá datos institucionales o personales).
2. Clonar el repositorio y abrirlo en el editor.
3. Pedir al agente: *"Lee `AGENTS.md` y ejecuta `skills/bootstrap-project/SKILL.md`"* ([bootstrap-project](skills/bootstrap-project/SKILL.md)).
4. Responder sus preguntas: nombre, descripción, owner, Project Profile y si habrá datos personales.
5. Revisar los cambios, hacer commit y push.
6. Continuar con Discovery: completar `docs/01-discovery/problem.md`.

### Existing Project

1. Abrir en el editor el repositorio que ya tiene código.
2. Pedir al agente: *"Ejecuta `skills/adopt-existing-project/SKILL.md` con la plantilla `https://github.com/edelgados-educad/Plantilla-Agentic-SDLC-basado-en-SDD`. El cambio a realizar es: …"* ([adopt-existing-project](skills/adopt-existing-project/SKILL.md)).
3. Revisar y aprobar el plan de adopción que propone el agente: no reemplaza ni elimina archivos existentes.
4. Confirmar el Project Profile propuesto.
5. Revisar el `current-state.md` del área afectada, las preguntas abiertas y el primer work item; luego commit y push.

## Template Versioning

La versión de la plantilla vive únicamente en [`VERSION`](VERSION); su historial, en [CHANGELOG.md](CHANGELOG.md). Semantic Versioning: **MAJOR** = cambios incompatibles en metodología o estructura; **MINOR** = nuevas capacidades compatibles; **PATCH** = correcciones sin alterar el flujo.

- `VERSION` y `CHANGELOG.md` pertenecen **solo a la plantilla**.
- Un proyecto derivado registra su origen en `Template Version: [TEMPLATE_VERSION]` (sección Project) y **no hereda** `VERSION` ni `CHANGELOG.md` de la plantilla.
- Los cambios de harness o Constitution en un proyecto derivado se documentan mediante ADR o en el changelog propio del proyecto.

## Philosophy

- **Repository as source of truth:** nada depende de información que solo exista en una conversación ([Source of Truth](docs/00-governance/constitution.md#source-of-truth)).
- **Spec first:** ninguna feature se implementa sin spec aprobada, salvo el Emergency Path.
- **Mechanisms over documentation:** IDs consistentes, campos obligatorios, tablas de columnas fijas, estados enumerados y checklists, listos para automatizar.
- **Human-in-the-loop:** el juicio humano se concentra donde aporta más valor ([Human Approval Rules](docs/00-governance/constitution.md#human-approval-rules)).
- **Progressive disclosure:** documentos de entrada cortos que enlazan al detalle; cada concepto tiene una única ubicación canónica.
- **Provider-agnostic:** sin archivos de un proveedor; los adaptadores son trabajo futuro.

## Lifecycle

```text
IDEA → CLASSIFY → ASSESS → CONSTITUTION → DISCOVERY → PRODUCT SPEC
→ FEATURE SPEC → CLARIFY → ARCHITECTURE → CONTRACTS → IMPLEMENTATION PLAN
→ TASK DAG → AGENT EXECUTION → FEEDBACK SENSORS → REVIEW → CONVERGENCE
→ RELEASE → OBSERVABILITY → LEARNING → HARNESS IMPROVEMENT
```

No todo trabajo recorre todas las etapas: aplican según el Work Type y la Lifecycle Applicability.

### Lifecycle Mapping

| Stage | Artifact | Gate | Owner Role |
|---|---|---|---|
| IDEA | `docs/01-discovery/problem.md` draft o solicitud registrada | — | Human |
| CLASSIFY | `Project Profile` en README (al crear el proyecto) + entrada en `docs/05-plans/index.md` + `Work Type` en `plan.md` | — | Orchestrator (+ Human para el perfil) |
| ASSESS | `current-state.md`, `constraints.md` | Assessment Gate | Analyst |
| CONSTITUTION | `constitution.md` | Governance Gate | Human + Orchestrator |
| DISCOVERY | `docs/01-discovery/*` | Discovery Gate | Analyst |
| PRODUCT SPEC | `docs/02-product/*` | Product Gate | Analyst |
| FEATURE SPEC | `docs/03-specs/[WORK_ID]-[SLUG]/` | Spec Gate | Analyst |
| CLARIFY | `Open Questions` resueltas en la spec | Spec Gate | Analyst + Human |
| ARCHITECTURE | Architecture docs + ADR | Architecture Gate | Architect |
| CONTRACTS | `contracts/` de la spec | Contract Gate | Architect |
| IMPLEMENTATION PLAN | `docs/05-plans/active/[WORK_ID]-[SLUG]/plan.md` | Plan Gate | Orchestrator + Architect |
| TASK DAG | `tasks.md`, `dependencies.md` | Implementation Gate | Orchestrator |
| AGENT EXECUTION | código, tests, `progress.md` | — | Implementer + Tester |
| FEEDBACK SENSORS | resultados de verificación automática | Verification Gate | Tester |
| REVIEW | `review.md` | Review Gate | Reviewer + Security |
| CONVERGENCE | `traceability.md` | Convergence Gate | Orchestrator |
| RELEASE | `docs/07-operations/*` | Release Gate | Human |
| OBSERVABILITY | `observability.md`, `slo.md` | Production Ready Gate | Human / Operations |
| LEARNING | `docs/08-learning/*` | — | Orchestrator + Human |
| HARNESS IMPROVEMENT | cambios en agents, skills, gates, evals | Harness Change Gate | Human |

Condiciones de cada gate: [quality-gates.md](docs/00-governance/quality-gates.md).

### Stage Definitions

| Stage | Definition |
|---|---|
| CLASSIFY | Al crear el proyecto, el humano elige el Project Profile con propuesta del Orchestrator. En cada trabajo, el Orchestrator asigna un Work Type, crea el ID, propone la Lifecycle Applicability y evalúa los profile escalation triggers según `work-types.md`. |
| ASSESS | Greenfield: viabilidad, restricciones iniciales, dependencias conocidas, riesgos. Brownfield, acotado al área afectada por el trabajo: arquitectura real observada, deuda, cobertura de pruebas, reglas implícitas, dependencias, feedback sensors existentes. |
| CLARIFY | Resolución de las `Open Questions` críticas de una spec antes de aprobarla. Las respuestas humanas se registran en la propia spec, nunca solo en la conversación. |
| CONTRACTS | Definición de interfaces públicas o entre componentes (APIs, eventos, mensajes, schemas, formatos de datos) cuando aplique. |

## Project Profiles, Work Types and Lifecycle Applicability

- **Project Profile** (`LITE`, `STANDARD`, `CRITICAL`): se elige una vez por proyecto y fija el rigor base.
- **Work Type** (`PROJECT`, `FEATURE`, `CHANGE`, `BUG`, `HOTFIX`, `REFACTOR`, `TECH_DEBT`, `SPIKE`, `DOCUMENTATION`): se elige por trabajo y define flujo, ID y artefactos.
- **Lifecycle Applicability:** cada etapa se marca por trabajo en `plan.md` o `change-record.md`; los applicability triggers prevalecen sobre el perfil.
- Definición canónica, escalation triggers y Emergency Change Procedure: [work-types.md](docs/00-governance/work-types.md).

## IDs and Traceability

| Element | Format | Scope |
|---|---|---|
| Work item | Según [work-types.md](docs/00-governance/work-types.md#work-types) (`FEAT-001`, `BUG-001`, …) | Global |
| Functional Requirement | `FEAT-001/FR-001` | Spec |
| Product Business Rule | `BR-001` | Global |
| Feature Business Rule | `FEAT-001/BR-001` | Spec |
| Acceptance Criterion | `FEAT-001/AC-001` | Spec |
| Non-functional Requirement | `NFR-001` | Global |
| Task | `[WORK_ID]/T001` | Plan |
| Risk | `[WORK_ID]/R001` | Plan |
| Review Finding | `[WORK_ID]/RV-001` | Plan |
| Architecture Rule | `AR-001` | Global |
| ADR | `ADR-001` | Global |
| Incident | `INC-001` | Global |
| Open Question | `Q-001` | Spec |

Dentro del documento correspondiente puede usarse la forma corta; en referencias entre documentos, siempre la forma completa. Cadena obligatoria: `Requirement → Acceptance Criterion → Task → Test / Eval`.

- Cada AC incluye `Covers:`; cada Task incluye `Covers:` y `Verified by:`.
- `traceability.md` de cada spec consolida la matriz `FR | AC | Task | Test/Eval | Status` (perfil `LITE`: sin columna Task).
- `BUG`, `HOTFIX`, `REFACTOR` y `TECH_DEBT` referencian en `change-record.md` los FR/AC existentes afectados y el test que verifica la corrección o la preservación del comportamiento.
- Ningún trabajo pasa el Convergence Gate con filas obligatorias incompletas; las excepciones requieren justificación, riesgo y aprobación humana.

## Repository Structure

| Path | Purpose |
|---|---|
| `AGENTS.md`, `ARCHITECTURE.md`, `GLOSSARY.md` | Mapas de entrada para agentes y arquitectura; glosario de términos técnicos y de la metodología |
| `VERSION`, `CHANGELOG.md` | Versión e historial de la plantilla |
| `docs/00-governance/` | Constitution, principios, work types, Definition of Done, quality gates |
| `docs/01-discovery/`, `docs/02-product/` | Problema, alcance, estado actual; producto, journeys, reglas, NFR |
| `docs/03-specs/` | Feature specs (`[WORK_ID]-[SLUG]/`) e índice |
| `docs/04-architecture/` | Contexto, contenedores, componentes, datos, integraciones, seguridad, despliegue, ADR |
| `docs/05-plans/` | Registro de trabajos y planes (`active/`, `completed/`) |
| `docs/06-quality/`, `docs/07-operations/` | Sensores, pruebas, reglas y checks; despliegue, observabilidad, SLO, runbook, rollback |
| `docs/08-learning/` | Feedback Flywheel, incidentes, retrospectivas, lecciones, tech debt |
| `agents/`, `skills/` | Siete roles y nueve procedimientos reutilizables |
| `evals/`, `tests/` | Evaluaciones y pruebas |
| `src/`, `infra/`, `scripts/` | Código, infraestructura y automatizaciones del proyecto derivado |

## How To

- **Create a feature:** registrar el `FEAT-XXX` ([create-plan](skills/create-plan/SKILL.md)), copiar `docs/03-specs/_template/` a `docs/03-specs/[WORK_ID]-[SLUG]/` ([create-spec](skills/create-spec/SKILL.md)) y clarificar hasta `Approved` ([clarify-spec](skills/clarify-spec/SKILL.md)).
- **Create a plan:** copiar de `docs/05-plans/_template/` solo los archivos del Work Type a `docs/05-plans/active/[WORK_ID]-[SLUG]/`, justificar la applicability y construir el Task DAG.
- **Create an ADR:** copiar `docs/04-architecture/adr/_template.md` a `ADR-XXX-[SLUG].md`, registrarlo en [adr/index.md](docs/04-architecture/adr/index.md) como `Proposed` y obtener aprobación.
- **Handle a bug:** reproducir con un test que falla, corregir y verificar ([debug-issue](skills/debug-issue/SKILL.md)).
- **Handle a hotfix:** solo ante incidente crítico, con el [Emergency Change Procedure](docs/00-governance/work-types.md#emergency-change-procedure) y post-incident completion obligatoria.
- **Close a work item:** Review y Convergence Gates aprobados, traceability completa, `Done` en `docs/05-plans/index.md`, carpeta movida a `completed/` y Feedback Flywheel evaluado.

Al completar una plantilla: reemplazar texto guía y placeholders sin eliminar encabezados; lo que no aplique se marca `N/A` con motivo.

## Convergence and Feedback Flywheel

- **Convergence:** un trabajo termina solo cuando spec, implementación, tests, documentación y comportamiento observado coinciden ([definición](docs/00-governance/quality-gates.md#convergence)).
- **Feedback Flywheel:** cada incidente o fallo repetido mejora el harness, no solo el código ([definición](docs/08-learning/README.md)).

## Placeholders

Formato único: nombre en mayúsculas con guiones bajos entre corchetes (p. ej., `[PROJECT_NAME]`). Un placeholder nuevo usa el mismo formato y se registra aquí. No inventar valores: sin dato confirmado, el placeholder permanece. En patrones de ID, `XXX` es el número secuencial (`ADR-XXX`, `INC-XXX`, `TD-XXX`).

| Level | Placeholders | Replaced by |
|---|---|---|
| Project | `[PROJECT_NAME]`, `[PROJECT_DESCRIPTION]`, `[OWNER]`, `[PROJECT_PROFILE]`, `[TEMPLATE_VERSION]`, `[HARNESS_ROOT]` | [bootstrap-project](skills/bootstrap-project/SKILL.md) o [adopt-existing-project](skills/adopt-existing-project/SKILL.md) |
| Work | `[WORK_ID]`, `[WORK_TYPE]`, `[SLUG]`, `[FEATURE_NAME]`, `[APPROVER]`, `[DATE]`, `[SYSTEM_NAME]`, `[COMPONENT_NAME]`, `[WORK_TITLE]`, `[DESCRIPTION]`, `[JOURNEY_NAME]`, `[DECISION_TITLE]`, `[INCIDENT_TITLE]` | Al crear cada spec, plan o work item |

Los templates (`_template/`, `_template.md`) conservan todos sus placeholders, incluidos los de nivel proyecto, y se completan al copiarse.

| Placeholder | Meaning |
|---|---|
| `[PROJECT_NAME]` | Nombre del proyecto derivado |
| `[PROJECT_DESCRIPTION]` | Descripción breve del proyecto |
| `[OWNER]` | Rol responsable del documento o del trabajo |
| `[APPROVER]` | Rol que aprueba |
| `[DATE]` | Fecha `YYYY-MM-DD` |
| `[WORK_ID]` | ID del work item (`FEAT-001`, `BUG-001`, …) |
| `[WORK_TYPE]` | Work Type del trabajo |
| `[SLUG]` | Nombre corto en kebab-case para carpetas y archivos |
| `[FEATURE_NAME]` | Nombre de la feature |
| `[SYSTEM_NAME]` | Nombre del sistema propio o externo |
| `[COMPONENT_NAME]` | Nombre de un componente |
| `[TEMPLATE_VERSION]` | Contenido de `VERSION` al crear el proyecto |
| `[PROJECT_PROFILE]` | `LITE`, `STANDARD` o `CRITICAL` |
| `[HARNESS_ROOT]` | Harness Root: carpeta que contiene la documentación de la metodología (el `docs/` de la plantilla) cuando no puede ocupar `docs/`; si existe, toda ruta `docs/...` se lee desde ella |
| `[WORK_TITLE]` | Título del work item |
| `[DESCRIPTION]` | Descripción breve en títulos o filas de ejemplo |
| `[JOURNEY_NAME]` | Nombre de un user journey |
| `[DECISION_TITLE]` | Título de un ADR |
| `[INCIDENT_TITLE]` | Título de un incidente |
