# App, dashboards y reportes

## App model-driven

- Nombre visible: `KYN Agent Inventory tenant-wide APP`
- Finalidad: consulta controlada del inventario, acceso a dashboards, vistas, notas e informe clásico

## Navegación funcional

La app publica al menos:

- dashboard operativo;
- acceso a la entidad de agentes;
- dashboards ejecutivos;
- reporte clásico asociado a la tabla;
- recurso HTML de bienvenida incluido en la solución.

## Vistas

Las vistas principales se apoyan en campos operativos y analíticos como:

- `kyn_displayname`
- `kyn_owneremail`
- `kyn_creatoremail`
- `kyn_originnormalized`
- `kyn_modelprovider`
- `kyn_lastsyncstatus`
- `kyn_activityindicator`
- `kyn_lastpublishedat`

Existen además vistas específicas para agentes recientes, agentes inactivos y vistas de trabajo del usuario.

## Dashboards

### Dashboard clásico

Orientado a seguimiento operativo:

- conteo total;
- distribución por proveedor de modelo;
- distribución por origen;
- evolución temporal.

### Dashboard ejecutivo

Orientado a responsables y gobierno:

- lectura rápida del inventario;
- foco en situación actual del tenant;
- apoyo a comités o reporting periódico.

## Reporte clásico

La release candidate incluye un reporte clásico ligado directamente a `kyn_agenttenantwide`. Este reporte permite:

- ejecución desde la tabla;
- exportación tabular;
- agrupación por origen y proveedor;
- lectura ejecutiva del inventario.

El archivo empaquetado del reporte es un `.wdl` clásico y debe considerarse parte activa de la solución.

## Web resources incluidos

La `2.2.0.3` incorpora estos recursos web:

- `kyn_Bienvenida_Agent_Inventory`
- `kyn_dashboard`
- `kyn_chatgpt_icon`
- `kyn_claude_ai_icon`
- `kyn_copilot_icon`
- `kyn_copilo_ticon`
- `kyn_kyn_agent_model_icon`
- `kyn_kyn_agent_model_icon_host`

Estos recursos sirven para experiencia visual, bienvenida e iconografía.

Nota de calidad técnica: en esta candidata conviven `kyn_copilot_icon` y `kyn_copilo_ticon`. Conviene revisar si la duplicidad es intencional o un artefacto de evolución de iconos.

## Lectura correcta de los indicadores

- `lastSyncStatus` refleja visibilidad operativa en la última ejecución;
- `Activo` no significa validado funcionalmente, solo observado;
- `Inactivo` no implica borrado confirmado, solo ausencia en la sincronización actual;
- `usageIndicator` y `activityIndicator` son indicadores operativos derivados, no telemetría soportada de BizChat por agente.
