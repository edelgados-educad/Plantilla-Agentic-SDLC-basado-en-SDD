# Acceptance Tests

Status: Draft · Owner: [OWNER]

Cómo los Acceptance Criteria se convierten en verificaciones ejecutables.

## Process

1. Tomar cada AC de `acceptance-criteria.md` con su `Verification Type`.
2. Derivar casos desde Given / When / Then, `examples.md` y `edge-cases.md`.
3. Implementar el test o eval en la ubicación de su tipo ([test-strategy.md](test-strategy.md)).
4. Identificar el AC en el nombre, etiqueta o metadato del test con su ID completo (p. ej., `FEAT-001/AC-001`), para permitir trazabilidad automática.
5. Ejecutar y registrar ruta y resultado en `traceability.md` de la spec.

## Mapping by Verification Type

| Verification Type | Implementation | Location |
|---|---|---|
| `unit` | Test unitario determinista | `tests/unit/` |
| `integration` | Test con dependencias reales o dobles controlados | `tests/integration/` |
| `contract` | Test de compatibilidad productor/consumidor | `tests/contract/` |
| `e2e` | Recorrido completo del journey | Definida por el proyecto |
| `eval` | Dataset, scoring y umbral | `evals/` |
| `manual` | Procedimiento documentado con evidencia | Sección `Manual Procedures` |

## Rules

- Un AC está verificado solo si su test o eval se ejecutó y pasó; nunca por inspección del código.
- Un test sin AC ni requirement relacionado se reporta en `traceability.md`.

## Manual Procedures

| AC | Steps | Expected Result | Evidence | Executed By | Date |
|---|---|---|---|---|---|
