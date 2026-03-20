# Variables y expresiones del flujo

## 1. Variables

| Variable | Tipo | Inicialización | Uso |
| --- | --- | --- | --- |
| `varSkipToken` | string | `START` | paginación |
| `varCreated` | integer | `0` | contador altas |
| `varUpdated` | integer | `0` | contador cambios |
| `varDeleted` | integer | `0` | contador bajas |
| `varProcessedAgents` | array | `[]` | claves procesadas |
| `varErrors` | array | `[]` | errores por agente |
| `varRunStartTime` | string | `utcNow()` | marca temporal inicial |
| `varCreatedByDisplay` | string | vacío | resolución de creador |
| `varOwnerIdDisplay` | string | vacío | resolución de owner |
| `varDebugLog` | string | vacío | trazas de diferencias |

## 2. Operaciones de conectores

| Acción | Conector | Operación |
| --- | --- | --- |
| `Query_Power_Platform_Resources` | Power Platform Admins V2 | `QueryResources` |
| `Get_User_Profile_CreatedBy` | Office 365 Users | `UserProfile_V2` |
| `Get_User_Profile_OwnerId` | Office 365 Users | `UserProfile_V2` |
| `List_Existing_By_Agent_And_Environment` | Dataverse | `ListRecords` |
| `Create_Agent_Record` | Dataverse | `CreateRecord` |
| `Update_Agent_Record` | Dataverse | `UpdateRecord` |
| `List_All_Agent_Records` | Dataverse | `ListRecords` |
| `Delete_Agent_Record` | Dataverse | `DeleteRecord` |
| `Send_an_email_(V2)` | Office 365 Outlook | `SendEmailV2` |

## 3. Expresiones clave

### 3.1 Fin de paginación

`@equals(variables('varSkipToken'), '')`

### 3.2 Siguiente página

`@{coalesce(body('Query_Power_Platform_Resources')?['skipToken'], '')}`

### 3.3 Clave funcional procesada

`@concat(coalesce(items('Apply_to_each_Agent')?['agentId'], ''), '|', coalesce(items('Apply_to_each_Agent')?['environmentId'], ''))`

### 3.4 Detección de sistema para creador u owner

Se considera `System` cuando el identificador es:

- `00000000-0000-0000-0000-000000000000`
- cadena vacía

### 3.5 Existencia del registro

`@greater(length(coalesce(body('List_Existing_By_Agent_And_Environment')?['value'], createArray())), 0)`

### 3.6 Borrado por ausencia en la ejecución

`not contains(varProcessedAgents, yb_agentid|yb_environmentid)`

## 4. Campos proyectados desde `QueryResources`

- `resourceId`
- `location`
- `agentId`
- `tenantId`
- `resourceType`
- `environmentId`
- `displayName`
- `createdAt`
- `createdBy`
- `ownerId`
- `isQuarantined`
- `lastPublishedAt`
- `createdIn`
- `schemaName`
- `entraAppId`
- `orchestrationJson`
- `authenticationJson`
- `modelJson`

## 5. Campos incluidos en `Condition_Has_Changes`

- `yb_displayname`
- `yb_location`
- `yb_createdin`
- `yb_schemaname`
- `yb_entraappid`
- `yb_orchestrationjson`
- `yb_authenticationjson`
- `yb_modeljson`
- `yb_isquarantined`
- `yb_resourceid`
- `yb_resourcetype`
- `yb_tenantid`
- `yb_environmentid`

## 6. Resultado final compuesto

El flujo compone:

- resumen textual de inicio/fin,
- `created`,
- `updated`,
- `deleted`,
- `processed`,
- `errors`,
- `errorDetails`.

## 7. Estructura del correo

El correo HTML incluye:

- cabecera de reporte,
- tarjetas con `Creados`, `Actualizados`, `Eliminados`, `Procesados`, `Errores`,
- bloque interpretativo,
- detalle de errores,
- `DEBUG` con `varDebugLog`.

## 8. Observaciones técnicas

- `varDebugLog` registra diferencias incluso para campos que no disparan update, pero el update solo ocurre si `Condition_Has_Changes` es verdadera.
- El cleanup se ejecuta cuando `length(varProcessedAgents) > 0`.
- La lista de cleanup tiene `$top = 5000`; si el inventario supera esa cifra, la lógica actual requerirá revisión.

