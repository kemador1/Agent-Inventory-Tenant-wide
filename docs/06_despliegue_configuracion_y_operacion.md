# Despliegue, configuración y operación

## Fuente de verdad para despliegue

En este repositorio la fuente principal es la solución descomprimida en raíz.

Archivos principales:

- [solution.xml](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/solution.xml)
- [customizations.xml](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/customizations.xml)
- [Workflows/KYNAgentInventorytenant-wide-612266CD-F828-F111-8341-7CED8D488E89.json](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/Workflows/KYNAgentInventorytenant-wide-612266CD-F828-F111-8341-7CED8D488E89.json)

## Dependencias a validar

### Connection references

- `kyn_ConnectionReferencePowerPlatformAdminsTenantwide`
- `kyn_ConnectionReferenceDataverseTenantwide`
- `kyn_sharedoffice365users_f32b7`
- `kyn_ConnectionReferenceAgentInventoryTenantwide`

### Variables de entorno

Presente en el repositorio:

- `kyn_ClienteoEmpresaInformesflujo`

Referenciadas por el flujo, pero no presentes físicamente en `environmentvariabledefinitions/`:

- `kyn_UrlAppGeneralAgentInventory`
- `kyn_UrlVistaAgentesCreadosAgentInventory`
- `kyn_UrlVistaAgentesEliminadosAgentInventory`

Conclusión:

- antes de desplegar, hay que confirmar si estas variables existen en el entorno de destino o si faltan en la exportación actual;
- esta discrepancia debe resolverse para evitar correos con enlaces incompletos o fallos de parametrización.

## Dependencias de app settings

`solution.xml` declara dependencias externas:

- `EnablePowerBIQuickReport`
- `FormFillBarUXEnabled`
- `HeaderAndNavigationRefresh`

Esto no siempre rompe la importación, pero sí puede condicionar el comportamiento de la app y debe ser tenido en cuenta.

## Checklist operativo de despliegue

1. validar que el entorno destino tiene las conexiones necesarias;
2. revisar connection references tras la importación;
3. revisar las variables de entorno requeridas;
4. comprobar que la tabla `kyn_suscripcionesdeinformes` tiene destinatarios activos;
5. revisar el trigger `Recurrence` del flujo;
6. activar el flujo y realizar prueba controlada;
7. verificar que la app abre y navega correctamente;
8. revisar que dashboard, formulario y vistas no referencian campos retirados.

## Operación diaria

La operación normal de la solución debería centrarse en:

- revisar el estado de ejecución del flujo;
- validar crecimiento del inventario;
- revisar registros marcados como ausentes;
- mantener suscripciones activas;
- comprobar que el resumen enviado remite a la app y no sustituye la revisión operativa.

## Criterio de soporte

Cuando falle la solución, revisar en este orden:

1. activación del flujo;
2. conexiones solution-aware;
3. variables de entorno;
4. permisos del conector Power Platform Admin;
5. integridad de vistas/formularios con respecto al modelo actual;
6. consistencia entre `solution.xml`, `customizations.xml` y `Workflows/`.
