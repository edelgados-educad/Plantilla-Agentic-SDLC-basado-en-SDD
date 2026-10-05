# Definition of Done

**Covers:** condiciones para declarar un trabajo terminado (Work Done), listo para release (Release Ready) y listo para producción (Production Ready).
**Delegates:** condiciones para avanzar entre etapas a [quality-gates.md](quality-gates.md).

Aplica a cualquier Work Type y Project Profile. Un punto que no aplica se marca `N/A` con justificación breve, coherente con la Lifecycle Applicability de `plan.md` / `change-record.md` y con los valores por defecto del perfil ([Profile Requirements](work-types.md#profile-requirements)).

El resultado se registra en la sección `Definition of Done Check` de `review.md` (en `findings.md` para `SPIKE`).

## Work Done

- [ ] Specification satisfied (o FR/AC afectados verificados, para tipos sin spec)
- [ ] Acceptance Criteria verified
- [ ] Unit tests passing
- [ ] Integration tests passing
- [ ] Contract tests passing when applicable
- [ ] Evals passing when applicable
- [ ] Architecture rules passing
- [ ] Security checks passing
- [ ] Performance budgets respected
- [ ] Observability implemented
- [ ] Documentation updated
- [ ] ADR created/updated when applicable
- [ ] No secrets introduced
- [ ] No unexplained dependencies
- [ ] No unresolved critical risks
- [ ] No open `BLOCKER` or `HIGH`
- [ ] Traceability complete
- [ ] Convergence Gate passed

## Release Ready

- [ ] Work Done satisfied
- [ ] Deployment criteria satisfied ([deployment.md](../07-operations/deployment.md))
- [ ] Rollback defined ([rollback.md](../07-operations/rollback.md))
- [ ] Release risks evaluated
- [ ] Human approval recorded

## Production Ready

- [ ] Release Ready satisfied
- [ ] Observability verified ([observability.md](../07-operations/observability.md))
- [ ] SLOs defined ([slo.md](../07-operations/slo.md))
- [ ] Runbook updated ([runbook.md](../07-operations/runbook.md))
- [ ] Alerts configured when applicable
