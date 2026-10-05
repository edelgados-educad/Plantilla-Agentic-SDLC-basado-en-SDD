# Constitution

**Covers:** reglas obligatorias para humanos y agentes en todo Project Profile y Work Type; Human-in-the-loop y Source of Truth (ubicación canónica).
**Delegates:** criterios que guían decisiones a [engineering-principles.md](engineering-principles.md); reglas verificables de arquitectura a [architecture-rules.md](../06-quality/architecture-rules.md); condiciones de avance a [quality-gates.md](quality-gates.md).

Agnóstica de lenguaje, framework, cloud y proveedor de IA. Aplica en todos los [Project Profiles](work-types.md#project-profiles): ningún perfil permite omitir una regla obligatoria.

## Engineering Principles

Las decisiones técnicas se guían por principios: simplicidad, bajo acoplamiento, alta cohesión, cambios pequeños y reversibles, verificación determinista y automatización.
Los principios orientan; las reglas de esta Constitution obligan. Ante conflicto, prevalece la Constitution.
Definición y aplicación de cada principio: [engineering-principles.md](engineering-principles.md).

## Architecture Principles

- No romper contratos públicos silenciosamente: los cambios incompatibles requieren análisis, versionado y aprobación humana.
- Toda integración externa debe contemplar fallos (timeout, reintentos, fallback) y poder observarse.
- Los cambios arquitectónicos relevantes requieren ADR ([adr/index.md](../04-architecture/adr/index.md)).
- Las dependencias entre componentes respetan las permitidas en [components.md](../04-architecture/components.md).
- Estos principios se concretan en reglas verificables en [architecture-rules.md](../06-quality/architecture-rules.md).

## Security Principles

- Nunca almacenar secretos en código ni en documentación.
- Mínimo privilegio y defensa en profundidad en todo componente e integración.
- Los datos sensibles se clasifican y protegen según [security.md](../04-architecture/security.md) y la normativa de protección de datos aplicable.
- Todo cambio que active un Security Review trigger ([work-types.md](work-types.md#applicability-triggers)) pasa por revisión de seguridad.

## Quality Principles

- Si una regla puede verificarse automáticamente, preferir la verificación automática sobre la instrucción escrita.
- Spec, implementación, tests y documentación deben converger ([Convergence](quality-gates.md#convergence)).
- Ningún trabajo avanza con un Quality Gate bloqueado ni se declara terminado fuera de la [Definition of Done](definition-of-done.md).

## Testing Principles

- Toda nueva funcionalidad requiere pruebas adecuadas, derivadas de sus Acceptance Criteria.
- Nunca deshabilitar, omitir ni debilitar tests para hacer pasar CI.
- Todo defecto corregido incluye un regression test que falla antes de la corrección.
- Tipos de prueba y cuándo aplican: [test-strategy.md](../06-quality/test-strategy.md).

## Observability Principles

- La observabilidad se diseña junto con la funcionalidad, no después del release.
- Toda integración externa y todo flujo crítico deben poder observarse.
- Nunca registrar datos sensibles prohibidos por [security.md](../04-architecture/security.md).
- Detalle operativo: [observability.md](../07-operations/observability.md).

## Documentation Principles

- Las decisiones significativas deben vivir en el repositorio (spec, ADR o `decisions.md`).
- Cada concepto tiene una única ubicación canónica; los demás documentos lo resumen en una línea y lo enlazan.
- La documentación se actualiza en el mismo trabajo que cambia el comportamiento.
- Progressive disclosure: documentos de entrada cortos que enlazan al detalle.

## Dependency Management

- No introducir dependencias sin justificación registrada: necesidad, alternativas evaluadas, licencia, mantenimiento y seguridad.
- Agregar o actualizar dependencias activa Security Review.
- Preferir capacidades existentes del proyecto antes que una dependencia nueva.

## AI Agent Principles

- Los agentes consumen el repositorio; la metodología nunca depende de información que solo exista en una conversación con un modelo.
- No inventar reglas de negocio: toda regla tiene fuente humana o documental; si no, queda como `Open Question`.
- Ante ambigüedad crítica, escalar al humano en lugar de suponer.
- Nunca ocultar fallos, tests fallidos ni riesgos no resueltos.
- Cada agente actúa dentro de su rol definido en `agents/` (mapa en [AGENTS.md](../../AGENTS.md)).

## Human Approval Rules

Requieren aprobación humana explícita, registrada en el artefacto correspondiente:

- transición de spec a `Approved`;
- requirements críticos;
- cambios arquitectónicos relevantes;
- contratos públicos incompatibles;
- cambios destructivos;
- seguridad crítica;
- operaciones de producción;
- aceptación de riesgos importantes;
- elección inicial del Project Profile y cualquier bajada de perfil;
- marcar `N/A` una etapa con applicability triggers activos, o Security Review / Architecture en perfil `CRITICAL` ([work-types.md](work-types.md#applicability-triggers));
- Constitution amendments;
- cambios relevantes al harness;
- activación del Emergency Path ([work-types.md](work-types.md#emergency-change-procedure)).

El objetivo del Human-in-the-loop no es controlar cada acción, sino concentrar el juicio humano donde aporta mayor valor.

## Source of Truth

Todo el conocimiento relevante vive en el repositorio: intención, especificaciones, reglas de negocio, arquitectura, decisiones, planes, tareas, restricciones, pruebas, evaluaciones, documentación operacional, aprendizajes y reglas para agentes. Una respuesta humana dada en una conversación se registra en el artefacto correspondiente antes de usarse.

Precedencia ante conflicto:

```text
Constitution
↓
Product Rules
↓
Feature Specifications
↓
Architecture Decisions
↓
Implementation Plans
↓
Tasks
↓
Code
```

- Si el código contradice una spec aprobada, no asumir que el código es correcto: investigar la divergencia.
- En brownfield, ante comportamiento no documentado: registrarlo en [current-state.md](../01-discovery/current-state.md), identificar su origen, escalar al humano y decidir si se convierte en regla.

## Change Management

- No implementar features sin especificación aprobada, salvo [Emergency Path](work-types.md#emergency-change-procedure).
- Todo trabajo se clasifica con un Work Type y se registra en [05-plans/index.md](../05-plans/index.md).
- Ninguna etapa se omite silenciosamente: la applicability se justifica en `plan.md` o `change-record.md`.
- Los cambios son pequeños, reversibles y trazables ([IDs and Traceability](../../README.md#ids-and-traceability)).

## Production Safety

- Las operaciones destructivas en producción requieren aprobación humana.
- Todo release tiene rollback definido ([rollback.md](../07-operations/rollback.md)).
- Ningún agente opera producción sin autorización humana explícita para esa operación.
- El Emergency Path no puede utilizarse para evitar deliberadamente el proceso normal.

## Amendments

La Constitution solo se modifica con propuesta explícita, razón, impacto y aprobación humana, a través del [Harness Change Gate](quality-gates.md#harness-change-gate). En proyectos derivados, el cambio se registra mediante ADR o en el changelog del proyecto, nunca alterando `VERSION` de la plantilla ([Template Versioning](../../README.md#template-versioning)).

| Date | Change | Reason | Impact | Approved By | Reference |
|---|---|---|---|---|---|
