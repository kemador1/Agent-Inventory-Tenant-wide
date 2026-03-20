# Documentación del producto

Esta carpeta documenta la solución `agentinventorytenantwide` versión `1.0.0.8`, exportada como solución no administrada de Power Platform / Dataverse.

## Qué contiene

- [01_vision_producto.md](01_vision_producto.md): objetivo, problema, valor de negocio y alcance real.
- [02_arquitectura_funcional_y_tecnica.md](02_arquitectura_funcional_y_tecnica.md): componentes, arquitectura y dependencias.
- [03_modelo_datos.md](03_modelo_datos.md): diseño de la tabla `yb_agenttenantwide` y criterios de modelado.
- [04_flujo_inventario_y_automatizacion.md](04_flujo_inventario_y_automatizacion.md): lógica detallada del flujo de inventario.
- [05_app_dashboards_reportes.md](05_app_dashboards_reportes.md): app model-driven, dashboards, vistas y reporte.
- [06_seguridad_roles_y_gobierno.md](06_seguridad_roles_y_gobierno.md): permisos, límites funcionales y gobierno.
- [07_manual_usuario_final.md](07_manual_usuario_final.md): manual para usuarios finales y analistas.
- [08_manual_despliegue_y_configuracion.md](08_manual_despliegue_y_configuracion.md): importación, parametrización y puesta en marcha.
- [09_manual_operacion_y_mantenimiento.md](09_manual_operacion_y_mantenimiento.md): operación, soporte y mantenimiento.
- [10_riesgos_limitaciones_y_proximos_pasos.md](10_riesgos_limitaciones_y_proximos_pasos.md): gaps actuales, riesgos y roadmap.
- [anexos/01_diccionario_campos.md](anexos/01_diccionario_campos.md): diccionario completo de campos.
- [anexos/02_variables_y_expresiones_del_flujo.md](anexos/02_variables_y_expresiones_del_flujo.md): variables, expresiones y conectores del flujo.
- [anexos/03_matriz_de_permisos.md](anexos/03_matriz_de_permisos.md): matriz de privilegios del rol custom.

## Resumen ejecutivo

La solución construye un hub de inventario de agentes sobre Dataverse para ofrecer visibilidad tenant-wide, con una app model-driven para consulta, dashboards ejecutivos, un reporte operativo y un flujo que sincroniza agentes detectados desde las APIs administrativas de Power Platform.

## Alcance objetivo vs alcance implementado

- Objetivo declarado: gobierno centralizado de agentes a nivel tenant, independientemente de su origen.
- Implementación actual observada: el flujo consulta únicamente recursos de tipo `microsoft.copilotstudio/agents`.
- Implicación: la visión de producto es más amplia que la cobertura funcional actual.

## Componentes incluidos en el paquete

- Tabla Dataverse: `yb_agenttenantwide`
- Flujo cloud: `Agent Inventory tenant wide`
- Reporte: `Inventario de Agentes Tenant-wide`
- Dashboard clásico: `Agent Inventory – Tenant Overview`
- Dashboard ejecutivo: `Agent Inventory – Overview Ejecutivo Tenant-wide`
- App model-driven: `Agent Inventory tenant wide APP`
- Variable de entorno: `yb_Notificacincorreosinformesflujo`

## Hechos relevantes para operación

- El flujo exportado tiene disparador manual tipo `Button`.
- La variable de entorno de notificación tiene valor por defecto `0`; sin parametrización no se enviarán correos útiles.
- El rol custom `Usuario Basico Agent Tenant-Wide ROLE` permite leer el inventario y gestionar notas, pero no crear, editar ni borrar registros de agentes.
- La solución tiene dependencias faltantes declaradas respecto a `CopilotStudioAccelerator`, `msdyn_AppCopilotFeatures`, `msdyn_AppFrameworkInfraExtensions` y `msdyn_TimelineExtended`.

