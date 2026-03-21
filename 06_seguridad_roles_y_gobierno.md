# Seguridad, roles y gobierno

## Modelo de acceso

La solución separa claramente:

- usuarios consumidores del inventario;
- administradores funcionales;
- administradores técnicos o CoE.

## Rol de consulta

La solución incluye un rol custom de lectura asociado a la app y a la tabla de inventario. Su objetivo es permitir consulta, visualización y anotación sin dar capacidades de administración del producto ni del origen.

## Capacidades permitidas a usuarios finales

- abrir la app;
- consultar dashboards;
- consultar vistas;
- abrir el detalle de agentes;
- ejecutar o abrir el reporte si su superficie lo permite;
- crear y mantener notas;
- exportar información según sus privilegios de lectura.

## Capacidades restringidas

- crear agentes en origen;
- modificar agentes en origen;
- modificar la definición del flujo;
- mantener connection references;
- administrar variables de entorno;
- borrar registros del inventario;
- editar registros del inventario fuera de los permisos expresamente concedidos.

## Gobierno funcional

La solución permite distinguir entre:

- ownership técnico detectado automáticamente;
- ownership funcional o gobierno, cuando la organización decida completarlo;
- estado operativo calculado por la sincronización;
- validación humana posterior cuando sea necesaria.

## Principios de gobierno

- el inventario es fuente operativa de control, no sustituto del origen;
- el estado activo/inactivo se interpreta como presencia o ausencia observada;
- la automatización no debe inventar métricas no soportadas por Microsoft;
- la seguridad debe impedir que el usuario final altere la automatización o la configuración de la solución.
