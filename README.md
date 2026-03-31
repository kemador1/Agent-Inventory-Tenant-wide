# Agent Inventory Tenant-wide

Repositorio de la solución Power Platform `kynagentinventorytenantwide`, orientada al inventario, visibilidad y gobierno de agentes a nivel tenant.

Este repositorio contiene la solución descomprimida como fuente principal. La documentación se ha rehecho tomando como referencia el estado real actual del contenido en raíz:

- `solution.xml`
- `customizations.xml`
- `Workflows/`
- `WebResources/`
- `Reports/`
- `environmentvariabledefinitions/`

## Contenido

1. [Estado actual](#estado-actual)
2. [Estructura del repositorio](#estructura-del-repositorio)
3. [Mapa de documentación](#mapa-de-documentación)
4. [Importación y despliegue](#importación-y-despliegue)
5. [Observaciones de mejora](#observaciones-de-mejora)

## Estado actual

- Solución: `kynagentinventorytenantwide`
- Nombre mostrado: `Agent Inventory Tenant-wide`
- Versión actual en `solution.xml`: `2.7.0.9`
- Tipo de paquete actual: `managed`
- Publisher: `kyn`

Componentes identificados en la solución actual:

- 2 tablas Dataverse:
  - `kyn_agenttenantwide`
  - `kyn_suscripcionesdeinformes`
- 1 flujo Power Automate:
  - `KYN Agent Inventory tenant-wide`
- 1 dashboard
- 1 model-driven app:
  - `kyn_AgentControlHubtenantwide`
- 1 rol de seguridad
- 1 informe
- 9 web resources
- 1 variable de entorno presente físicamente en el repositorio:
  - `kyn_ClienteoEmpresaInformesflujo`

## Estructura del repositorio

```text
Agent-Inventory-Tenant-wide/
├── README.md
├── solution.xml
├── customizations.xml
├── [Content_Types].xml
├── Workflows/
├── WebResources/
├── Reports/
├── environmentvariabledefinitions/
├── Release/
└── docs/
```

Criterio documental:

- la raíz contiene la solución exportada;
- `docs/` contiene la documentación oficial del proyecto;
- `Release/` contiene paquetes auxiliares o históricos que no deben confundirse con la fuente principal;
- la documentación diferencia entre:
  - estado real actual;
  - deuda técnica observada;
  - mejoras recomendadas.

## Mapa de documentación

- [Índice general](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/00_indice_general.md)
- [01. Solución y alcance](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/01_solucion_y_alcance.md)
- [02. Arquitectura funcional y técnica](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/02_arquitectura_funcional_y_tecnica.md)
- [03. Modelo de datos](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/03_modelo_de_datos.md)
- [04. Flujo principal Power Automate](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/04_flujo_principal_power_automate.md)
- [05. App, dashboard y seguridad](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/05_app_dashboard_y_seguridad.md)
- [06. Despliegue, configuración y operación](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/06_despliegue_configuracion_y_operacion.md)
- [07. Deuda técnica y mejoras recomendadas](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/07_deuda_tecnica_y_mejoras_recomendadas.md)

## Importación y despliegue

Referencia principal:

- [06. Despliegue, configuración y operación](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/06_despliegue_configuracion_y_operacion.md)

Puntos a validar antes de importar:

- conexiones solution-aware del flujo;
- presencia de variables de entorno requeridas por el flujo;
- dependencias de app settings indicadas en `solution.xml`;
- consistencia entre el flujo exportado y los componentes raíz declarados.

## Observaciones de mejora

La solución actual funciona como base documental, pero no está completamente saneada. Las principales observaciones detectadas en el contenido actual son:

- el flujo no usa ya `reportmode`, pero todavía conserva variables legacy de debug y HTML;
- `solution.xml` aún declara `kyn_Report_Subscriptions` como web resource raíz;
- el flujo referencia parámetros de URL para la app y vistas, pero en el repositorio solo está presente una variable de entorno física;
- siguen existiendo columnas legacy en `kyn_agenttenantwide`, como `kyn_modelNormalized` y `kyn_originNormalized`;
- el repositorio contiene restos de releases antiguas y cambios eliminados que conviene consolidar antes de publicar definitivamente.

Estas mejoras están detalladas y priorizadas en:

- [07. Deuda técnica y mejoras recomendadas](/Volumes/Ext_1TB/Github/Agent-Inventory-Tenant-wide/docs/07_deuda_tecnica_y_mejoras_recomendadas.md)
