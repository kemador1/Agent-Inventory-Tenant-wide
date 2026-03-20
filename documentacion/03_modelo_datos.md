# Modelo de datos

## Tabla principal

- Nombre lógico: `kyn_agenttenantwide`
- Función: inventario consolidado de agentes

## Clave y unicidad

- Clave alterna: `kyn_AgentEnvironmentKey`
- Campos: `kyn_agentid`, `kyn_environmentid`

## Campos usados por el flujo actual

### Identidad

- `kyn_name`
- `kyn_agentid`
- `kyn_displayname`
- `kyn_environmentid`
- `kyn_tenantid`
- `kyn_resourceid`
- `kyn_resourcetype`

### Procedencia y contexto

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

### Estado operativo

- `kyn_createdat`
- `kyn_lastpublishedat`
- `kyn_isquarantined`
- `kyn_activityindicator`
- `kyn_usageindicator`

### Sincronización

- `kyn_lastsyncstatus`
- `kyn_cleanupdecision`
- `kyn_lastseenon`
- `kyn_missingcounter`

Estos campos soportan el criterio operativo de ausencia consecutiva:

- primera ausencia: registro no visto en la ejecución;
- ausencias repetidas: candidato a inactivación;
- sin borrado físico automático.

## Campos legacy u opcionales

La tabla conserva algunos campos de gobierno creados en versiones anteriores para compatibilidad, pero no forman parte de la lógica principal de esta versión.
