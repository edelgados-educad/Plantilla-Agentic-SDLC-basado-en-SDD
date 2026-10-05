# Security Architecture

Status: Draft · Owner: [OWNER]

**Covers:** diseño de seguridad real de [SYSTEM_NAME].
**Delegates:** verificaciones a ejecutar a [security-checks.md](../06-quality/security-checks.md); responsabilidad y proceso del rol a [agents/security.md](../../agents/security.md).

## Authentication

¿Cómo se identifican usuarios y sistemas? ¿Qué proveedor de identidad se usa?

## Authorization

Modelo de permisos (roles, atributos, recursos) y punto donde se aplica.

## Secrets

Dónde se almacenan, quién accede y cómo se rotan. Nunca en código ni documentación.

## Encryption

Cifrado en tránsito y en reposo; gestión de claves.

## Trust Boundaries

| Boundary | From | To | Controls |
|---|---|---|---|

Cruzar un boundary activa el Security Review trigger 7 ([work-types.md](../00-governance/work-types.md#applicability-triggers)).

## Attack Surface

| Entry Point | Exposure (Public/Internal) | Authentication | Notes |
|---|---|---|---|

## Sensitive Data

Datos personales o regulados, su clasificación ([data-model.md](data-model.md)) y la normativa aplicable.

## Logging Restrictions

Datos que nunca se registran (credenciales, tokens, datos personales sin enmascarar) y reglas de enmascaramiento.
