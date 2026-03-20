# Manual de despliegue y configuración

## 1. Alcance

Este manual cubre la puesta en marcha de la solución exportada en un entorno Power Platform.

## 2. Artefacto

- Solución: `agentinventorytenantwide`
- Versión: `1.0.0.8`
- Tipo exportado: no administrada

## 3. Prerrequisitos

### 3.1 Plataforma

- entorno Dataverse operativo,
- permisos para importar soluciones,
- capacidad de crear o asignar connection references,
- acceso administrativo a Power Platform para el conector admin.

### 3.2 Dependencias

Antes o durante la importación, validar:

- `CopilotStudioAccelerator`
- `msdyn_AppCopilotFeatures`
- `msdyn_AppFrameworkInfraExtensions`
- `msdyn_M365CopilotAppInfraSettings`
- `msdyn_TimelineExtended`

Si faltan, la app puede importar con incidencias visuales o de configuración.

## 4. Pasos de despliegue

1. Importar la solución `agentinventorytenantwide`.
2. Revisar el resultado de importación y las dependencias faltantes.
3. Resolver o mapear las connection references.
4. Configurar la variable de entorno de notificación.
5. Validar acceso a la app y a la tabla.
6. Asignar roles de seguridad.
7. Ejecutar una sincronización de prueba.
8. Verificar datos, dashboards, reportes y correo.

## 5. Connection references a configurar

| Connection reference | Conector | Finalidad |
| --- | --- | --- |
| `yb_ConnectionReferenceAgentInventoryTenantwide` | Office 365 Outlook | envío de correo de resultado |
| `yb_ConnectionReferenceDataverseTenantwide` | Dataverse | persistencia del inventario |
| `yb_ConnectionReferencePowerPlatformAdminsTenantwide` | Power Platform Admins V2 | descubrimiento de agentes |
| `yb_sharedoffice365users_f32b7` | Office 365 Users | resolución de nombres de usuario |

## 6. Variable de entorno

### Nombre

`yb_Notificacincorreosinformesflujo`

### Uso

Lista de correos separada por `;`.

### Recomendación

Configurar una lista operativa real. Si se deja en `0`, el flujo no enviará un informe funcional.

## 7. Seguridad y acceso

### App

La app está mapeada al rol custom y a dos roles de plataforma incluidos por GUID en el export.

### Usuarios de negocio

Asignar `Usuario Basico Agent Tenant-Wide ROLE` a usuarios de consumo.

### Administradores

Asignar adicionalmente los roles necesarios de Power Platform para mantenimiento de solución, conexiones y flujo.

## 8. Validación post-despliegue

Checklist mínima:

- la app abre correctamente,
- el sitemap muestra `Dashboard` y `Agents`,
- la tabla `yb_agenttenantwide` existe,
- el flujo se puede ejecutar,
- la consulta administrativa devuelve datos,
- se crean o actualizan registros,
- los charts muestran información,
- el correo llega al destinatario configurado.

## 9. Consideraciones de promoción entre entornos

- revisar connection references en cada entorno,
- no transportar ciegamente destinatarios de correo de producción a entornos bajos,
- validar dependencias visuales y de app settings,
- ejecutar una carga controlada antes de abrir acceso a usuarios.

## 10. Observación importante sobre scheduling

Aunque la descripción funcional habla de inventario periódico, el flujo exportado usa un trigger manual `Button`. Para un comportamiento periódico real hay que:

- añadir un disparador programado al flujo, o
- invocarlo desde un proceso externo planificado.

## 11. Recomendaciones de despliegue seguro

- usar cuenta de servicio para operaciones administrativas y correo,
- probar primero en entorno no productivo,
- validar el comportamiento de borrado antes de producción,
- documentar claramente quién puede ejecutar el flujo.

