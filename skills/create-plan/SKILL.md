---
name: create-plan
description: Ejecuta CLASSIFY, IMPLEMENTATION PLAN y TASK DAG. Selecciona artefactos según Project Profile y Work Type, evalúa applicability triggers y construye tareas trazables con dependencias.
---

# Purpose

Convertir un trabajo clasificado en un plan ejecutable, con applicability justificada y un Task DAG trazable a FR/AC.

# When to Use

- Todo trabajo nuevo de cualquier Work Type, excepto `PROJECT`.
- Cambios de alcance que requieren replanificar.

# Inputs

- `Project Profile` del README y [work-types.md](../../docs/00-governance/work-types.md).
- Spec aprobada o FR/AC existentes afectados.
- Documentos de arquitectura, ADR y [test-strategy.md](../../docs/06-quality/test-strategy.md).

# Process

1. Evaluar los profile escalation triggers; si alguno aplica, escalar antes de continuar.
2. Clasificar el Work Type, asignar `[WORK_ID]` y agregar la fila en [05-plans/index.md](../../docs/05-plans/index.md).
3. Copiar de [_template/](../../docs/05-plans/_template/plan.md) solo los archivos de [Artifacts by Work Type](../../docs/00-governance/work-types.md#artifacts-by-work-type).
4. Completar `Lifecycle Applicability` partiendo de los valores del perfil y evaluando Security Review 1–8, Architecture 1–5 y Contracts 1–3.
5. Registrar en cada `N/A` los triggers evaluados y el motivo; escalar todo `N/A` con triggers activos.
6. Completar las demás secciones de `plan.md` y `risks.md`.
7. Crear tareas con `Covers:` y `Verified by:`; construir `dependencies.md` y `Parallel Groups`.
8. Solicitar el Plan Gate y el Implementation Gate.

# Outputs

- Carpeta del trabajo en `docs/05-plans/active/[WORK_ID]-[SLUG]/` y fila en el índice.

# Validation

- Lifecycle Applicability resuelta según sus [reglas](../../docs/00-governance/work-types.md#lifecycle-applicability); todo AC cubierto por al menos una tarea.
- DAG sin ciclos; tareas paralelas sin archivos compartidos o con coordinación registrada.
- Rollback definido cuando aplica.

# Failure Conditions

- Spec requerida no aprobada: detenerse.
- Trigger de aplicación incierta: tratarlo como aplicable.
