# Seguridad, roles y gobierno

## 1. Rol custom incluido

- Nombre: `Usuario Basico Agent Tenant-Wide ROLE`
- Id: `{0c003242-a423-f111-8341-6045bd09194b}`

## 2. Principio de acceso implementado

El rol custom está diseñado como rol de consumo del inventario:

- puede leer los registros de agentes,
- puede trabajar con notas,
- puede acceder a formularios, vistas y visualizaciones,
- no puede modificar directamente la entidad de inventario.

## 3. Permisos funcionales sobre la entidad `yb_agenttenantwide`

Privilegios observados:

- `Read`: sí, global
- `Append`: sí, global
- `Append To`: sí, global
- `Create`: no
- `Write`: no
- `Delete`: no
- `Assign`: no
- `Share`: no

Conclusión:

El usuario final con este rol puede consultar el inventario, pero no alterar los registros de agentes.

## 4. Permisos sobre notas

Privilegios observados:

- `CreateNote`: sí, global
- `ReadNote`: sí, global
- `WriteNote`: sí, global
- `DeleteNote`: sí, básico
- `AppendNote`: sí, global
- `AppendToNote`: sí, global

Conclusión:

El usuario puede documentar contexto operativo mediante notas, que es coherente con el diseño del formulario principal.

## 5. Permisos sobre reporting y experiencia de app

Privilegios observados:

- `ReadReport`: sí, básico
- `ReadSavedQueryVisualizations`: sí, global
- `ReadSystemForm`: sí, global
- `ReadAppModule`: sí, global
- `ReadQuery`: sí, global

Esto habilita consumo de la app, vistas, dashboards y visualizaciones.

## 6. Qué puede hacer el usuario final

- Abrir la app.
- Navegar por dashboards y vistas.
- Buscar agentes.
- Abrir el detalle del registro.
- Crear y editar notas.
- Leer reportes y visualizaciones disponibles.

## 7. Qué no puede hacer el usuario final

- Crear agentes manualmente en `yb_agenttenantwide`
- Editar campos del inventario
- Borrar registros del inventario
- Reasignar o compartir registros de agentes
- Corregir datos maestros del inventario desde la ficha

## 8. Implicación de gobierno

El producto separa correctamente:

- mantenimiento técnico del inventario,
- consumo y anotación por usuarios de negocio o analistas.

Eso reduce el riesgo de manipulación manual del inventario sincronizado.

## 9. Matiz importante

El rol custom sí incluye varios privilegios de workflow/flow y procesos generales. Eso no significa automáticamente que el usuario pueda alterar la tabla del inventario; la restricción fuerte está en la ausencia de privilegios de create/write/delete sobre `yb_agenttenantwide`.

## 10. Recomendaciones de gobierno

- Reservar la ejecución y mantenimiento del flujo a un grupo administrado.
- Asignar el rol custom a consumidores del inventario y analistas.
- Revisar si los privilegios de workflow del rol pueden endurecerse sin romper la experiencia.
- Mantener segregación entre administración de la solución y consumo funcional.

La matriz detallada de privilegios está en [anexos/03_matriz_de_permisos.md](anexos/03_matriz_de_permisos.md).

