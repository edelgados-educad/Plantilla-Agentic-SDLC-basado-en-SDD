# Glossary

**Covers:** términos técnicos y de la metodología usados en esta plantilla, con una definición breve.
**Delegates:** la definición completa de cada concepto a su ubicación canónica (enlazada en el término); los términos de negocio y técnicos propios de cada proyecto a [docs/01-discovery/glossary.md](docs/01-discovery/glossary.md).

Los términos se mantienen en inglés, tal como aparecen en la plantilla; las definiciones, en español. Dentro de cada sección, el orden es alfabético, salvo las etapas del lifecycle, que siguen su secuencia. Las etapas se escriben en MAYÚSCULAS para distinguirlas del documento o concepto homónimo (p. ej., la etapa `RELEASE` frente a una Release).

## Methodology Foundations

| Term | Definition |
|---|---|
| Adapter | Archivo de configuración específico de una herramienta de IA que traduce `AGENTS.md` a su formato. Trabajo futuro: la plantilla no incluye ninguno. |
| Agent | Sistema de IA que lee el repositorio y ejecuta tareas dentro de un rol definido en `agents/`. |
| Agentic SDLC | Ciclo de vida de desarrollo de software en el que agentes de IA ejecutan etapas bajo reglas, gates y aprobación humana. |
| Architecture as Code | Arquitectura, reglas y diagramas mantenidos como texto versionado y verificable en el repositorio. |
| Brownfield | Proyecto que ya tiene código o sistemas en operación. Se adopta con [adopt-existing-project](skills/adopt-existing-project/SKILL.md). |
| Canonical Location | Único documento donde se define un concepto; los demás lo resumen en una línea y lo enlazan. |
| Coding Agent | Herramienta que ejecuta un modelo de IA sobre el repositorio (arnés de programación). La plantilla no depende de ninguna en particular. |
| Context Engineering | Diseño de qué información recibe un agente, cuándo y en qué forma, para que actúe con el contexto mínimo suficiente. |
| Continuous Learning | Mejora continua del proceso a partir de incidentes, retrospectivas y fallos repetidos. |
| Derived Project | Proyecto creado a partir de la plantilla. |
| Diagram as Code | Diagrama escrito como texto versionado en lugar de imagen. |
| [Feedback Flywheel](docs/08-learning/README.md) | Ciclo que convierte cada incidente o fallo repetido en una mejora del harness, no solo del código. |
| Greenfield | Proyecto nuevo, sin código previo. Se inicia con [bootstrap-project](skills/bootstrap-project/SKILL.md). |
| Harness | Conjunto de reglas, gates, sensores, skills, agentes y plantillas que guía y verifica el trabajo de humanos y agentes. |
| Harness Engineering | Disciplina de diseñar y mejorar el harness para que el software producido sea correcto, trazable y verificable. |
| [Harness Root](README.md#placeholders) | Carpeta que contiene la documentación de la metodología cuando no puede ocupar `docs/` (p. ej., `docs/harness`). |
| [Human-in-the-loop](docs/00-governance/constitution.md#human-approval-rules) | Principio de concentrar la aprobación humana en las decisiones de mayor impacto. |
| Mechanisms over Documentation | Preferir estructuras verificables (IDs, campos obligatorios, estados, checklists) a instrucciones en prosa. |
| Multi-agent Workflow | Trabajo repartido entre agentes con roles distintos, coordinados por el Orchestrator. |
| [Placeholder](README.md#placeholders) | Marcador en mayúsculas entre corchetes (p. ej., `[PROJECT_NAME]`) que se reemplaza por un valor real. Tiene nivel proyecto o trabajo. |
| Progressive Disclosure | Entregar primero lo esencial y enlazar al detalle, para reducir el contexto que se lee. |
| Provider-agnostic | Independiente de cualquier proveedor o herramienta de IA. |
| Skill | Procedimiento reutilizable (`skills/*/SKILL.md`) que un agente ejecuta paso a paso. |
| [Source of Truth](docs/00-governance/constitution.md#source-of-truth) | El repositorio como única fuente válida de intención, decisiones y reglas; nada vale si solo existe en una conversación. |
| Spec-Driven Development (SDD) | Enfoque en el que una especificación aprobada precede y gobierna la implementación. |
| Template | La plantilla completa, o un archivo o carpeta `_template` que se copia para crear un artefacto nuevo. |
| Template Repository | Repositorio de GitHub marcado como plantilla; habilita el botón "Use this template". |

## Lifecycle Stages

| Term | Definition |
|---|---|
| [Lifecycle](README.md#lifecycle) | Secuencia canónica de 20 etapas, de IDEA a HARNESS IMPROVEMENT; cada trabajo recorre solo las que le aplican. |
| Stage | Etapa del lifecycle, con artefacto, gate y rol responsable. |
| `IDEA` | Etapa: registro inicial de una necesidad o problema. |
| `CLASSIFY` | Etapa: asignación de Work Type, ID y Lifecycle Applicability; al crear el proyecto, elección del Project Profile. |
| `ASSESS` | Etapa: evaluación del estado actual, las restricciones o el impacto antes de cambiar. |
| `CONSTITUTION` | Etapa: revisión de las reglas obligatorias de la Constitution aplicables al proyecto. |
| `DISCOVERY` | Etapa: comprensión del problema, objetivos, stakeholders, alcance y restricciones (`docs/01-discovery/`). |
| `PRODUCT SPEC` | Etapa: definición de visión, capacidades, reglas de negocio y NFR del producto (`docs/02-product/`). |
| `FEATURE SPEC` | Etapa: especificación verificable de una funcionalidad (`docs/03-specs/[WORK_ID]-[SLUG]/`). |
| `CLARIFY` | Etapa: resolución con el humano de las preguntas abiertas de una spec. |
| `ARCHITECTURE` | Etapa: análisis del impacto arquitectónico y registro de decisiones (ADR). |
| `CONTRACTS` | Etapa: definición de interfaces públicas o entre componentes. |
| `IMPLEMENTATION PLAN` | Etapa: plan del trabajo en `plan.md` (enfoque, applicability, riesgos, pruebas, despliegue y rollback). |
| `TASK DAG` | Etapa: descomposición del trabajo en tareas con dependencias, como grafo dirigido sin ciclos (Directed Acyclic Graph), en `tasks.md` y `dependencies.md`. |
| `AGENT EXECUTION` | Etapa: implementación de las tareas `READY` con sus pruebas. |
| `FEEDBACK SENSORS` | Etapa: ejecución de las verificaciones automáticas. |
| `REVIEW` | Etapa: revisión de calidad y seguridad, con hallazgos registrados. |
| `CONVERGENCE` | Etapa: comprobación de Convergence antes de cerrar el trabajo. |
| `RELEASE` | Etapa: paso a producción con rollback definido y aprobación humana. |
| `OBSERVABILITY` | Etapa: verificación del comportamiento en producción mediante métricas, SLO y alertas. |
| `LEARNING` | Etapa: registro de incidentes, lecciones y deuda técnica. |
| `HARNESS IMPROVEMENT` | Etapa: cambios al harness derivados del aprendizaje. |

## Gates and Completion

| Term | Definition |
|---|---|
| Blocking Condition | Situación que impide pasar un gate. |
| [Convergence](docs/00-governance/quality-gates.md#convergence) | Estado en que spec, implementación, tests, documentación y comportamiento observado coinciden; sin él, el trabajo no está terminado. |
| [Definition of Done](docs/00-governance/definition-of-done.md) | Condiciones para declarar un trabajo terminado, en tres niveles: Work Done, Release Ready y Production Ready. |
| Entry Criteria | Condiciones que deben cumplirse para evaluar un gate. |
| Evidence | Artefacto del repositorio que demuestra que un gate se cumplió. |
| Production Ready | Nivel de la Definition of Done: Release Ready más observabilidad verificada, SLO, runbook y alertas. |
| [Quality Gate](docs/00-governance/quality-gates.md) | Punto de control con criterios de entrada, condiciones de bloqueo, aprobador y evidencia. Hay 15, de Assessment Gate a Harness Change Gate. |
| Release Ready | Nivel de la Definition of Done: Work Done más rollback definido, riesgos de release evaluados y aprobación humana. |
| Work Done | Nivel de la Definition of Done: requisitos verificados, pruebas en verde, documentación y trazabilidad completas. |

## Governance and Work Types

| Term | Definition |
|---|---|
| Amendment | Modificación formal de la Constitution, con propuesta, razón, impacto y aprobación humana. |
| [Applicability Trigger](docs/00-governance/work-types.md#applicability-triggers) | Condición que obliga a ejecutar Security Review, Architecture o Contracts en un trabajo. |
| Approver | Rol humano que aprueba una decisión o un artefacto. |
| [Constitution](docs/00-governance/constitution.md) | Reglas obligatorias para humanos y agentes en todo perfil y tipo de trabajo. |
| Document Status | Línea `Status:` al inicio de los documentos de proyecto: `Draft`, `Approved` o `N/A`. |
| [Emergency Path](docs/00-governance/work-types.md#emergency-change-procedure) | Emergency Change Procedure: flujo excepcional y aprobado para un `HOTFIX` ante un incidente crítico. |
| [Engineering Principles](docs/00-governance/engineering-principles.md) | Criterios que orientan decisiones técnicas; a diferencia de la Constitution, no son obligatorios. |
| Escalation | Elevar una decisión al humano cuando supera la autoridad del agente. |
| [Lifecycle Applicability](docs/00-governance/work-types.md#lifecycle-applicability) | Decisión, por trabajo y por etapa, de si la etapa se ejecuta; se registra en `plan.md` o `change-record.md`. |
| `N/A` | No aplica; siempre con justificación. |
| Owner | Rol responsable de un documento o de un trabajo. |
| Post-incident Completion | Documentación, pruebas, trazabilidad y análisis que se completan después de un hotfix. |
| Profile Escalation Trigger | Evento que obliga a proponer un perfil más alto (p. ej., empezar a procesar datos personales). |
| [Project Profile](docs/00-governance/work-types.md#project-profiles) | Nivel base de rigor del proyecto, elegido una vez: `LITE`, `STANDARD` o `CRITICAL`. |
| `CRITICAL` | Perfil para datos personales o regulados, pagos o sistemas de alto impacto; exige controles reforzados. |
| `LITE` | Perfil para scripts, prototipos y herramientas internas sin datos personales ni usuarios externos. |
| `STANDARD` | Perfil por defecto para aplicaciones de negocio típicas. |
| Slug | Nombre corto en kebab-case usado en carpetas y archivos (p. ej., `busqueda-cursos`). |
| Work ID | Identificador de un work item (p. ej., `FEAT-001`); placeholder `[WORK_ID]`. |
| Work Item | Unidad de trabajo registrada en `docs/05-plans/index.md` con un ID único. |
| [Work Type](docs/00-governance/work-types.md#work-types) | Clasificación de cada trabajo; define su ID, sus artefactos y su flujo. |
| `BUG` | Work Type: corrección de un defecto. |
| `CHANGE` (`CHG`) | Work Type: cambio a un comportamiento existente. |
| `DOCUMENTATION` (`DOC`) | Work Type: cambio exclusivamente documental. |
| `FEATURE` (`FEAT`) | Work Type: nueva capacidad funcional. |
| `HOTFIX` (`HOT`) | Work Type: corrección urgente en producción mediante el Emergency Path. |
| `PROJECT` | Work Type: nuevo producto o sistema; inicializa el repositorio. |
| `REFACTOR` (`REF`) | Work Type: cambio interno que no altera el comportamiento esperado. |
| `SPIKE` (`SPK`) | Work Type: investigación o experimento; su código no pasa a producción sin un work item propio. |
| `TECH_DEBT` (`TD`) | Work Type: mejora técnica planificada. |

## Specification and Traceability

| Term | Definition |
|---|---|
| Acceptance Criterion (AC) | Condición verificable que demuestra que un FR se cumple; incluye `Covers:` y `Verification Type:`. |
| Actor | Persona, rol o sistema que interactúa con la funcionalidad. |
| Alternative Flow | Camino válido distinto del flujo principal. |
| Assumption | Hecho aceptado temporalmente como verdadero, pendiente de validar. |
| Business Rule (BR) | Regla de negocio con fuente verificable; global (`BR-001`) o propia de una feature. |
| Change History | Registro, en la spec, de los trabajos `CHANGE` que la modificaron. |
| Clarifications Log | Registro, en la spec, de las preguntas respondidas por humanos y de su efecto en la spec. |
| Constraint | Restricción no negociable que limita las soluciones posibles. |
| Contract | Definición de una interfaz (API, evento, mensaje o schema) entre productor y consumidor. |
| Contract-First | Definir y aprobar el contrato antes de implementarlo. |
| Covers | Campo que indica qué FR o AC cubre un AC o una tarea. |
| Current State | Descripción del sistema real observado antes de cambiarlo. |
| Edge Case | Caso límite con comportamiento esperado definido. |
| Error Scenario | Situación de fallo y respuesta esperada del sistema. |
| Example | Par de entrada y salida esperada que puede convertirse en test o eval. |
| Functional Requirement (FR) | Comportamiento verificable que el sistema debe tener. |
| Given / When / Then | Formato de AC: contexto inicial, acción y resultado esperado. |
| [IDs](README.md#ids-and-traceability) | Identificadores con formato fijo (`FR-001`, `AC-001`, `ADR-001`, …); entre documentos se usa la forma completa (`FEAT-001/AC-001`). |
| Implicit Rule | Comportamiento no documentado observado en un sistema existente; requiere confirmación humana antes de ser regla. |
| Incompatible Change | Cambio que rompe a los consumidores actuales de un contrato (breaking change). |
| KPI | Key Performance Indicator: indicador clave para medir el éxito de un objetivo. |
| Non-functional Requirement (NFR) | Requisito de calidad (performance, seguridad, disponibilidad, etc.) con métrica, umbral y método de verificación. |
| Open Question | Duda registrada en la spec (`Q-001`); las críticas deben responderse antes de aprobarla. |
| Precondition | Condición que debe cumplirse antes del flujo principal. |
| Scope | Alcance del proyecto: In Scope, Out of Scope y Future Scope. |
| Stakeholder | Persona o rol con interés o influencia en el proyecto. |
| Traceability | Cadena verificable que une cada requisito con su criterio de aceptación, su tarea y su test o eval. |
| Traceability Matrix | Tabla de `traceability.md` con columnas FR, AC, Task, Test/Eval y Status. |
| User Flow | Secuencia de pasos observables del flujo principal de una feature. |
| User Journey | Recorrido de un actor para lograr un objetivo, con sus pain points. |
| Verification Type | Forma de verificar un AC: `unit`, `integration`, `contract`, `e2e`, `eval` o `manual`. |
| Verified by | Campo de una tarea con la ruta del test o eval que la demuestra. |

## Architecture and Security

| Term | Definition |
|---|---|
| Architecture Decision Record (ADR) | Documento que registra una decisión arquitectónica, sus alternativas y sus consecuencias ([índice](docs/04-architecture/adr/index.md)). |
| Architecture Rule (AR) | Regla arquitectónica verificable (`AR-001`), idealmente automatizada ([reglas](docs/06-quality/architecture-rules.md)). |
| Attack Surface | Conjunto de puntos de entrada por los que el sistema puede ser atacado. |
| Circuit Breaker | Mecanismo que corta temporalmente las llamadas a una dependencia que falla, para evitar fallos en cascada. |
| Component | Unidad interna de un contenedor con una responsabilidad clara. |
| Container | Unidad desplegable o de almacenamiento: aplicación, API, worker, base de datos o cola. |
| Data Classification | Nivel de sensibilidad de un dato: `Public`, `Internal`, `Confidential` o `Restricted`. |
| Data Model | Entidades, relaciones, componente dueño y ciclo de vida de los datos. |
| Defense in Depth | Varias capas de control de seguridad, para que la falla de una no comprometa el sistema. |
| [Dependency Inversion](docs/00-governance/engineering-principles.md#dependency-inversion) | La lógica de negocio depende de interfaces propias, no de detalles de infraestructura. |
| Deployable Unit | Artefacto que se despliega de forma independiente. |
| Encryption at Rest / in Transit | Cifrado de los datos almacenados / de los datos que viajan por la red. |
| Environment | Entorno de ejecución: `DEV`, `QA`, `STAGING` o `PRODUCTION`. |
| Fallback | Comportamiento alternativo cuando una dependencia no está disponible. |
| [High Cohesion](docs/00-governance/engineering-principles.md#high-cohesion) | Cada componente agrupa responsabilidades relacionadas. |
| Idempotency | Propiedad de una operación que produce el mismo resultado aunque se repita. |
| Infrastructure as Code (IaC) | Infraestructura definida como código versionado, en la carpeta `infra/`. |
| Injection | Ataque que introduce comandos o consultas maliciosas a través de entradas no validadas. |
| Integration | Conexión con un sistema externo, con su protocolo, autenticación y manejo de fallos. |
| Least Privilege | Otorgar solo los permisos mínimos necesarios. |
| Ley 29733 | Ley de Protección de Datos Personales del Perú; ejemplo de normativa aplicable al tratamiento de datos personales. |
| Logging Leakage | Exposición de datos sensibles o secretos en los logs. |
| [Loose Coupling](docs/00-governance/engineering-principles.md#loose-coupling) | Un componente puede cambiar sin forzar cambios en otros. |
| Masking | Ocultar parcialmente un dato sensible, por ejemplo al registrarlo en logs. |
| Permitted Dependency | Dependencia autorizada entre componentes; lo no listado está prohibido. |
| Personal Data | Dato que identifica o hace identificable a una persona. |
| Prompt Injection | Ataque que manipula las instrucciones de un componente de IA mediante entradas maliciosas. |
| Rate Limit | Límite de solicitudes permitidas en un período. |
| Retry / Backoff | Reintento de una operación fallida, con espera creciente entre intentos. |
| [Reversibility](docs/00-governance/engineering-principles.md#reversible-decisions) | Facilidad y costo de revertir una decisión; sección obligatoria de todo ADR. |
| Secret | Credencial, token o clave; nunca se guarda en código ni en documentación. |
| Secrets Manager | Servicio que almacena y entrega secretos de forma controlada. |
| Sensitive Data | Dato personal, regulado o confidencial que requiere protección especial. |
| System Context | Vista de más alto nivel: actores, sistemas externos y límites del sistema. |
| Threat Analysis | Identificación de amenazas sobre la superficie modificada y de sus controles. |
| Timeout | Tiempo máximo de espera de una operación antes de considerarla fallida. |
| Trust Boundary | Límite entre zonas con distinto nivel de confianza (p. ej., internet y red interna). |

## Planning and Execution

| Term | Definition |
|---|---|
| Agent Role | Rol con responsabilidades y restricciones definidas en `agents/`. Hay siete. |
| [Analyst](agents/analyst.md) | Rol que convierte intención en discovery, product docs y specs verificables. |
| [Architect](agents/architect.md) | Rol que analiza el impacto arquitectónico, define contratos y redacta ADR. |
| [Implementer](agents/implementer.md) | Rol que implementa tareas `READY` con sus pruebas. |
| [Orchestrator](agents/orchestrator.md) | Rol que coordina el lifecycle: clasifica, planifica, ejecuta gates y comprueba convergencia. |
| [Reviewer](agents/reviewer.md) | Rol que revisa calidad, arquitectura, convergencia y justificaciones `N/A`. |
| [Security](agents/security.md) | Rol que evalúa amenazas y controles de seguridad y privacidad. |
| [Tester](agents/tester.md) | Rol que verifica con postura adversarial y actualiza la trazabilidad. |
| Change Record | Registro (`change-record.md`) de un trabajo `BUG`, `HOTFIX`, `REFACTOR`, `TECH_DEBT` o `DOCUMENTATION`. |
| Decision Log | Registro (`decisions.md`) de las decisiones tomadas durante un trabajo. |
| Findings | Resultado documentado de un `SPIKE` (`findings.md`). |
| Parallel Group | Tareas sin dependencias entre sí que pueden ejecutarse en paralelo. |
| Progress | Estado operativo de un trabajo (`progress.md`), suficiente para retomarlo sin la conversación original. |
| Risk | Riesgo de un trabajo (`R001`) con probabilidad, impacto, mitigación y estado. |
| Task | Unidad ejecutable de un plan (`T001`), con objetivo, cobertura y verificación. |
| Task Status | Estado de una tarea: `TODO`, `READY`, `IN_PROGRESS`, `BLOCKED`, `REVIEW` o `DONE`. |

## Quality and Verification

| Term | Definition |
|---|---|
| AI Eval | Eval de componentes de IA: exactitud, fidelidad a fuentes, seguridad, sesgo, latencia y costo. |
| Architecture Test | Test que verifica automáticamente una regla `AR`. |
| Blocking Sensor | Sensor cuya falla detiene el avance del trabajo. |
| Compiler | Herramienta que traduce el código y detecta errores antes de ejecutarlo. |
| Continuous Integration (CI) | Ejecución automática de build y verificaciones en cada cambio integrado. |
| Contract Test | Test que verifica la compatibilidad entre productor y consumidor de un contrato. |
| Coverage | Proporción del código o de los requisitos que ejercitan las pruebas. |
| Dataset | Conjunto versionado de casos usado por un eval. |
| [Deterministic Verification](docs/00-governance/engineering-principles.md#deterministic-verification) | Verificación que da el mismo resultado con la misma entrada. |
| End-to-End Test (e2e) | Prueba de un recorrido completo del usuario a través del sistema. |
| [Eval](evals/README.md) | Evaluación de calidad mediante datasets, scoring y umbrales, para comportamiento no binario. |
| [Feedback Sensor](docs/06-quality/feedback-sensors.md) | Verificación automática que entrega una señal objetiva (pass/fail o métrica) sobre un cambio. |
| Flaky Test | Test inestable que pasa o falla sin cambios en el código. |
| Formatter | Herramienta que aplica automáticamente el estilo de formato del código. |
| Integration Test | Prueba de la interacción entre componentes o con dependencias. |
| Latency | Tiempo de respuesta de una operación. |
| Linter | Herramienta que detecta errores probables y malas prácticas en el código. |
| Pass Threshold | Umbral mínimo que debe alcanzar un eval para aprobar. |
| Performance Budget | Límite medible de rendimiento derivado de un NFR. |
| Performance Test | Prueba que mide tiempos, throughput o consumo bajo carga. |
| Quality Score | Evaluación periódica por dimensiones, en escala de 0 a 3, del estado del producto y del harness. |
| Regression Test | Prueba que evita que un defecto corregido reaparezca. |
| Review Finding | Hallazgo de una revisión (`RV-001`) con severidad, ubicación y recomendación. |
| Scoring Method | Métrica o rúbrica con la que se califica un eval. |
| Security Checks | Checklist operacional de verificaciones de seguridad (`docs/06-quality/security-checks.md`). |
| Security Review | Revisión de seguridad obligatoria cuando aplica algún trigger de seguridad. |
| Security Scanning | Análisis automático de vulnerabilidades en el código y sus dependencias. |
| Severity | Gravedad de un hallazgo de revisión: `BLOCKER`, `HIGH`, `MEDIUM`, `LOW` o `SUGGESTION`. |
| Smoke Test | Verificación rápida de que lo esencial funciona tras un despliegue. |
| Test Double | Sustituto controlado de una dependencia real en una prueba (mock, stub o fake). |
| Test Strategy | Tipos de prueba del proyecto, cuándo son obligatorios y dónde viven. |
| Throughput | Cantidad de operaciones procesadas por unidad de tiempo. |
| Type Checker | Herramienta que verifica la consistencia de tipos sin ejecutar el código. |
| Unit Test | Prueba rápida y aislada de una unidad de lógica. |

## Operations and Learning

| Term | Definition |
|---|---|
| Alert | Notificación automática cuando una métrica cruza un umbral; enlaza a su runbook. |
| Blameless | Análisis de incidentes centrado en hechos y sistemas, no en culpables. |
| Business Metric | Métrica del resultado de negocio (p. ej., inscripciones completadas). |
| Correlation ID | Identificador que une los logs y trazas de una misma solicitud. |
| Deployment | Proceso de instalar una versión en un entorno. |
| Error Budget | Margen de fallo tolerado por un SLO; al agotarse, se prioriza la confiabilidad sobre nuevas features. |
| Feature Flag | Interruptor que activa una funcionalidad de forma progresiva sin desplegar de nuevo. |
| Five Whys | Técnica de causa raíz que pregunta "¿por qué?" de forma sucesiva. |
| Harness Gap | Carencia del harness que permitió un incidente o un defecto. |
| Incident | Evento no planificado que afecta el servicio (`INC-001`), con severidad `CRITICAL`, `HIGH`, `MEDIUM` o `LOW`. |
| Lesson Learned | Aprendizaje consolidado, con enlace a su origen y al cambio de harness que lo aplica. |
| Log | Registro estructurado de eventos del sistema. |
| Metric | Medición numérica del sistema a lo largo del tiempo. |
| Migration | Cambio controlado de datos, esquema o configuración entre versiones. |
| Observability | Capacidad de entender el estado interno del sistema a partir de logs, métricas y trazas. |
| Release | Versión del sistema puesta a disposición en producción. |
| Retrospective | Revisión periódica de qué funcionó, qué no y qué mejorar en el harness. |
| Rollback | Reversión a la versión anterior ante un fallo. |
| Root Cause Analysis (RCA) | Análisis para encontrar la causa raíz técnica y de proceso de un incidente. |
| RPO | Recovery Point Objective: pérdida máxima de datos tolerable ante un fallo. |
| RTO | Recovery Time Objective: tiempo máximo tolerable para recuperar el servicio. |
| Runbook | Procedimiento operativo ante síntomas conocidos: diagnóstico, acción y escalamiento. |
| Sampling | Registro de solo una fracción de las trazas, para controlar costo y volumen. |
| SLI | Service Level Indicator: métrica que mide un aspecto del servicio (p. ej., porcentaje de solicitudes exitosas). |
| SLO | Service Level Objective: valor objetivo de un SLI en una ventana de tiempo. |
| [Tech Debt](docs/08-learning/tech-debt.md) | Deuda técnica: atajo o carencia que encarece los cambios futuros; se registra como `TD-001`. |
| Trace | Recorrido de una solicitud a través de componentes e integraciones. |

## Versioning and Tooling

| Term | Definition |
|---|---|
| Annotated Tag | Tag de git con mensaje y autor; marca las versiones de la plantilla (p. ej., `v1.1.1`). |
| Branch | Línea de desarrollo en git; la principal es `main`. |
| Changelog | Historial de cambios por versión (`CHANGELOG.md`). |
| CLI | Command Line Interface: interfaz de línea de comandos. |
| Commit | Registro de un conjunto de cambios en git, con autor y mensaje. |
| Force Push | Reescritura del historial remoto; requiere aprobación y, de preferencia, `--force-with-lease`. |
| Frontmatter | Bloque de metadatos al inicio de un Markdown; en las skills contiene `name` y `description`. |
| Git | Sistema de control de versiones distribuido. |
| kebab-case | Formato en minúsculas separado por guiones (p. ej., `create-spec`). |
| Markdown | Formato de texto plano con marcas simples; formato de toda la documentación. |
| Push | Envío de commits y tags locales al repositorio remoto. |
| Remote | Repositorio remoto asociado al local (p. ej., `origin` en GitHub). |
| [Semantic Versioning](README.md#template-versioning) | Versionado `MAJOR.MINOR.PATCH` según el tipo de cambio. |
| [Template Version](README.md#template-versioning) | Versión de la plantilla de la que proviene un proyecto, registrada en su README. |
| UPPER_SNAKE_CASE | Formato en mayúsculas separado por guiones bajos; formato de los placeholders. |
| WCAG | Web Content Accessibility Guidelines: pautas de accesibilidad web, referencia típica para NFR de accesibilidad. |
