---
name: clarify-spec
description: Ejecuta la etapa CLARIFY. Resuelve con el humano las Open Questions de una spec y registra respuestas y cambios en la propia spec hasta dejarla lista para aprobación.
---

# Purpose

Eliminar ambigüedades críticas antes de aprobar una spec, garantizando que toda respuesta humana quede en el repositorio y no solo en la conversación.

# When to Use

- Spec en `Draft` o `Clarification` con `Open Questions`.
- Antes de solicitar la aprobación del [Spec Gate](../../docs/00-governance/quality-gates.md#spec-gate).

# Inputs

- `spec.md` con la tabla `Open Questions`.
- Stakeholders y aprobadores definidos en [stakeholders.md](../../docs/01-discovery/stakeholders.md).

# Process

1. Listar preguntas `Open`, priorizando las `Critical`.
2. Reformular cada pregunta como decisión cerrada, con opciones e impacto de cada una.
3. Consultar al humano responsable según la `Approval Matrix`.
4. Registrar cada respuesta en `Clarifications Log` (`Answered By`, `Date`, `Spec Changes`).
5. Actualizar las secciones afectadas de la spec, AC, examples y edge cases.
6. Marcar la pregunta como `Answered`.
7. Sin preguntas `Critical` abiertas: solicitar aprobación y registrar `Approved by:` y `Date:`; `Status: Approved`.

# Outputs

- Spec actualizada, `Clarifications Log` completo y, si corresponde, spec en `Approved`.

# Validation

- Ninguna respuesta existe solo en la conversación.
- Cada respuesta indica qué secciones de la spec cambió.

# Failure Conditions

- El humano no responde: la spec permanece en `Clarification`; no se avanza.
- Respuestas contradictorias entre stakeholders: escalar al aprobador definido.
