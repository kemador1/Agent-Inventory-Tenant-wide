# 07 - Despliegue y release management

## Principio de despliegue

La solucion debe desplegarse como paquete de Power Platform validado previamente en entorno de pruebas. No debe promoverse un paquete que solo "importa a veces" o que exige correcciones manuales impredecibles tras la importacion.

## Secuencia recomendada

1. importar en entorno DEV o TEST;
2. publicar personalizaciones;
3. validar tablas, vistas, formularios y app;
4. activar o revisar flujo principal;
5. ejecutar prueba funcional con una suscripcion real;
6. promover a siguiente entorno.

## Criterios de aceptacion de release

- importacion sin errores de metadata;
- sin referencias a web resources obsoletos;
- sin vistas con columnas de otra entidad;
- sin formularios con ids o controles invalidos;
- envio correcto para modo permitido;
- no envio para modo `OFF`.

## Gestion documental de release

Cada release debe ir acompanada de:

- paquete managed o unmanaged segun estrategia de entorno;
- notas de version;
- checklist de despliegue;
- trazabilidad de cambios funcionales y tecnicos.

## Observacion importante

La documentacion oficial no debe limitarse al nombre del zip. Debe explicar como se integra la solucion completa. Por eso este repositorio ahora separa documentacion formal en `docs/` y soporte tecnico en `anexos/`.
