# Flujo de inventario y automatización

## Flujo principal

- Nombre: `KYN Agent Inventory tenant-wide`
- Archivo: `Workflows/KYNAgentInventorytenant-wide-EAE8C024-3BE4-4BD6-BAD5-E14E3435C632.json`
- Tipo de disparo: botón manual

## Secuencia funcional

1. Consulta agentes tenant-wide en Power Platform Admins V2.
2. Normaliza origen, proveedor de modelo, modelo e indicadores operativos.
3. Resuelve `createdBy` y `ownerId` vía Office 365 Users cuando aplica.
4. Busca el registro existente por clave funcional `agentId + environmentId`.
5. Si no existe, crea el registro.
6. Si existe, compara solo campos materiales y estables.
7. Si hay cambios, actualiza el registro y genera una traza detallada del cambio.
8. Si no hay cambios, refresca solo metadatos de visibilidad de ejecución.
9. Ejecuta cleanup seguro para marcar inactivo lo no observado en la sincronización actual.
10. Envía un correo resumen en español.

## Detección de cambios reales

La condición de cambios se centra en campos estables para evitar falsos positivos por fechas o serialización JSON.

El log operativo muestra por agente:

- campo cambiado;
- valor anterior;
- valor nuevo.

## Criterio de cleanup implementado

- si un agente aparece en el origen, queda activo;
- si un agente no aparece en la sincronización actual, queda inactivo;
- si un agente vuelve a aparecer en una ejecución posterior, recupera estado activo;
- no existe borrado físico automático;
- el histórico se conserva en Dataverse.

## Variables de entorno

- `kyn_Notificacincorreosinformesflujo`: destinatarios del correo.
- `kyn_ClienteoEmpresaInformesflujo`: nombre de empresa o cliente para asunto, cabecera y pie del correo.
