# 02 - Despliegue y configuración

## Prerrequisitos
- Entorno Dataverse con permisos de importación de soluciones.
- Conexiones de Power Automate operativas.
- Permisos para crear/editar registros en tablas de la solución.

## Importación
1. Ir a Soluciones en Power Platform.
2. Importar `kynagentinventorytenantwide_2_7_0_7_managed.zip`.
3. Esperar fin de importación y revisar log.
4. Publicar personalizaciones.

## Verificación post-import
- Existe la tabla `kyn_suscripcionesdeinformes`.
- Existe columna `kyn_reportmodecode` en la tabla de suscripciones.
- La app model-driven muestra subárea de suscripciones como tabla.
- El flujo principal está activo.

## Carga inicial de suscripciones
Crear registros en `kyn_suscripcionesdeinformes` con:
- `kyn_name`: nombre descriptivo
- `kyn_recipientemail`: correo destino
- `kyn_reportmodecode`: modo de reporte

## Validación funcional rápida
1. Crear una suscripción con correo propio y modo `Complete report`.
2. Ejecutar flujo manualmente.
3. Confirmar recepción del correo.
4. Cambiar a `Do not send report` y reejecutar.
5. Confirmar que no llega correo.
