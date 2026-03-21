# Flujo de inventario y automatización

## Identificación

- Nombre: `KYN Agent Inventory tenant-wide`
- Archivo: `Workflows/KYNAgentInventorytenant-wide-EAE8C024-3BE4-4BD6-BAD5-E14E3435C632.json`
- Tipo de disparo: manual

## Conectores utilizados

- `Power Platform Admins V2`
- `Dataverse`
- `Office 365 Users`
- conector de correo para envío del informe

## Variables principales

- `varCreated`
- `varUpdated`
- `varDeleted`
- `varErrors`
- `varProcessedAgents`
- `varRunStartTime`
- `varSkipToken`
- `varCreatedByDisplay`
- `varCreatedByEmail`
- `varOwnerIdDisplay`
- `varOwnerIdEmail`
- `varDebugLog`

## Parámetros

- `Notificación correos informes flujo (kyn_Notificacincorreosinformesflujo)`
- `Cliente o empresa informes flujo (kyn_ClienteoEmpresaInformesflujo)`

## Lógica detallada

1. Inicializa contadores, variables de contexto y el instante de inicio.
2. Ejecuta `QueryResources` sobre `microsoft.copilotstudio/agents`.
3. Gestiona paginación mediante `varSkipToken`.
4. Recorre cada agente descubierto.
5. Resuelve `createdBy` y `ownerId` mediante `Office 365 Users` cuando es posible.
6. Calcula normalizaciones:
   - proveedor de modelo;
   - modelo normalizado;
   - indicador de actividad;
   - indicador de uso.
7. Busca registro existente en Dataverse por clave funcional.
8. Si no existe:
   - crea el registro;
   - lo deja activo;
   - incrementa `varCreated`.
9. Si existe:
   - compone el registro actual;
   - evalúa `Condition_Has_Changes`;
   - si hay cambios materiales, actualiza el registro y agrega detalle HTML a `varDebugLog`;
   - si no hay cambios materiales, actualiza solo señales técnicas de visibilidad.
10. Añade el agente a `varProcessedAgents`.
11. Tras el recorrido, ejecuta cleanup sobre los registros no observados.
12. Para los no observados:
   - incrementa `varDeleted` como contador operativo de ausentes/inactivos;
   - actualiza `statecode = 1` y `statuscode = 2`;
   - mantiene el registro sin borrado físico.
13. Construye un resultado final y envía correo HTML en español.

## Comparación material

La condición de cambio compara campos estables y funcionalmente relevantes, entre ellos:

- `displayName`
- `createdBy`
- `ownerId`
- `location`
- `createdIn`
- `schemaName`
- `entraAppId`
- `modelNormalized`
- `modelProvider`
- `usageIndicator`
- `activityIndicator`
- `isQuarantined`
- `resourceId`
- `resourceType`
- `tenantId`
- `environmentId`

La solución evita basarse en fechas crudas o blobs JSON para la detección de cambios principales, salvo donde sea necesario para enriquecer el dato.

## Log de cambios

El flujo construye un bloque HTML por agente actualizado con:

- nombre del campo;
- valor previo;
- valor nuevo.

Esto permite que el correo no solo diga cuántos cambios hubo, sino por qué se han considerado cambios.

## Cleanup y estado operativo

El comportamiento actual del flujo debe interpretarse así:

- no observado en la ejecución actual: inactivo;
- observado en la ejecución actual: activo;
- reaparición posterior: vuelve a activo;
- sin borrado físico automático.

## Correo final

El correo:

- usa asunto y cabecera parametrizados por cliente o empresa;
- resume creados, actualizados, ausentes y errores;
- muestra detalle HTML de cambios materiales;
- incluye timestamps y contexto operativo de la ejecución.
