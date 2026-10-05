# [WORK_ID] — Acceptance Criteria

Cada AC es verificable e incluye `Covers:` (FR que cubre) y `Verification Type:` (`unit`, `integration`, `contract`, `e2e`, `eval`, `manual`). Usar Given / When / Then cuando aporte claridad. En referencias entre documentos usar la forma completa `[WORK_ID]/AC-001`.

## Rules

- Todo FR tiene al menos un AC; un AC sin `Covers:` es inválido.
- `manual` exige justificar por qué no se automatiza y se registra como candidato en [tech-debt.md](../../08-learning/tech-debt.md).
- Un AC se considera verificado solo con evidencia ejecutada, registrada en [traceability.md](traceability.md).
- Conversión de AC en tests ejecutables: [acceptance-tests.md](../../06-quality/acceptance-tests.md).

## AC-001 — [DESCRIPTION]

- **Covers:** FR-001
- **Verification Type:** unit
- **Given** el contexto inicial observable
- **When** la acción del actor o el evento
- **Then** el resultado esperado y verificable
