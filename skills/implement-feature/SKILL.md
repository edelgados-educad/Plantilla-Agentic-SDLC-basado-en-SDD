---
name: implement-feature
description: Ejecuta AGENT EXECUTION sobre tareas READY. Implementa el cambio mínimo con sus pruebas, corre los feedback sensors y deja evidencia para retomar el trabajo.
---

# Purpose

Implementar una tarea del Task DAG respetando spec, contratos y arquitectura, con verificación automática y evidencia en el repositorio.

# When to Use

- Existe una tarea en `READY` en `tasks.md` y el [Implementation Gate](../../docs/00-governance/quality-gates.md#implementation-gate) está aprobado.

# Inputs

- Tarea `READY` y sus `Inputs`.
- Spec, AC, examples, contratos, ADR y [architecture-rules.md](../../docs/06-quality/architecture-rules.md).
- Inventario de [feedback-sensors.md](../../docs/06-quality/feedback-sensors.md).

# Process

1. Pasar la tarea a `IN_PROGRESS` y leer solo el contexto que indica.
2. Escribir o actualizar los tests de los FR/AC de `Covers` a partir de los AC y examples.
3. Implementar el cambio mínimo dentro de `Files Expected to Change`.
4. Ejecutar los sensores en el orden recomendado y corregir hasta que los bloqueantes pasen.
5. Registrar la evidencia en `progress.md` y cualquier desviación en `decisions.md`.
6. Pasar la tarea a `REVIEW`.

# Outputs

- Código y tests de la tarea, evidencia de sensores y `progress.md` actualizado.

# Validation

- Sensores bloqueantes en verde; tests de `Covers` presentes y pasando.
- Sin secretos, sin dependencias injustificadas y sin cambios fuera de alcance no registrados.

# Failure Conditions

- Ambigüedad o contradicción con la spec: detenerse y escalar.
- Cambio necesario fuera del alcance: detenerse; el Orchestrator replanifica.
- Sensor que falla por causas ajenas: registrar y escalar; nunca desactivarlo.
