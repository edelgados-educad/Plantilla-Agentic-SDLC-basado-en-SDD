# Non-functional Requirements

Status: Draft · Owner: [OWNER]

Requisitos de calidad globales. Todo NFR tiene métrica, umbral y método de verificación; sin ellos no es verificable. Los NFR de performance se desglosan en [performance-budgets.md](../06-quality/performance-budgets.md).

| ID | Category | Requirement | Metric | Threshold | Verification Method | Status |
|---|---|---|---|---|---|---|
| NFR-001 | Performance | [DESCRIPTION] | | | | Proposed |

Estados: `Proposed`, `Active`, `Deprecated`.

## Categories

| Category | Guiding Question |
|---|---|
| Performance | ¿Qué tiempo de respuesta o throughput se requiere y bajo qué carga? |
| Availability | ¿Qué disponibilidad se exige y en qué horario? |
| Scalability | ¿Qué crecimiento de usuarios o datos se espera? |
| Security | ¿Qué controles son obligatorios (autenticación, cifrado, auditoría)? |
| Privacy | ¿Qué datos personales se tratan, con qué finalidad y retención? |
| Observability | ¿Qué debe poder medirse, trazarse y alertarse? |
| Maintainability | ¿Qué estándares de código y documentación aplican? |
| Resilience | ¿Cómo debe comportarse ante fallos de dependencias? ¿Qué RTO y RPO aplican? |
| Accessibility | ¿Qué nivel de accesibilidad se exige (p. ej., WCAG 2.2 AA)? |
| Compliance | ¿Qué normas o auditorías debe superar? |
| Cost | ¿Qué límite de costo operativo aplica? |
