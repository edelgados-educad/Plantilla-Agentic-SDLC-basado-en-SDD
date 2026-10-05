---
name: assess-codebase
description: Ejecuta la etapa ASSESS. Construye con evidencia el estado actual (brownfield), las restricciones (greenfield) o el impacto de un trabajo sobre el sistema existente.
---

# Purpose

Obtener una visión verificable del sistema y sus restricciones antes de especificar, planificar o cambiar, priorizando la evidencia del sistema sobre la documentación existente.

# When to Use

- Adopción de la plantilla en un repositorio existente (brownfield) o inicio de un `PROJECT` (greenfield).
- ASSESS de `CHANGE`, `BUG`, `REFACTOR`, `TECH_DEBT` y `SPIKE` ([Default Lifecycle by Work Type](../../docs/00-governance/work-types.md#default-lifecycle-by-work-type)).

# Inputs

- Código, configuración, pipelines y resultados de pruebas existentes.
- Documentación previa (a contrastar, no a asumir como cierta).
- [constraints.md](../../docs/01-discovery/constraints.md) y respuestas humanas registradas.

# Process

1. Inventariar sistemas, componentes e integraciones a partir del código y la configuración.
2. Reconstruir la arquitectura observada en [current-state.md](../../docs/01-discovery/current-state.md) y, si aplica, en `docs/04-architecture/`, marcando lo no verificado.
3. Registrar comportamiento no documentado en `Implicit Rules` y escalarlo al humano ([Source of Truth](../../docs/00-governance/constitution.md#source-of-truth)).
4. Evaluar pruebas y cobertura de los flujos críticos.
5. Inventariar los sensores en [feedback-sensors.md](../../docs/06-quality/feedback-sensors.md) (`Available`, `Command/Location`, `Blocking`).
6. Registrar deuda accionable en [tech-debt.md](../../docs/08-learning/tech-debt.md) y riesgos base.
7. Brownfield o `PROJECT`: proponer el Project Profile evaluando los [profile escalation triggers](../../docs/00-governance/work-types.md#profile-escalation-triggers).
8. Trabajo puntual: identificar componentes y FR/AC afectados, y riesgo del cambio.

# Outputs

- `current-state.md` y `constraints.md` actualizados.
- Inventario de feedback sensors, ítems de tech debt y riesgos base.
- Propuesta de Project Profile o análisis de impacto del trabajo.

# Validation

- Toda afirmación tiene evidencia (ruta, comando, log o resultado).
- Se cumplen los criterios del [Assessment Gate](../../docs/00-governance/quality-gates.md#assessment-gate).

# Failure Conditions

- Sin acceso al código o a los sensores: registrar como desconocido y escalar.
- Documentación que contradice el código: registrar la divergencia sin asumir cuál es correcta y escalar.
