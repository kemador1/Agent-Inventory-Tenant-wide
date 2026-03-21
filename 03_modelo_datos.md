# Modelo de datos

## Tabla principal

- Nombre lógico real: `kyn_agenttenantwide`
- Nombre funcional: inventario tenant-wide de agentes

Nota: en algunos borradores se ha referido informalmente como `yb_agenttenantwide`, pero la tabla implementada en la solución es `kyn_agenttenantwide`.

## Criterios de modelado

La tabla se diseña para cubrir cuatro necesidades:

- identidad funcional del agente;
- procedencia y contexto técnico;
- ownership y metadatos de publicación;
- estado operativo y trazabilidad de sincronización.

## Unicidad

- Clave alterna: `kyn_AgentEnvironmentKey`
- Composición: `kyn_agentid` + `kyn_environmentid`

Este criterio evita duplicados entre ejecuciones y garantiza que un mismo agente dentro del mismo entorno se sincronice sobre un único registro.

## Bloques de información

### Identidad

- `kyn_name`
- `kyn_agentid`
- `kyn_displayname`
- `kyn_environmentid`
- `kyn_tenantid`
- `kyn_resourceid`
- `kyn_resourcetype`

### Origen y contexto

- `kyn_createdin`
- `kyn_originnormalized`
- `kyn_schemaname`
- `kyn_entraappid`
- `kyn_location`

### Ownership técnico

- `kyn_createdby`
- `kyn_creatoremail`
- `kyn_creatorobjectid`
- `kyn_ownerid`
- `kyn_owneremail`
- `kyn_ownerobjectid`

### Estado y modelo

- `kyn_createdat`
- `kyn_lastpublishedat`
- `kyn_isquarantined`
- `kyn_modeljson`
- `kyn_modelnormalized`
- `kyn_modelprovider`
- `kyn_activityindicator`
- `kyn_usageindicator`

### Sincronización y ciclo de vida

- `kyn_lastsyncstatus`
- `kyn_cleanupdecision`
- `kyn_lastseenon`
- `kyn_missingcounter`
- `statecode`
- `statuscode`

## Criterio de ciclo de vida

La release candidate opera así:

- si el agente se detecta, el registro queda activo;
- si no se detecta en la sincronización actual, el registro queda inactivo;
- si reaparece, vuelve a activo;
- no hay borrado físico automático.

## Campos de gobierno presentes en esquema

Aunque el flujo principal de esta candidata no depende de todos ellos, la tabla conserva campos de gobierno y analítica para compatibilidad y evolución futura:

- `kyn_functionalowner`
- `kyn_criticality`
- `kyn_criticalitycode`
- `kyn_reviewstatus`
- `kyn_reviewstatuscode`
- `kyn_governancescore`
- `kyn_lastenrichedon`
- `kyn_telemetrysource`
- `kyn_usageevidence`
- `kyn_enrichmentsummary`

## Razones del diseño

- mantener el dato operativo separado del dato nativo de sistema;
- disponer de emails propios de owner y creator;
- evitar depender del `createdby` nativo de Dataverse como único identificador funcional;
- permitir explotación por vistas, dashboards, reporte y correo sin recalcular todo en tiempo real.
