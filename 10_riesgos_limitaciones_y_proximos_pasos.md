# Riesgos, limitaciones y próximos pasos

## Riesgos actuales

| Riesgo | Impacto | Situación actual | Mitigación |
| --- | --- | --- | --- |
| visión parcial del origen en una ejecución | alto | vigente | contrastar el estado inactivo con el origen si el volumen de ausentes es anómalo |
| cambios falsos por formato o serialización | medio | parcialmente mitigado | restringir comparaciones a campos materiales y revisar expresiones |
| dependencia de nombres exactos en `WebResources` | medio | vigente | documentar nombres lógicos y validar formularios tras importar |
| sobreinterpretación de indicadores derivados | medio | vigente | documentar que no son telemetría soportada de BizChat |
| coexistencia de campos legacy y campos activos | bajo/medio | vigente | aclarar en documentación qué campos son operativos y cuáles son de compatibilidad |

## Limitaciones

- el inventario cubre el origen soportado en el flujo actual, no un ecosistema multi-fuente completo;
- la solución no expone coste real PAYG por agente;
- la solución no recupera prompts o sesiones completas soportadas de Copilot Chat por agente;
- el estado inactivo debe leerse como ausencia observada en la última ejecución, no como baja definitiva confirmada;
- la iconografía dinámica en formulario no está cerrada como componente estándar productivo dentro de esta candidata.

## Próximos pasos recomendados

- estabilizar definitivamente la lógica de reporte y correo;
- decidir si se simplifican o activan formalmente los campos de gobierno presentes en esquema;
- reforzar la visibilidad del reporte clásico desde la app;
- normalizar mejor el tratamiento de iconografía por modelo;
