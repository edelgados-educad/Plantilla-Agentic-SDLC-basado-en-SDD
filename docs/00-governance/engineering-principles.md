# Engineering Principles

**Covers:** criterios que guían decisiones técnicas.
**Delegates:** reglas obligatorias a [constitution.md](constitution.md); reglas verificables a [architecture-rules.md](../06-quality/architecture-rules.md).

Ante conflicto entre un principio y una regla de la Constitution, prevalece la Constitution. Cuando dos principios compiten, registrar el trade-off en `decisions.md` o en un ADR.

## Simplicity First

- **Definition:** la solución más simple que satisface la spec y los NFR.
- **Application:** rechazar abstracciones, capas o configuraciones que ningún requisito justifique.

## Explicit over Implicit

- **Definition:** comportamiento, dependencias y supuestos visibles en código y documentos.
- **Application:** evitar efectos laterales ocultos; registrar supuestos en [assumptions.md](../01-discovery/assumptions.md).

## Loose Coupling

- **Definition:** un componente puede cambiar sin forzar cambios en otros.
- **Application:** comunicar componentes mediante contratos definidos; no compartir estado interno.

## High Cohesion

- **Definition:** cada componente agrupa responsabilidades relacionadas.
- **Application:** si un concepto obliga a tocar muchos componentes, revisar la asignación de responsabilidades.

## Dependency Inversion

- **Definition:** la lógica de negocio no depende de detalles de infraestructura.
- **Application:** depender de interfaces propias; los adaptadores implementan los detalles externos.

## Contract-First When Applicable

- **Definition:** las interfaces se definen antes de implementarse.
- **Application:** con Contracts triggers activos, el contrato pasa el Contract Gate antes de AGENT EXECUTION.

## Observability by Design

- **Definition:** el sistema expone su estado interno desde el diseño.
- **Application:** cada flujo crítico define qué log, métrica o traza demuestra que funciona.

## Security by Design

- **Definition:** la seguridad se diseña desde el inicio, no se agrega al final.
- **Application:** evaluar los Security Review triggers en CLASSIFY, no recién en REVIEW.

## Testability

- **Definition:** el código se verifica de forma aislada y repetible.
- **Application:** diseñar con entradas y salidas observables; inyectar dependencias externas.

## Deterministic Verification

- **Definition:** la misma entrada produce el mismo resultado de verificación.
- **Application:** aislar tiempo, aleatoriedad y red en tests; usar evals con umbral explícito cuando el resultado no es determinista.

## Small Changes

- **Definition:** incrementos pequeños, revisables y reversibles.
- **Application:** tareas con un objetivo, archivos esperados acotados y verificación propia.

## Reversible Decisions

- **Definition:** preferir decisiones fáciles de revertir.
- **Application:** toda decisión irreversible exige ADR con sección `Reversibility` y aprobación humana.

## Progressive Disclosure of Context

- **Definition:** entregar a humanos y agentes el contexto mínimo necesario, enlazando al detalle.
- **Application:** documentos de entrada cortos ([AGENTS.md](../../AGENTS.md), [ARCHITECTURE.md](../../ARCHITECTURE.md)); el detalle vive en `docs/`.

## Automation Before Manual Repetition

- **Definition:** lo que se repite y es verificable se automatiza.
- **Application:** una verificación manual repetida se registra como candidata a feedback sensor en [tech-debt.md](../08-learning/tech-debt.md).
