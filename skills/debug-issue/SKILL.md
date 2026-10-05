---
name: debug-issue
description: Diagnostica y corrige defectos (BUG o HOTFIX) partiendo de una reproducción, con causa raíz documentada, regression test y evaluación final del Feedback Flywheel.
---

# Purpose

Corregir defectos por su causa raíz, con evidencia reproducible, y mejorar el harness para que el defecto no reaparezca.

# When to Use

- Trabajos `BUG` o `HOTFIX`.
- Fallos de sensores o tests cuya causa no es evidente.

# Inputs

- Reporte del defecto o incidente (`INC-XXX`).
- FR/AC existentes afectados, logs, métricas y trazas ([observability.md](../../docs/07-operations/observability.md)).
- `change-record.md` del trabajo.

# Process

1. Reproducir el defecto con un test que falle; si no es posible, documentar la evidencia disponible.
2. Identificar los FR/AC afectados y registrarlos en `change-record.md`.
3. Formular hipótesis y verificarlas con evidencia, una a la vez.
4. Documentar la causa raíz.
5. `HOTFIX`: seguir el [Emergency Change Procedure](../../docs/00-governance/work-types.md#emergency-change-procedure).
6. Aplicar la corrección mínima; el regression test debe fallar antes y pasar después.
7. Ejecutar los feedback sensors y registrar la verificación.
8. Evaluar si el defecto revela una carencia del harness según el [Feedback Flywheel](../../docs/08-learning/README.md); registrar incidente, lección, tech debt o propuesta de cambio de harness.

# Outputs

- Corrección con regression test, `change-record.md` completo y resultado de la evaluación del Feedback Flywheel.

# Validation

- Existe un regression test vinculado a los FR/AC afectados.
- La causa raíz está documentada y el Feedback Flywheel fue evaluado.

# Failure Conditions

- No se puede reproducir: registrar lo investigado y escalar.
- La causa raíz está fuera del alcance del trabajo: crear un nuevo work item.
