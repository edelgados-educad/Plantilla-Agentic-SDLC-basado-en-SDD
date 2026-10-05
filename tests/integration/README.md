# Integration Tests

Pruebas de interacción entre componentes y con dependencias reales o dobles controlados ([test-strategy.md](../../docs/06-quality/test-strategy.md)).

- **Pertenece aquí:** persistencia, mensajería, integraciones externas y sus escenarios de fallo (timeouts, reintentos, fallback).
- **No pertenece aquí:** lógica aislada (`unit/`) ni compatibilidad de contratos (`contract/`).
- Usar entornos y datos sintéticos; nunca credenciales ni datos de producción.
