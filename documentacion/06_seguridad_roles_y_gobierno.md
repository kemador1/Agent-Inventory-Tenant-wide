# Seguridad, roles y gobierno

## Rol principal de consulta

- Nombre: `KYN Agent Inventory Reader ROLE`
- Id: `{94fb8dce-ab35-4185-b5d3-744b74be8276}`

## Qué permite

- leer la tabla `kyn_agenttenantwide`;
- abrir la app y dashboards;
- consultar el reporte;
- crear y mantener notas;
- acceder a vistas y gráficos.

## Qué no permite

- crear registros de agentes manualmente;
- editar registros del inventario;
- borrar registros del inventario;
- modificar la definición de los flujos;
- modificar agentes en la plataforma origen.

## Principio de control

El usuario final consume y comenta el inventario; no administra la infraestructura de automatización ni la configuración de agentes.

## Separación de responsabilidades

### Usuario final / analista

- consulta;
- filtra;
- exporta;
- anota hallazgos;
- solicita revisión.

### Administrador funcional

- completa owner funcional;
- valida criticidad;
- decide estado de revisión;
- interpreta resultados.

### Administrador técnico / CoE

- importa la solución;
- mantiene connection references;
- ejecuta y supervisa flujos;
- corrige errores operativos;
- evoluciona el modelo.

## Gobierno del dato

- la automatización rellena estados iniciales;
- la curación humana prevalece cuando ya existe valor no inicial;
- toda revisión relevante queda en Dataverse y puede auditarse.
