# 06 - Seguridad, operacion y soporte

## Seguridad

La seguridad debe controlar dos cosas:

- quien puede consultar el inventario;
- quien puede administrar suscripciones y configuracion operativa.

En el paquete existe un rol lector que debe revisarse en cada entorno antes de produccion. El detalle exportado de privilegios se encuentra en `anexos/04_matriz_roles_permisos.csv`.

## Operacion diaria

La operacion de la solucion requiere:

- monitorizacion de ejecuciones del flujo;
- revision de errores de sincronizacion;
- mantenimiento de suscripciones invalidas;
- comprobacion periodica de vistas, formularios y app tras cada despliegue.

## Responsabilidades operativas

### Equipo funcional

- valida que las vistas y formularios responden al negocio;
- define quien debe recibir que tipo de reporte.

### Equipo tecnico

- valida importacion de la solucion;
- corrige dependencias rotas;
- mantiene expresiones, conectores y empaquetado.

## Soporte

Incidencias tipicas:

- el flujo corre pero no envia correo;
- la importacion falla por metadata inconsistente;
- una vista referencia un atributo inexistente;
- el formulario muestra columnas legacy;
- una suscripcion existe pero el destinatario no recibe salida.

## Nivel minimo de control

Antes de cerrar un ticket de soporte deben revisarse:

1. estado del flujo;
2. valores de la suscripcion del usuario;
3. modo de reporte resuelto;
4. condicion de envio;
5. consistencia del paquete importado.
