# Agent Inventory Tenant-wide

Documentacion oficial de la solucion Power Platform `Agent Inventory Tenant-wide`.

Este repositorio ya no contiene notas sueltas de release. La documentacion se ha reorganizado como documentacion formal de solucion: alcance funcional, arquitectura, modelo de datos, automatizacion, app model-driven, seguridad, despliegue, operacion y troubleshooting.

## Objetivo de la solucion

La solucion proporciona inventario tenant-wide de agentes, consolidacion en Dataverse, visualizacion operativa en app model-driven y distribucion de reportes personalizables por usuario a partir de una tabla de suscripciones mantenida en la propia aplicacion.

## Principios de diseno

- El inventario debe reflejar datos de la consulta origen con un modelo consistente.
- La configuracion de notificaciones y reportes debe vivir en Dataverse y en la app, no en HTML ni en parametros ocultos.
- La solucion debe ser importable, mantenible y operable como conjunto: tablas, vistas, formularios, app y flujos.
- Los modos de reporte deben ser comprensibles por negocio y trazables tecnicamente.

## Estructura documental

- `docs/01_resumen_funcional.md`
- `docs/02_arquitectura_funcional_y_tecnica.md`
- `docs/03_modelo_datos_y_gobierno.md`
- `docs/04_automatizacion_y_flujos.md`
- `docs/05_app_model_driven_y_experiencia_usuario.md`
- `docs/06_seguridad_operacion_y_soporte.md`
- `docs/07_despliegue_y_release_management.md`
- `docs/08_troubleshooting_y_lecciones_aprendidas.md`

## Anexos tecnicos

- `anexos/01_diccionario_campos.csv`
- `anexos/02_expresiones_flujo.txt`
- `anexos/03_fetchxml_vistas.xml`
- `anexos/04_matriz_roles_permisos.csv`
- `anexos/05_checklist_go_live.md`

## Paquetes de solucion

El repositorio contiene los paquetes de solucion disponibles en este estado de trabajo. La documentacion es aplicable a la linea funcional actual de la solucion y debe acompañar al paquete promovido a cada entorno.
