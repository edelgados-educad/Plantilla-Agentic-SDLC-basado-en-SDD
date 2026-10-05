# Observability

Status: Draft · Owner: [OWNER]

Cómo se observa [SYSTEM_NAME] en operación. Toda integración externa debe poder observarse. Nunca registrar datos sensibles prohibidos por [security.md](../04-architecture/security.md).

## Logs

Formato estructurado, niveles, identificador de correlación, retención y campos prohibidos.

## Metrics

| Metric | Type | Source | Related NFR/SLO |
|---|---|---|---|

## Traces

Propagación de contexto entre componentes e integraciones, y política de muestreo.

## Errors

Captura, agrupación y vínculo de errores con incidentes.

## Business Metrics

| Metric | Definition | Related KPI |
|---|---|---|

## Alerts

| Alert | Condition | Severity | Notify | Runbook |
|---|---|---|---|---|

`Severity` usa los valores de incidentes ([incident template](../08-learning/incidents/_template.md)). Toda alerta enlaza una entrada de [runbook.md](runbook.md).

## Integration Coverage

| Integration | Logs | Metrics | Alerts |
|---|---|---|---|
