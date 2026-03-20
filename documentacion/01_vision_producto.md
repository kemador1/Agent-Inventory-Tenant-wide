# Visión de producto

## Propósito

La solución mantiene un inventario tenant-wide de agentes de Copilot Studio en Dataverse y deja trazabilidad operativa de cada sincronización.

## Qué hace esta versión

- descubre agentes `microsoft.copilotstudio/agents`;
- crea o actualiza registros de inventario en Dataverse;
- gestiona ausencias sin borrado duro y prevé inactivación tras ausencias consecutivas;
- informa por correo en español con detalle de cambios reales;
- permite personalizar el branding del correo mediante variable de entorno.

## Qué no hace esta versión

- no ejecuta un flujo separado de enriquecimiento;
- no calcula scoring de gobierno automático;
- no inventa telemetría no soportada por Microsoft para BizChat/Copilot Chat.
