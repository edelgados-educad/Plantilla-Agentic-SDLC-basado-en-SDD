# Evals

**Covers:** organización y formato mínimo de evals. Estrategia general de verificación en [test-strategy.md](../docs/06-quality/test-strategy.md).

- **Tests** (`tests/`): validan principalmente comportamiento determinista.
- **Evals** (`evals/`): validan calidad o comportamiento mediante datasets, scoring, tolerancias, evaluación semántica o métricas.

| Folder | Purpose |
|---|---|
| [functional/](functional/README.md) | Calidad funcional medible con datasets |
| [regression/](regression/README.md) | Casos de defectos e incidentes pasados que no deben reaparecer |
| [security/](security/README.md) | Casos adversariales: abuso, inyección y fuga de datos |
| [ai/](ai/README.md) | Calidad de componentes de IA; `N/A` si el producto no incluye IA |

## Minimum Eval Format

Un archivo por eval dentro de su carpeta, nombrado `[WORK_ID]-[SLUG].md`:

```markdown
# [WORK_ID] — [DESCRIPTION]
## Objective
## Related FR/AC
## Dataset/Cases
## Scoring Method
## Pass Threshold
## Results
```

| Field | Content |
|---|---|
| Objective | Qué calidad se mide y por qué |
| Related FR/AC | IDs en forma completa (p. ej., `FEAT-001/AC-003`) |
| Dataset/Cases | Ubicación y descripción; datos sintéticos o anonimizados |
| Scoring Method | Métrica o rúbrica y cómo se calcula |
| Pass Threshold | Umbral explícito y tolerancia |
| Results | Fecha, versión evaluada, resultado y evidencia |

## Rules

- Un eval sin umbral explícito no es verificable.
- Los datasets se versionan y nunca contienen datos personales reales ni secretos.
- Los evals bloqueantes se registran como sensor en [feedback-sensors.md](../docs/06-quality/feedback-sensors.md).
- Los resultados se referencian en `traceability.md` de la spec.
