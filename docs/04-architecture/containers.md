# Containers

Status: Draft · Owner: [OWNER]

Unidades desplegables o de almacenamiento de [SYSTEM_NAME]. La tecnología de cada contenedor se decide y justifica mediante ADR.

| Container | Type | Responsibility | Technology | ADR | Owner |
|---|---|---|---|---|---|

Valores de `Type`: `Application`, `API`, `Worker`, `Storage`, `Database`, `Queue`, `External Service`.

## Communication

| From | To | Purpose | Protocol | Sync/Async | Contract |
|---|---|---|---|---|---|

Toda comunicación con un `External Service` se detalla en [integrations.md](integrations.md).
