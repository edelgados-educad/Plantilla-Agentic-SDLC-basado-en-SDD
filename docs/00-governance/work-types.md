# Project Profiles and Work Types

**Covers (canonical):** Project Profiles, profile escalation triggers, Work Types, IDs por tipo, artefactos por tipo, lifecycle por defecto, Lifecycle Applicability, Applicability Triggers y Emergency Change Procedure.
**Delegates:** lifecycle canónico a [README.md](../../README.md#lifecycle); condiciones de cada gate a [quality-gates.md](quality-gates.md).

Dos niveles de ajuste:

- **Project Profile:** se elige una vez por proyecto y define el nivel base de rigor.
- **Work Type:** se elige por cada trabajo y define el flujo de ese trabajo dentro del perfil.

## Project Profiles

| Profile | When to Use | Base Rigor |
|---|---|---|
| `LITE` | Scripts, automatizaciones puntuales, prototipos, herramientas internas sin datos personales o regulados y sin usuarios externos | Mínimo viable: intención clara, spec simplificada, verificación automática disponible |
| `STANDARD` | Aplicaciones de negocio típicas | Lo definido por defecto en esta plantilla |
| `CRITICAL` | Datos personales o regulados, pagos, sistemas de producción de alto impacto, requisitos de cumplimiento | `STANDARD` + controles reforzados |

El perfil vigente se declara en el README del proyecto (`Project Profile: [PROJECT_PROFILE]`). Lo elige el humano a propuesta del Orchestrator.

### Profile Requirements

| Element | LITE | STANDARD | CRITICAL |
|---|---|---|---|
| Discovery | Solo `problem.md` y `scope.md` | Completo | Completo |
| Product docs | `N/A` por defecto | Completo | Completo |
| Feature spec | [LITE Minimum Spec](#lite-minimum-spec) | Completa | Completa |
| Architecture docs | `N/A` por defecto, salvo triggers | Según applicability | `REQUIRED` |
| Security Review | Según triggers | Según triggers | Siempre `REQUIRED` |
| Contracts | Según triggers | Según triggers | Según triggers; cambios incompatibles con aprobación humana |
| ADR | Solo si hay decisión irreversible | Según Constitution | Según Constitution |
| Traceability | FR → AC → Test (sin columna Task) | Completa | Completa, sin excepciones salvo aprobación humana |
| Operations docs | `N/A` por defecto | Según applicability | `REQUIRED` |
| Production Ready Gate | `N/A` por defecto | Según applicability | `REQUIRED` |
| Marcar `N/A` en Security Review o Architecture | Según triggers | Según triggers | Requiere aprobación humana |

Reglas:

- El perfil fija los **valores por defecto**. Los [Applicability Triggers](#applicability-triggers) **siempre prevalecen**: si un trigger se activa en un proyecto `LITE`, la etapa es `REQUIRED`.
- La [Constitution](constitution.md) aplica en todos los perfiles. Ningún perfil permite saltarse sus reglas obligatorias (no inventar reglas de negocio, no exponer secretos, no debilitar tests).
- Los documentos de proyecto (discovery, product, architecture, quality, operations) inician con una línea `Status:` cuyo valor es `Draft`, `Approved` o `N/A (Profile [PROJECT_PROFILE])`.
- Los documentos que un perfil marca `N/A` no se borran: se mantienen con `Status: N/A (Profile [PROJECT_PROFILE])` para que los agentes los omitan sin perder la estructura si el perfil sube.

### LITE Minimum Spec

En `LITE`, la spec puede limitarse a: Work Type, Status, Owner, Context, Problem, Objective, Scope, Functional Requirements, Acceptance Criteria y Open Questions. Las demás secciones se omiten o se marcan `N/A`.

### Profile Escalation Triggers

| From → To | Triggers |
|---|---|
| `LITE` → `STANDARD` | Usuarios externos o de otras áreas; uso recurrente en procesos de negocio; integraciones con sistemas institucionales; más de un desarrollador o agente trabajando en paralelo; vida útil esperada mayor a la de un prototipo. |
| `STANDARD` → `CRITICAL` | Procesamiento de datos personales o regulados; pagos o información financiera; impacto alto ante caída; requisitos regulatorios o de auditoría; exposición pública a internet con datos sensibles. |
| `LITE` → `CRITICAL` | Cualquier trigger de `STANDARD` → `CRITICAL`. |

Reglas de cambio de perfil:

- El Orchestrator evalúa los escalation triggers en cada CLASSIFY. Si detecta uno, propone el cambio y lo escala al humano.
- **Subir** de perfil requiere registrar el motivo en un ADR y completar los artefactos faltantes antes del siguiente Release Gate.
- **Bajar** de perfil siempre requiere aprobación humana y un ADR.
- Ante la duda sobre si un trigger aplica, tratarlo como aplicable.

## Work Types

| Type | ID Prefix | Description |
|---|---|---|
| `PROJECT` | — | Nuevo producto o sistema (inicializa el repositorio completo) |
| `FEATURE` | `FEAT-001` | Nueva capacidad funcional |
| `CHANGE` | `CHG-001` | Cambio de comportamiento existente |
| `BUG` | `BUG-001` | Corrección de defecto |
| `HOTFIX` | `HOT-001` | Corrección urgente en producción |
| `REFACTOR` | `REF-001` | Cambio interno sin modificar comportamiento esperado |
| `TECH_DEBT` | `TD-001` | Mejora técnica planificada |
| `SPIKE` | `SPK-001` | Investigación, validación o experimento |
| `DOCUMENTATION` | `DOC-001` | Cambio exclusivamente documental |

- El placeholder genérico para cualquier ID de trabajo es `[WORK_ID]`. La numeración es secuencial por tipo y un ID nunca se reutiliza.
- Todo trabajo se registra en [05-plans/index.md](../05-plans/index.md) durante CLASSIFY. Los IDs `TD-XXX` se asignan desde [tech-debt.md](../08-learning/tech-debt.md).
- `PROJECT` no tiene ID ni carpeta de plan: inicializa el repositorio desde la plantilla con [bootstrap-project](../../skills/bootstrap-project/SKILL.md) y produce governance, discovery, product y los primeros work items.
- Brownfield: la adopción en un repositorio existente se hace con [adopt-existing-project](../../skills/adopt-existing-project/SKILL.md); el ASSESS inicial se limita al área afectada por el primer work item.

## Artifacts by Work Type

| Type | Spec (`03-specs/`) | Plan folder (`05-plans/active/`) |
|---|---|---|
| `FEATURE` | Spec completa nueva | `plan.md`, `tasks.md`, `dependencies.md`, `risks.md`, `progress.md`, `decisions.md`, `review.md` |
| `CHANGE` | Actualiza la spec afectada y registra en su `## Change History`; crea spec nueva solo si el cambio es grande | Igual que `FEATURE` |
| `BUG` | No crea spec; referencia FR/AC existentes | `plan.md`, `tasks.md`, `change-record.md`, `review.md` |
| `HOTFIX` | No crea spec; referencia FR/AC existentes | `change-record.md`, `review.md` (resto se completa post-incidente) |
| `REFACTOR` | No crea spec | `plan.md`, `tasks.md`, `change-record.md`, `review.md` |
| `TECH_DEBT` | No crea spec | `plan.md`, `tasks.md`, `change-record.md`, `review.md` |
| `SPIKE` | No crea spec | `plan.md`, `findings.md` |
| `DOCUMENTATION` | No crea spec | `change-record.md`, `review.md` |

- Los artefactos no listados para un tipo no se crean. Si se necesitan, el Orchestrator los agrega y lo registra en `plan.md` o `change-record.md`.
- **Spec:** copiar `docs/03-specs/_template/` a `docs/03-specs/[WORK_ID]-[SLUG]/`. Un `CHANGE` es grande cuando modifica el objetivo o el alcance de la spec existente; ante la duda, decide el humano.
- **Plan:** copiar de `docs/05-plans/_template/` solo los archivos listados a `docs/05-plans/active/[WORK_ID]-[SLUG]/`; al cerrar, mover la carpeta a `docs/05-plans/completed/`.
- `plan.md` (o `change-record.md` si no hay plan) se crea en CLASSIFY con Work Item, Work Type y Lifecycle Applicability; el resto se completa en IMPLEMENTATION PLAN.

## Default Lifecycle by Work Type

| Type | Default Flow |
|---|---|
| `PROJECT` | Lifecycle completo |
| `FEATURE` | FEATURE SPEC → CLARIFY → ARCHITECTURE → CONTRACTS → PLAN → TASK DAG → EXECUTION → SENSORS → REVIEW → CONVERGENCE → RELEASE |
| `CHANGE` | ASSESS (impacto) → actualización de spec → resto como `FEATURE` según applicability |
| `BUG` | ASSESS → PLAN → TASK DAG → FIX → REGRESSION TEST → SENSORS → REVIEW → CONVERGENCE |
| `HOTFIX` | [Emergency Change Procedure](#emergency-change-procedure) |
| `REFACTOR` | ASSESS → PLAN → TASK DAG → EXECUTION → SENSORS (con evidencia de comportamiento preservado) → REVIEW |
| `TECH_DEBT` | ASSESS (motivación, impacto, riesgo) → PLAN → TASK DAG → EXECUTION → SENSORS → REVIEW |
| `SPIKE` | ASSESS → EXPERIMENT → FINDINGS → DECISION. Nunca se convierte automáticamente en código de producción. |
| `DOCUMENTATION` | Cambio → REVIEW |

Todo trabajo inicia en CLASSIFY. Equivalencias con el lifecycle canónico: PLAN = IMPLEMENTATION PLAN; EXECUTION, FIX, REGRESSION TEST y EXPERIMENT ocurren en AGENT EXECUTION; SENSORS = FEEDBACK SENSORS; FINDINGS y DECISION se registran en `findings.md`.

## Lifecycle Applicability

| Value | Meaning |
|---|---|
| `REQUIRED` | Debe completarse |
| `CONDITIONAL` | El Orchestrator evalúa si aplica |
| `N/A` | No aplica; requiere justificación breve |

Reglas:

- La applicability vive **únicamente** en la tabla `Lifecycle Applicability` de `plan.md` (o de `change-record.md` para tipos sin plan). No se repite en la spec.
- El Orchestrator la propone durante CLASSIFY partiendo de los valores por defecto del perfil ([Profile Requirements](#profile-requirements)).
- Los [Applicability Triggers](#applicability-triggers) prevalecen sobre los valores por defecto del perfil.
- Todo `CONDITIONAL` se resuelve a `REQUIRED` o `N/A` antes del Plan Gate.
- Nunca omitir silenciosamente una etapa.

## Applicability Triggers

Las etapas **Security Review** (parte de REVIEW), **Architecture** y **Contracts** pueden marcarse `N/A` sin aprobación humana solo si el cambio **no** cumple ninguno de sus disparadores. Los disparadores están numerados para citarlos en la columna `Triggers Evaluated` (p. ej., `Security Review 1–8: ninguno activo`).

### Security Review Triggers

1. Toca autenticación, autorización, sesiones o permisos.
2. Procesa, almacena, transmite o registra datos sensibles o personales.
3. Modifica o crea interfaces expuestas (APIs, endpoints, eventos externos).
4. Agrega o actualiza dependencias.
5. Modifica manejo de secretos, configuración de seguridad o cifrado.
6. Cambia validación de entradas o construye consultas/comandos dinámicos.
7. Cruza un trust boundary definido en [security.md](../04-architecture/security.md).
8. Afecta infraestructura, despliegue o permisos de entornos.

### Architecture Triggers

1. Crea, elimina o mueve responsabilidades entre componentes o contenedores.
2. Agrega una integración externa o un nuevo tipo de almacenamiento.
3. Modifica dependencias permitidas entre componentes.
4. Cambia el modelo de datos de forma estructural.
5. Afecta requisitos no funcionales críticos (performance, availability, resilience).

### Contracts Triggers

1. Crea o modifica una interfaz pública o entre componentes.
2. Cambia schemas, formatos de datos, eventos o mensajes.
3. Introduce un cambio potencialmente incompatible para consumidores.

### Common Rules

- En perfil `CRITICAL`, Security Review y Architecture nunca son `N/A` sin aprobación humana, aunque no haya triggers activos.
- Todo `N/A` registra qué disparadores se evaluaron y por qué no aplican.
- Si algún disparador aplica, la etapa es `REQUIRED`.
- Si el agente no puede determinar si un disparador aplica, debe tratarlo como aplicable.
- El Reviewer verifica las justificaciones de `N/A` como parte del Review Gate.
- Fuera del caso `CRITICAL` anterior, la aprobación humana solo se requiere para marcar `N/A` una etapa con algún disparador activo (aceptación explícita de riesgo).

## Emergency Change Procedure

Uso exclusivo para trabajo clasificado como `HOTFIX` ante un incidente crítico.

Requisitos mínimos, registrados en `change-record.md`: aprobación humana explícita, incidente o razón documentada, alcance mínimo, riesgo identificado, rollback definido, critical tests disponibles y observabilidad posterior.

```text
CRITICAL INCIDENT
→ HUMAN APPROVAL
→ MINIMAL FIX
→ CRITICAL VERIFICATION
→ RELEASE
→ OBSERVE
→ POST-INCIDENT COMPLETION
```

Post-incident completion obligatoria: documentación faltante, actualización de spec o change record, regression tests, traceability, incident report ([incident template](../08-learning/incidents/_template.md)), root cause analysis y [Feedback Flywheel](../08-learning/README.md).

El Emergency Path no puede utilizarse para evitar deliberadamente el proceso normal. Su uso se revisa en la retrospectiva del incidente.
