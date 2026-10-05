---
name: create-spec
description: Crea una feature spec desde la plantilla para un FEATURE o un CHANGE grande, con requirements verificables, acceptance criteria trazables y preguntas abiertas explícitas.
---

# Purpose

Traducir intención aprobada en una especificación verificable que sirva de fuente de verdad para arquitectura, plan, implementación y pruebas.

# When to Use

- Etapa FEATURE SPEC de un `FEATURE`.
- `CHANGE` grande que requiere spec nueva ([Artifacts by Work Type](../../docs/00-governance/work-types.md#artifacts-by-work-type)).

# Inputs

- Work item clasificado (`[WORK_ID]`) en [05-plans/index.md](../../docs/05-plans/index.md).
- [product-spec.md](../../docs/02-product/product-spec.md), [business-rules.md](../../docs/02-product/business-rules.md) y [non-functional-requirements.md](../../docs/02-product/non-functional-requirements.md).
- Journeys, glosario y respuestas humanas registradas.
- Referencias relevantes de [docs/references/](../../docs/references/README.md) (p. ej., mockups), citadas por su `REF-XXX` en FR, AC o `References`.

# Process

1. Copiar [docs/03-specs/_template/](../../docs/03-specs/_template/spec.md) a `docs/03-specs/[WORK_ID]-[SLUG]/`.
2. Completar metadatos; `Status: Draft`.
3. Redactar Context, Problem, Objective y Scope enlazando product docs, sin copiarlos.
4. Redactar FR verificables con `Source`; reglas propias como `BR-XXX` y globales solo enlazadas.
5. Describir User Flow, Alternative Flows y Error Scenarios.
6. Redactar AC con `Covers:` y `Verification Type:`; completar `examples.md` y `edge-cases.md`.
7. Completar Contracts, Security, Privacy, Observability y NFR aplicables.
8. Registrar cada vacío o ambigüedad como `Open Question` con su criticidad.
9. Agregar la fila en [03-specs/index.md](../../docs/03-specs/index.md); si hay preguntas abiertas, pasar a `Clarification`.
10. Inicializar `traceability.md` con las filas FR → AC.

# Outputs

- Carpeta de spec completa y fila en el índice de specs.

# Validation

- Sin términos vagos en FR; todo FR con AC; toda regla con fuente.
- Perfil `LITE`: al menos las secciones de [LITE Minimum Spec](../../docs/00-governance/work-types.md#lite-minimum-spec).

# Failure Conditions

- Regla sin fuente: no se inventa, se registra como `Open Question`.
- Reglas o requirements en conflicto: escalar al humano.
