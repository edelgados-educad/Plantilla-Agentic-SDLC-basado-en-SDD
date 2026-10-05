# Unit Tests

Pruebas de lógica aislada y determinista ([test-strategy.md](../../docs/06-quality/test-strategy.md)).

- **Pertenece aquí:** tests rápidos sin red, disco ni reloj real; dependencias externas sustituidas por dobles.
- **No pertenece aquí:** pruebas con dependencias reales (`integration/`), contratos (`contract/`) ni reglas de arquitectura (`architecture/`).
- Cada test identifica el AC que verifica con su ID completo, según [acceptance-tests.md](../../docs/06-quality/acceptance-tests.md).
