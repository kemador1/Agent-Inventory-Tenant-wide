# Manual de usuario final

## Perfil destinatario

Usuarios de negocio, analistas, responsables de gobierno y soporte con acceso de lectura al inventario.

## Qué pueden hacer

- abrir la app;
- consultar dashboards y vistas;
- buscar agentes;
- filtrar por owner, creator, origen, proveedor de modelo y estado;
- abrir el detalle del registro;
- consultar el reporte clásico desde la tabla, si la superficie lo muestra;
- crear notas y seguimiento documental;
- exportar información según permisos.

## Qué no pueden hacer

- crear o editar agentes en el origen;
- modificar el flujo de inventario;
- cambiar variables de entorno;
- administrar conexiones;
- borrar masivamente el inventario;
- modificar la seguridad del producto.

## Uso recomendado

1. Abrir `KYN Agent Inventory tenant-wide APP`.
2. Revisar el dashboard para entender situación general.
3. Entrar en la vista de agentes.
4. Filtrar por:
   - `ownerEmail`
   - `creatorEmail`
   - `originNormalized`
   - `modelProvider`
   - `lastSyncStatus`
5. Abrir un registro concreto.
6. Revisar estado, modelo, owner y última detección.
7. Añadir nota si el registro requiere seguimiento.

## Interpretación de campos clave

- `ownerEmail`: correo del owner técnico resuelto.
- `creatorEmail`: correo del creador técnico resuelto.
- `modelProvider`: proveedor inferido del modelo.
- `lastSyncStatus`: estado operativo de la última sincronización.
- `Activo`: agente observado en la ejecución actual.
- `Inactivo`: agente no observado en la ejecución actual.
- `lastSeenOn`: última fecha en la que el flujo detectó el agente.

## Buenas prácticas

- revisar primero los registros inactivos inesperados;
- usar notas para justificar decisiones funcionales;
- contrastar con el origen si un agente crítico aparece inactivo.
