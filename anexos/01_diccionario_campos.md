# Diccionario de campos

## Campos principales de identidad y contexto

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `kyn_name` | texto | nombre principal del registro |
| `kyn_agentid` | texto | identificador funcional del agente en origen |
| `kyn_displayname` | texto | nombre visible del agente |
| `kyn_environmentid` | texto | identificador del entorno |
| `kyn_tenantid` | texto | identificador del tenant |
| `kyn_resourceid` | texto | identificador del recurso descubierto |
| `kyn_resourcetype` | texto | tipo de recurso |
| `kyn_location` | texto | ubicación administrativa del recurso |
| `kyn_createdin` | texto | origen de creación declarado por la fuente |
| `kyn_originnormalized` | texto | origen normalizado para explotación |
| `kyn_schemaname` | texto | schema técnico asociado |
| `kyn_entraappid` | texto | identificador de aplicación Entra si existe |

## Campos de ownership técnico

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `kyn_createdby` | texto | nombre del creador técnico resuelto |
| `kyn_creatoremail` | texto | email o UPN del creador técnico |
| `kyn_creatorobjectid` | texto | object id del creador en origen |
| `kyn_ownerid` | texto | nombre del owner técnico resuelto |
| `kyn_owneremail` | texto | email o UPN del owner técnico |
| `kyn_ownerobjectid` | texto | object id del owner en origen |

## Campos de modelo y publicación

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `kyn_createdat` | fecha-hora | fecha de creación del agente en origen |
| `kyn_lastpublishedat` | fecha-hora | fecha de última publicación |
| `kyn_isquarantined` | texto / flag | indicador derivado de cuarentena |
| `kyn_modeljson` | texto largo | bloque JSON de modelo devuelto por el origen |
| `kyn_modelnormalized` | texto | modelo normalizado para explotación |
| `kyn_modelprovider` | texto | proveedor normalizado del modelo |
| `kyn_activityindicator` | texto | indicador operativo derivado |
| `kyn_usageindicator` | texto | indicador de uso derivado |

## Campos de sincronización

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `kyn_lastsyncstatus` | texto | estado observado en la última sincronización |
| `kyn_cleanupdecision` | texto | decisión operativa aplicada por el flujo |
| `kyn_lastseenon` | fecha-hora | última fecha en que el agente fue visto |
| `kyn_missingcounter` | entero | contador de ausencias consecutivas |
| `statecode` | estado | estado activo/inactivo del registro |
| `statuscode` | razón de estado | razón del estado en Dataverse |

## Campos de gobierno presentes en esquema

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `kyn_functionalowner` | texto | owner funcional mantenido por gobierno |
| `kyn_criticality` | texto | criticidad funcional |
| `kyn_criticalitycode` | texto | código estable de criticidad |
| `kyn_reviewstatus` | texto | estado de revisión |
| `kyn_reviewstatuscode` | texto | código estable de revisión |
| `kyn_governancescore` | decimal o numérico | puntuación derivada de gobierno |
| `kyn_lastenrichedon` | fecha-hora | última fecha de enriquecimiento |
| `kyn_telemetrysource` | texto | origen de evidencia de indicadores |
| `kyn_usageevidence` | texto largo | evidencia narrativa o caveats |
| `kyn_enrichmentsummary` | texto largo | resumen de enriquecimiento |
