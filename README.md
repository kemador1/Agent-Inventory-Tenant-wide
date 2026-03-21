# Documentación del producto

Esta carpeta contiene la documentación funcional, técnica y operativa alineada con la release candidate `2.2.0.2` de `kynagentinventorytenantwide`.

## Navegación

- [01_vision_producto.md](01_vision_producto.md)
- [02_arquitectura_funcional_y_tecnica.md](02_arquitectura_funcional_y_tecnica.md)
- [03_modelo_datos.md](03_modelo_datos.md)
- [04_flujo_inventario_y_automatizacion.md](04_flujo_inventario_y_automatizacion.md)
- [05_app_dashboards_reportes.md](05_app_dashboards_reportes.md)
- [06_seguridad_roles_y_gobierno.md](06_seguridad_roles_y_gobierno.md)
- [07_manual_usuario_final.md](07_manual_usuario_final.md)
- [08_manual_despliegue_y_configuracion.md](08_manual_despliegue_y_configuracion.md)
- [09_manual_operacion_y_mantenimiento.md](09_manual_operacion_y_mantenimiento.md)
- [10_riesgos_limitaciones_y_proximos_pasos.md](10_riesgos_limitaciones_y_proximos_pasos.md)
- [11_bienvenida_power_platform.html](11_bienvenida_power_platform.html)
- [anexos/01_diccionario_campos.md](anexos/01_diccionario_campos.md)
- [anexos/02_variables_y_expresiones_del_flujo.md](anexos/02_variables_y_expresiones_del_flujo.md)
- [anexos/03_matriz_de_permisos.md](anexos/03_matriz_de_permisos.md)
- [anexos/04_iconografia_dinamica_en_formulario.md](anexos/04_iconografia_dinamica_en_formulario.md)

## Resumen ejecutivo

`KYN Agent Inventory Tenant-wide` es una solución de Power Platform para inventariar agentes a nivel tenant, consolidarlos en Dataverse y ofrecer una capa de operación, consulta y gobierno con reporting reutilizable.

La `2.2.0.2` incorpora:

- tabla `kyn_agenttenantwide`;
- flujo principal de inventario;
- app model-driven;
- dashboards;
- reporte clásico ligado a la tabla;
- variables de entorno de correo y branding;
- recursos web HTML, JS y SVG para experiencia visual.

## Comportamiento operativo documentado

- si el agente se detecta en la ejecución actual, queda activo;
- si no se detecta, queda inactivo;
- si reaparece, vuelve a activo;
- no se ejecuta borrado físico automático;
- el correo informa en español y detalla cambios materiales.

## Alcance real

- descubrimiento: `microsoft.copilotstudio/agents`;
- persistencia: Dataverse;
- explotación: app, dashboards, reporte clásico y correo operativo.

## Fuera de alcance

- coste real PAYG por agente;
- telemetría soportada de sesiones o prompts de BizChat por agente;
- administración del origen desde esta solución.
