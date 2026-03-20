# App, dashboards y reportes

## App model-driven

- Nombre visible: `KYN Agent Inventory tenant-wide APP`
- Finalidad: ofrecer una experiencia simple de consulta, análisis, filtrado y notas sobre el inventario

## Navegación

La app incluye dos entradas principales:

- `Dashboard`
- `Agents`

La app se entrega sin iconografía SVG personalizada para evitar errores de importación entre tenants. Si se desea branding visual, los iconos pueden cargarse manualmente después de la importación.

## Vistas

Las vistas principales muestran, además del dato base:

- `kyn_originnormalized`
- `kyn_modelprovider`
- `kyn_owneremail`
- `kyn_creatoremail`
- `kyn_lastsyncstatus`
- `kyn_activityindicator`
- `kyn_lastpublishedat`
- `statecode`

## Dashboards

### Dashboard clásico

Pensado para supervisión operativa:

- conteo de agentes;
- distribución por origen normalizado;
- distribución por proveedor de modelo;
- evolución temporal.

### Dashboard ejecutivo

Pensado para consumo de responsables:

- foco en visibilidad rápida;
- lectura de tendencia;
- revisión del inventario activo.

## Reporte ejecutivo

- Nombre: `KYN Agent Inventory Executive Report`
- Contenido reforzado:
  - origen normalizado,
  - proveedor de modelo,
  - owner email,
  - sync status,
  - fecha de última publicación,
  - actividad operativa.

## Uso recomendado del reporting

- dashboard para seguimiento continuo;
- reporte para exportación y comité;
- vistas para trabajo analítico y revisión manual.

## Lectura correcta de los indicadores

- `activityIndicator` y `usageIndicator` no equivalen a uso real de BizChat por agente;
- `Activo` significa observado en la sincronización actual;
- `Inactivo` significa no observado en la sincronización actual, no borrado confirmado del tenant.
