# Variables y expresiones del flujo

## Variables principales

- `varCreated`
- `varUpdated`
- `varMarkedMissing`
- `varProcessedAgents`
- `varErrors`
- `varRunStartTime`
- `varDebugLog`

## Expresiones clave

- detección de proveedor de modelo;
- detección de modelo normalizado;
- cálculo de actividad y uso;
- comparación material de cambios;
- construcción del detalle de cambios para el correo;
- cálculo de presentación de fechas y duración en el correo HTML.

## Criterio operativo

La versión actual evita comparar fechas y blobs JSON como criterio de update para reducir falsos positivos. El estado activo o inactivo se recalcula en cada sincronización según presencia real en el origen.
