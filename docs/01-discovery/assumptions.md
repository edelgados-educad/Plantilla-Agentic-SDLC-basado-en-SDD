# Assumptions

Status: Draft · Owner: [OWNER]

Supuestos aceptados temporalmente como verdaderos. Un supuesto no es una regla de negocio: si se valida y define comportamiento, se promueve a [business-rules.md](../02-product/business-rules.md).

| Assumption | Risk if False | Planned Validation | Validation Owner | Status |
|---|---|---|---|---|

Estados: `Unvalidated`, `Validated`, `Invalidated`.

- Un supuesto `Invalidated` obliga a revisar las specs y planes que dependen de él.
- Los supuestos `Unvalidated` se revisan en cada Discovery Gate y Plan Gate.
