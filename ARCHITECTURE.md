# ARCHITECTURE.md

Mapa de la arquitectura de [SYSTEM_NAME]. Resume y enlaza (progressive disclosure); el detalle vive en `docs/04-architecture/`. Solo arquitectura real o aprobada, nunca ficticia.

## System Summary

[PROJECT_DESCRIPTION]. Describir en 3–5 líneas qué hace el sistema, para quién y sus restricciones arquitectónicas principales.

## Architecture Map

```text
Actors and External Systems      → system-context.md
        ↓
Containers (apps, APIs, workers, storage, queues) → containers.md
        ↓
Components and permitted dependencies              → components.md
        ↓
Data · Integrations · Security · Deployment        → data-model.md · integrations.md · security.md · deployment.md
```

## Architecture Documents

| Document | Read When |
|---|---|
| [system-context.md](docs/04-architecture/system-context.md) | Cambian actores, sistemas externos o boundaries |
| [containers.md](docs/04-architecture/containers.md) | Se agrega o modifica una unidad desplegable o de almacenamiento |
| [components.md](docs/04-architecture/components.md) | Se mueven responsabilidades o dependencias |
| [data-model.md](docs/04-architecture/data-model.md) | Cambia el modelo de datos o su clasificación |
| [integrations.md](docs/04-architecture/integrations.md) | Se agrega o modifica una integración externa |
| [security.md](docs/04-architecture/security.md) | Aplica algún Security Review trigger |
| [deployment.md](docs/04-architecture/deployment.md) | Cambia la topología de entornos |
| [architecture-rules.md](docs/06-quality/architecture-rules.md) | Antes de implementar: reglas verificables `AR-XXX` |

Cuándo un cambio requiere la etapa ARCHITECTURE: [Architecture Triggers](docs/00-governance/work-types.md#applicability-triggers).

## ADR Index

Decisiones registradas en [adr/index.md](docs/04-architecture/adr/index.md). Se crea un ADR para cambios arquitectónicos relevantes, decisiones irreversibles y cambios de Project Profile.

## Current Architecture Status

- **Overall:** Draft. El estado de cada documento está en su línea `Status:`.
- **Known Divergences:** diferencias entre arquitectura documentada y observada, con enlace a [current-state.md](docs/01-discovery/current-state.md) o al work item que las resuelve.
- **Pending Decisions:** ADR en `Proposed`.
- **Last Reviewed:** [DATE]
