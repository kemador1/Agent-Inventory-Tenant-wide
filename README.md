# Agent Inventory Tenant-wide

Repositorio de release para la solución de Power Platform **Agent Inventory Tenant-wide**.

## Versión publicada
- **Paquete managed:** `kynagentinventorytenantwide_2_7_0_7_managed.zip`
- **Tipo:** Managed
- **Objetivo:** Inventario tenant-wide de agentes y envío de reportes configurables por usuario desde la app model-driven.

## Contenido del repositorio
- `kynagentinventorytenantwide_2_7_0_7_managed.zip`
- `docs/01_resumen_funcional.md`
- `docs/02_despliegue_configuracion.md`
- `docs/03_operacion_soporte.md`
- `docs/04_troubleshooting_importacion.md`
- `anexos/01_diccionario_campos.csv`
- `anexos/02_expresiones_flujo.txt`
- `anexos/03_fetchxml_vistas.xml`
- `anexos/04_matriz_roles_permisos.csv`
- `anexos/05_checklist_go_live.md`

## Configuración de reportes por usuario
La personalización de reportes está en la app/model-driven (tabla), no en HTML.

Tabla: `kyn_suscripcionesdeinformes`
- `kyn_name`
- `kyn_recipientemail`
- `kyn_reportmodecode` (Choice)
- `kyn_reportmode` (legacy, opcional fallback)

## Modos de reporte
- `148250000`: Complete report (all agents)
- `148250001`: Created agents only
- `148250002`: Created by users (exclude system)
- `148250003`: Changes only since last run
- `148250004`: Do not send report

## Recomendación de importación
1. Importar en entorno de validación.
2. Publicar personalizaciones.
3. Ejecutar flujo manual.
4. Validar suscripciones (caso envía / no envía).
