# Deployment Procedure

Status: Draft · Owner: [OWNER]

**Covers:** cómo se despliega, procedimiento y verificación.
**Delegates:** qué se despliega y topología a [04-architecture/deployment.md](../04-architecture/deployment.md).

## Preconditions

- [ ] [Release Gate](../00-governance/quality-gates.md#release-gate) aprobado.
- [ ] Rollback definido ([rollback.md](rollback.md)).
- [ ] Ventana de despliegue y comunicación acordadas.
- [ ] Migraciones revisadas: reversibles o con plan de contingencia.

## Procedure

1. Paso de despliegue con su pipeline o comando.

El procedimiento se automatiza en pipelines; este documento describe el flujo, no reemplaza la automatización.

## Verification

| Check | Method | Expected Result |
|---|---|---|
| Smoke test | | |
| Salud de integraciones críticas | | |
| Métricas y alertas sin anomalías | | |

## Release Log

| Release | Date | Environment | Work Items | Approved By | Result |
|---|---|---|---|---|---|
