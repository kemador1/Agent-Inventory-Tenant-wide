# Modelo de datos

## Visión general

La solución actual usa dos tablas Dataverse:

1. `kyn_agenttenantwide`
2. `kyn_suscripcionesdeinformes`

## Tabla `kyn_agenttenantwide`

Propósito:

- almacenar el inventario consolidado de agentes detectados en el tenant.

Campos observados de mayor relevancia:

- `kyn_agenttenantwideid`
- `kyn_agentid`
- `kyn_name`
- `kyn_displayname`
- `kyn_resourceid`
- `kyn_resourcetype`
- `kyn_tenantid`
- `kyn_environmentid`
- `kyn_createdat`
- `kyn_createdby`
- `kyn_createdbydisplay`
- `kyn_creatoremail`
- `kyn_ownerid`
- `kyn_ownerdisplay`
- `kyn_owneremail`
- `kyn_createdin`
- `kyn_location`
- `kyn_schemaname`
- `kyn_entraappid`
- `kyn_authenticationjson`
- `kyn_orchestrationjson`
- `kyn_modeljson`
- `kyn_activityindicator`
- `kyn_isquarantined`
- `kyn_lastpublishedat`
- `kyn_lastseenon`
- `kyn_lastsyncstatus`
- `kyn_cleanupdecision`
- `kyn_missingcounter`

Campos que siguen apareciendo y deben revisarse funcionalmente:

- `kyn_modelNormalized`
- `kyn_originNormalized`

Valoración:

- estos dos campos parecen residuales respecto a la intención actual;
- si ya no forman parte de formularios, vistas ni lógica del flujo, conviene retirarlos del modelo en una siguiente versión controlada;
- si todavía se usan para cálculo visual o compatibilidad, deben documentarse explícitamente.

## Tabla `kyn_suscripcionesdeinformes`

Propósito:

- almacenar destinatarios del informe diario.

Campos observados:

- `kyn_suscripcionesdeinformesid`
- `kyn_name`
- `kyn_recipientemail`
- `ownerid`
- `statecode`
- `statuscode`

Valoración:

- el modelo actual es sencillo y suficiente para un patrón básico de suscripción;
- el flujo actual ya no usa `reportmode`, lo que simplifica la tabla desde la perspectiva funcional;
- si en el futuro se quiere segmentar destinatarios o parametrizar el tipo de informe, debe rediseñarse con un modelo de suscripción claro, no con campos legacy dispersos.

## Relaciones

Las relaciones observadas en `customizations.xml` son las esperables con entidades owner-enabled:

- relaciones con `businessunit`
- relaciones con `owner`, `team`, `systemuser`
- relaciones estándar de `createdby` y `modifiedby`

No se ha detectado una relación funcional directa entre `kyn_agenttenantwide` y `kyn_suscripcionesdeinformes`, lo cual es correcto dado que la suscripción opera como configuración de distribución y no como hijo del agente.

## Consideraciones de gobierno del dato

- `kyn_agenttenantwide` mezcla información técnica del recurso con información de explotación operativa;
- el flujo actual persiste JSON completos (`authentication`, `model`, `orchestration`), lo que es útil para trazabilidad, pero puede crecer rápido y penalizar mantenimiento;
- para escenarios de gobierno maduros conviene distinguir:
  - datos operativos visibles;
  - payload técnico crudo;
  - campos normalizados realmente consumidos por app y reporting.

## Recomendaciones de mejora del modelo

1. decidir el destino de `kyn_modelNormalized` y `kyn_originNormalized`;
2. revisar si `kyn_authenticationjson`, `kyn_modeljson` y `kyn_orchestrationjson` deben mantenerse íntegros o resumidos;
3. documentar el significado exacto de:
   - `kyn_lastsyncstatus`
   - `kyn_cleanupdecision`
   - `kyn_missingcounter`
4. mantener la tabla de suscripciones simple mientras no exista un caso real de segmentación avanzada;
5. si se separa el envío de correo en otro flujo, valorar una tabla adicional de ejecuciones o colas de notificación.
