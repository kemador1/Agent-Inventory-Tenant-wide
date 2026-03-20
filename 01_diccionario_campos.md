# Diccionario de campos de `yb_agenttenantwide`

## Metadatos generales

- Entidad: `yb_agenttenantwide`
- Entity set: `yb_agenttenantwides`
- Ownership: `UserOwned`
- Notas habilitadas: sí
- Auditoría: no

## Campos custom

| Campo lógico | Nombre visible | Tipo | Longitud / formato | Uso principal | Observaciones |
| --- | --- | --- | --- | --- | --- |
| `yb_agenttenantwideid` | agent tenant wide | primarykey | n/a | id técnico del registro | id de Dataverse |
| `yb_name` | Name | nvarchar | 850, text | nombre principal del registro | se rellena con `displayName` |
| `yb_agentid` | agentId | nvarchar | 100, text | identificador funcional del agente | parte de la clave funcional |
| `yb_authenticationjson` | authenticationJson | nvarchar | 100, text | metadato técnico de autenticación | longitud muy baja para JSON |
| `yb_createdat` | createdAt | datetime | datetime | fecha de creación del agente | no dispara update por sí sola |
| `yb_createdby` | createdBy | nvarchar | 100, text | creador resuelto o fallback | texto, no lookup |
| `yb_createdin` | createdIn | nvarchar | 100, text | origen o canal de creación | se usa en charts y reportes |
| `yb_displayname` | displayName | nvarchar | 100, text | nombre visible del agente | principal campo mostrado |
| `yb_entraappid` | entraAppId | nvarchar | 100, text | referencia técnica a app Entra | comparado en updates |
| `yb_environmentid` | environmentId | nvarchar | 100, text | entorno del agente | parte de la clave funcional |
| `yb_isquarantined` | isQuarantined | nvarchar | 100, text | estado de cuarentena | se guarda como `1` o `0` |
| `yb_lastpublishedat` | lastPublishedAt | datetime | datetime | última publicación conocida | se escribe pero no dispara update |
| `yb_location` | location | nvarchar | 100, text | ubicación/región | comparado en updates |
| `yb_modeljson` | modelJson | nvarchar | 100, text | información del modelo | también usado como dimensión analítica |
| `yb_orchestrationjson` | orchestrationJson | nvarchar | 100, text | orquestación técnica | longitud muy baja |
| `yb_ownerid` | ownerId | nvarchar | 100, text | propietario resuelto o fallback | texto, no lookup |
| `yb_resourceid` | resourceId | ntext | 2000, text | id completo del recurso | campo más robusto para trazabilidad |
| `yb_resourcetype` | resourceType | nvarchar | 100, text | tipo de recurso | hoy esperado `microsoft.copilotstudio/agents` |
| `yb_schemaname` | schemaName | nvarchar | 100, text | schema técnico | comparado en updates |
| `yb_tenantid` | tenantId | nvarchar | 100, text | tenant de pertenencia | comparado en updates |

## Campos de sistema relevantes

| Campo | Tipo | Uso |
| --- | --- | --- |
| `createdon` | datetime | creación del registro Dataverse |
| `modifiedon` | datetime | modificación del registro Dataverse |
| `ownerid` | lookup | propietario del registro Dataverse |
| `statecode` | state | activo/inactivo |
| `statuscode` | status | razón de estado |

## Mapeo desde la fuente

| Campo fuente del flujo | Campo Dataverse |
| --- | --- |
| `displayName` | `yb_name`, `yb_displayname` |
| `agentId` | `yb_agentid` |
| `authenticationJson` | `yb_authenticationjson` |
| `createdAt` | `yb_createdat` |
| `createdBy` resuelto | `yb_createdby` |
| `createdIn` | `yb_createdin` |
| `entraAppId` | `yb_entraappid` |
| `environmentId` | `yb_environmentid` |
| `isQuarantined` | `yb_isquarantined` |
| `lastPublishedAt` | `yb_lastpublishedat` |
| `location` | `yb_location` |
| `modelJson` | `yb_modeljson` |
| `orchestrationJson` | `yb_orchestrationjson` |
| `ownerId` resuelto | `yb_ownerid` |
| `resourceId` | `yb_resourceid` |
| `resourceType` | `yb_resourcetype` |
| `schemaName` | `yb_schemaname` |
| `tenantId` | `yb_tenantid` |

## Campos comparados en la detección de cambio

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

## Campos escritos pero no usados para decidir update

- `yb_name`
- `yb_createdat`
- `yb_createdby`
- `yb_ownerid`
- `yb_lastpublishedat`

