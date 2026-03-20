# Manual de usuario final

## Perfil destinatario

Usuarios de negocio, analistas y responsables de gobierno con acceso de lectura sobre el inventario.

## Qué pueden hacer

- abrir la app;
- consultar dashboards;
- buscar agentes;
- filtrar por origen, entorno, owner, proveedor de modelo y estado de sincronización;
- abrir el detalle de un agente;
- leer campos técnicos y funcionales;
- crear notas y seguimiento documental;
- exportar información desde vistas o reporte si su perfil lo permite.

## Qué no pueden hacer

- crear agentes;
- editar agentes en la plataforma origen;
- borrar agentes del inventario;
- cambiar la definición de los flujos;
- modificar connection references;
- alterar reglas de seguridad.

## Pasos de uso

1. Abrir la app `KYN Agent Inventory tenant-wide APP`.
2. Entrar en `Dashboard` para visión general.
3. Entrar en `Agents` para analizar el detalle.
4. Usar filtros por:
   - `ownerEmail`
   - `creatorEmail`
   - `originNormalized`
   - `modelProvider`
   - `lastSyncStatus`
5. Abrir un registro para inspección.
6. Añadir una nota si se requiere seguimiento.

## Cómo interpretar campos clave

- `ownerEmail`: email resuelto del owner técnico del agente.
- `creatorEmail`: email resuelto del creador técnico.
- `lastSyncStatus`: estado operativo observado en la última sincronización.
- `Activo`: el agente ha sido detectado en la ejecución actual.
- `Inactivo`: el agente no ha sido detectado en la ejecución actual.
- `lastSeenOn`: última vez en la que el agente fue detectado por el flujo.

## Buenas prácticas

- usar notas para justificar cambios manuales;
- revisar primero agentes `Inactivos` si se espera que sigan existiendo;
- no interpretar `usageIndicator` como consumo real de BizChat.
