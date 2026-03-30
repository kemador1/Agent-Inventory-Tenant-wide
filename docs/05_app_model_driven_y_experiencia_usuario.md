# 05 - App model-driven y experiencia de usuario

## Rol de la app

La app model-driven es la superficie oficial de administracion de la solucion. No debe entenderse como un complemento visual del flujo, sino como el punto de operacion del inventario y de la configuracion de reportes.

## Capacidades que debe exponer

- acceso a `kyn_agenttenantwide`;
- acceso a `kyn_suscripcionesdeinformes`;
- formularios coherentes con el modelo actual;
- vistas alineadas con las columnas reales de cada entidad.

## Gestion de suscripciones

La app debe permitir que un usuario autorizado:

- cree o edite su suscripcion;
- defina el correo de recepcion;
- seleccione el tipo de reporte mediante `kyn_reportmodecode`;
- desactive funcionalmente su recepcion usando el modo `Do not send report`.

## Criterios de calidad de UX

- los nombres visibles deben describir el resultado de negocio, no codigos internos;
- no deben aparecer campos retirados o sin uso;
- el formulario debe explicar claramente que recibe cada modo;
- la navegacion debe conducir a inventario y suscripciones sin componentes residuales.

## Recomendacion para formulario de suscripciones

El formulario principal debe mostrar como minimo:

- nombre de la suscripcion;
- correo destinatario;
- modo de reporte;
- propietario.

El campo `kyn_reportmode` puede mantenerse oculto como compatibilidad, pero no debe ser el mecanismo primario de edicion para el usuario.

## Error de diseno que se evita

La suscripcion no debe resolverse mediante un HTML o web resource incrustado como pseudo-pantalla de configuracion. Eso rompe el modelo operativo de Power Platform y dificulta soporte, seguridad y mantenibilidad.
