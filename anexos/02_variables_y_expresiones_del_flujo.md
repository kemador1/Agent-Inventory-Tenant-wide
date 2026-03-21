# Variables y expresiones del flujo

## Variables principales

| Variable | Función |
| --- | --- |
| `varCreated` | contador de registros creados |
| `varUpdated` | contador de registros actualizados |
| `varMarkedMissing` | contador operativo de registros marcados ausentes o inactivos |
| `varErrors` | colección de errores |
| `varProcessedAgents` | colección de agentes procesados en la ejecución |
| `varRunStartTime` | timestamp de inicio |
| `varSkipToken` | control de paginación del origen |
| `varCreatedByDisplay` | nombre resuelto del creador |
| `varCreatedByEmail` | correo resuelto del creador |
| `varOwnerIdDisplay` | nombre resuelto del owner |
| `varOwnerIdEmail` | correo resuelto del owner |
| `varDebugLog` | detalle HTML de cambios materiales |

## Parámetros

| Parámetro | Función |
| --- | --- |
| `kyn_Notificacincorreosinformesflujo` | destinatarios del informe |
| `kyn_ClienteoEmpresaInformesflujo` | branding del asunto, cabecera y pie |

## Acciones clave

- `Recurrence` (trigger)
- `QueryResources`
- `Compose_Normalized_ModelProvider`
- `Compose_Normalized_ModelName`
- `Compose_UsageIndicator`
- `Compose_ActivityIndicator`
- `Compose_Existing_Record`
- `Condition_Has_Changes`
- `Compose_Change_Details`
- `Compose_Final_Result`

## Expresiones relevantes

### Detección de proveedor de modelo

Se basa en búsqueda textual dentro de `modelJson` para clasificar proveedores como:

- `OpenAI`
- `Anthropic`
- `Microsoft`
- `Google`
- `Meta`
- `Other` o `Unknown`

### Detección de cambios materiales

La condición compara campos estables y materialmente significativos para evitar falsos positivos debidos a:

- formato de fecha;
- serialización JSON;
- cambios no funcionales.

### Construcción del correo

El flujo genera HTML con:

- resumen de contadores;
- detalle de cambios;
- errores detectados;
- branding de empresa o cliente.

## Conectores

- Power Platform Admins V2;
- Dataverse;
- Office 365 Users;
- conector de correo configurado en la solución.

## Observaciones operativas

- el trigger actual es programado (`Recurrence`);
- el flujo usa paginación del origen mediante `SkipToken`;
- el cleanup actual inactiva registros no observados;
- el correo todavía debe leerse como informe operativo, no como certificación funcional ni financiera.
