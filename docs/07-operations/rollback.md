# Rollback

Status: Draft · Owner: [OWNER]

Cómo revertir un release de forma segura. Todo release tiene rollback definido antes del Release Gate.

## Triggers

Condiciones que obligan a revertir (p. ej., SLO incumplido, error crítico, smoke test fallido).

## Strategy by Change Type

| Change Type | Strategy | Max Time to Rollback | Notes |
|---|---|---|---|
| Código de aplicación | | | |
| Configuración | | | |
| Migración de datos | | | |
| Infraestructura | | | |
| Contrato público | | | |

## Procedure

1. Paso de rollback con su pipeline o comando.

## Data Considerations

Cómo se preservan o reconcilian los datos escritos después del release. Las operaciones destructivas requieren aprobación humana.

## Verification

Cómo confirmar que el sistema volvió al estado previo.

## Rollback Log

| Date | Release | Reason | Executed By | Result | Incident |
|---|---|---|---|---|---|
