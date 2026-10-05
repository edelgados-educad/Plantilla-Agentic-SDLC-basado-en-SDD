# [WORK_ID] — Dependencies

Task DAG del trabajo. `A → B`: B requiere A en `DONE`. `A + B → C`: C requiere ambas. El grafo no puede tener ciclos.

```text
T001 → T002
T001 → T003
T002 + T003 → T004
```

## Parallel Groups

Tareas sin dependencias entre sí que pueden ejecutarse en paralelo.

- Group A: T002, T003

No paralelizar tareas que modifican los mismos archivos (`Files Expected to Change`) salvo coordinación explícita registrada abajo.

## Coordination Notes

| Group | Shared Files | Coordination |
|---|---|---|
