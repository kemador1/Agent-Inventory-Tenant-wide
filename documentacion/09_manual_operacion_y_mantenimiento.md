# Manual de operación y mantenimiento

## Operación estándar

1. Ejecutar `KYN Agent Inventory tenant-wide`.
2. Revisar el correo resumen.
3. Confirmar volumen de `Created`, `Updated`, `Marked Missing` y `Errors`.
4. Confirmar que los agentes no observados quedan inactivos.
5. Si hay `Updated`, revisar el detalle de cambios por agente.

## Política de ausencia e inactivación

- si el agente aparece en origen, queda activo;
- si el agente no aparece en la sincronización actual, queda inactivo;
- si vuelve a aparecer, recupera estado activo de forma automática;
- no se realiza borrado físico automático.

## Controles periódicos

- picos anómalos de `Marked Missing`;
- incrementos bruscos de registros inactivos;
- errores repetidos de conexión;
- registros sin `ownerEmail` ni `creatorEmail`;
- cambios repetitivos sobre el mismo conjunto sin cambio real en origen.

## Mantenimiento correctivo

### Si falla el flujo de inventario

- revisar connection references;
- validar permisos del conector admin;
- revisar respuesta de `QueryResources`;
- revisar expresiones de comparación material.

## Mantenimiento evolutivo

- añadir nuevos campos materiales si se justifican;
- ajustar plantilla del correo;
- revisar columnas visibles en vistas y reporte.
