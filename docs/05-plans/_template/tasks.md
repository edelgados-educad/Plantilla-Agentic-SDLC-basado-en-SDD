# [WORK_ID] — Tasks

Estados: `TODO`, `READY`, `IN_PROGRESS`, `BLOCKED`, `REVIEW`, `DONE`. Una tarea pasa a `READY` solo cuando todas sus dependencias están en `DONE`; el Implementer solo toma tareas `READY`. `Covers` usa la forma completa de los IDs (p. ej., `FEAT-001/FR-001`). Copiar la sección por tarea.

## T001 — [DESCRIPTION]

| Field | Value |
|---|---|
| Objective | Resultado único y verificable de la tarea. |
| Owner Role | Implementer |
| Covers | `[WORK_ID]/FR-001`, `[WORK_ID]/AC-001` (o FR/AC existentes afectados) |
| Inputs | Spec, contratos, ADR o archivos necesarios. |
| Outputs | Código, tests o documentos producidos. |
| Dependencies | — |
| Files Expected to Change | |
| Validation | Sensores y checks a ejecutar antes de pasar a `REVIEW`. |
| Verified by | Ruta del test o eval que demuestra la tarea. |
| Status | TODO |
