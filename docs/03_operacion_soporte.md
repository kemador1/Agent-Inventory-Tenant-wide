# 03 - Operación y soporte

## Operación diaria
- Revisar ejecuciones del flujo tenant-wide.
- Verificar número de registros procesados y correos enviados.
- Corregir suscripciones inválidas (correo vacío/formato incorrecto).

## Gobierno de datos
- Mantener consistencia de campos con el modelo actual.
- Evitar reintroducir columnas legacy no usadas en vistas de entidades incorrectas.
- Validar cambios en DEV antes de promoción.

## Buenas prácticas
- Toda nueva lógica de notificaciones debe salir de tabla/configuración, no de HTML.
- Para cambios de expression en Flow, usar `string()`/`int()` en cast explícito.
- Evitar `empty()` sobre enteros; usar `equals(valor, null)`.

## Checklist de release
- Importación sin errores en entorno limpio.
- Flujos activos.
- App publicada.
- Prueba de correo positiva y negativa (`OFF`).
- Documentación actualizada con versión exacta.
