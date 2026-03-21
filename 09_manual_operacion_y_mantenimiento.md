# Manual de operación y mantenimiento

## Operación estándar

1. Ejecutar `KYN Agent Inventory tenant-wide`.
2. Revisar el correo de sincronización.
3. Comprobar `Created`, `Updated`, `Marked Missing` y `Errors`.
4. Revisar el detalle HTML de cambios detectados.
5. Confirmar que los registros ausentes se han marcado inactivos.

## Comportamiento operativo esperado

- agente encontrado: registro activo;
- agente no encontrado: registro inactivo;
- agente reaparecido: registro reactivo a estado activo;
- sin borrado físico automático.

## Controles periódicos

- picos de `Updated` sin cambio real esperado;
- incrementos bruscos de `Marked Missing`;
- conjuntos amplios de agentes inactivos inesperados;
- errores repetidos de resolución de usuario;
- correos no entregados o branding incorrecto;
- problemas de carga de `WebResources`.

## Soporte correctivo

### Si falla el flujo

- revisar `connection references`;
- revisar permisos del conector administrativo;
- validar la respuesta de `QueryResources`;
- revisar expresiones de normalización y comparación;
- revisar si el correo referencia acciones o variables inexistentes.

### Si el estado parece incoherente

- validar si el origen devolvió una visión parcial;
- revisar si el agente realmente sigue existiendo;
- confirmar que la clave `agentId + environmentId` no ha cambiado.

### Si fallan recursos visuales

- comprobar publicación de `WebResources`;
- confirmar nombres lógicos exactos;
- validar dependencias de formularios y app.

## Mantenimiento evolutivo

- ajustar el criterio de comparación material;
- ampliar el reporte clásico;
- enriquecer vistas y dashboards;
- completar los campos de gobierno si la organización los activa;
- reforzar la iconografía dinámica en formularios si se decide incorporarla productivamente.
