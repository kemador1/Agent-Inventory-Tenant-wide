# Documentación del producto

Esta carpeta documenta la solución `kynagentinventorytenantwide` versión `2.2.0.0`, preparada como solución no administrada de Power Platform / Dataverse.

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

La solución construye un inventario tenant-wide de agentes sobre Dataverse y lo publica mediante una app model-driven, dashboards y reporting ejecutivo. La versión `2.2.0.0` simplifica la operación y refuerza la trazabilidad:

- clave alterna para evitar duplicados por `agentId + environmentId`;
- cleanup endurecido sin borrado duro automático y con futura inactivación por ausencias consecutivas;
- normalización de origen y modelo;
- campos de email para owner y creator separados del `createdby` nativo de Dataverse;
- un único flujo de inventario, sin flujo de enriquecimiento adicional;
- trazabilidad explícita de los campos que provocan cada actualización;
- correo operativo en español y personalizable por empresa/cliente;
- navegación sin `WebResources` SVG personalizados, para maximizar la importabilidad entre tenants;
- manuales formales de operación, despliegue y usuario.

## Componentes incluidos

- Tabla Dataverse: `kyn_agenttenantwide`
- Flujo: `KYN Agent Inventory tenant-wide`
- Reporte: `KYN Agent Inventory Executive Report`
- Dashboard clásico: `KYN Agent Inventory – Tenant Overview`
- Dashboard ejecutivo: `KYN Agent Inventory – Executive Overview Tenant-wide`
- App model-driven: `KYN Agent Inventory tenant-wide APP`
- Variable de entorno: `kyn_Notificacincorreosinformesflujo`
- Variable de entorno: `kyn_ClienteoEmpresaInformesflujo`
- Página HTML de bienvenida: `11_bienvenida_power_platform.html`

## Decisiones clave de diseño

- El flujo de inventario sigue siendo el origen maestro de descubrimiento.
- Los registros no observados no se eliminan físicamente; si un agente no aparece en la sincronización actual, pasa a inactivo y se reactiva automáticamente si vuelve a detectarse en una ejecución posterior.
- El producto no afirma telemetría real por agente para Copilot Chat / BizChat si Microsoft no la expone de forma soportada.

## Alcance real de esta versión

- Descubrimiento confirmado: `microsoft.copilotstudio/agents`
- Persistencia y explotación: Dataverse
- Reporting: dashboards, vistas y reporte exportable

## Fuera de alcance en esta versión

- coste real PAYG por agente;
- sesiones y prompts completos de Copilot Chat como métrica soportada por agente;
- control transaccional de borrado físico masivo;
- consolidación multi-fuente con Graph beta dentro del flujo productivo.

## Referencia rápida

1. Importar la solución.
2. Configurar las connection references.
3. Informar las variables de entorno de correos y empresa/cliente.
4. Ejecutar `KYN Agent Inventory tenant-wide`.
5. Validar vistas, dashboard, reporte y correo de salida.
