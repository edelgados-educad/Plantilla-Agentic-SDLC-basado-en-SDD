---
name: review-feature
description: Ejecuta REVIEW y apoya CONVERGENCE. Revisa calidad, arquitectura, seguridad y suficiencia de pruebas, verifica justificaciones N/A y registra hallazgos con severidad.
---

# Purpose

Decidir con evidencia si un cambio puede avanzar, dejando hallazgos accionables y la verificación de convergencia en el repositorio.

# When to Use

- Tareas en `REVIEW` con el [Verification Gate](../../docs/00-governance/quality-gates.md#verification-gate) aprobado.
- Cualquier Work Type que incluya `review.md`.

# Inputs

- Cambio a revisar, `tasks.md` y evidencia de sensores.
- Spec, `plan.md` o `change-record.md` y `traceability.md`.
- [architecture-rules.md](../../docs/06-quality/architecture-rules.md) y [security-checks.md](../../docs/06-quality/security-checks.md).

# Process

1. Confirmar que el Verification Gate está aprobado.
2. Revisar correctness, readability, maintainability, consistency, architecture compliance, duplication, unnecessary complexity y test sufficiency.
3. Si la Security Review aplica, ejecutarla según [agents/security.md](../../agents/security.md).
4. Re-evaluar cada `N/A` de la Lifecycle Applicability contra el cambio real.
5. Registrar hallazgos en `review.md` con severidad, ubicación y recomendación.
6. Completar `Definition of Done Check`.
7. Comprobar [Convergence](../../docs/00-governance/quality-gates.md#convergence) entre spec, implementación, tests y documentación.
8. Registrar la decisión: `Approved` o `Changes Requested`.

# Outputs

- `review.md` completo y decisión registrada.

# Validation

- Sin `BLOCKER` ni `HIGH` en `Open` cuando la decisión es `Approved`.
- Todo hallazgo tiene ubicación y recomendación.

# Failure Conditions

- Falta evidencia de verificación: `Changes Requested`.
- Divergencia sin intención válida determinable: escalar al humano.
