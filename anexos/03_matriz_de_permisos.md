# Matriz de permisos del rol custom

## Principio general

El rol custom de consulta está orientado a permitir consumo del inventario, no administración de la solución ni del origen.

## Matriz funcional

| Capacidad | Resultado esperado |
| --- | --- |
| Leer registros de `kyn_agenttenantwide` | permitido |
| Abrir la app model-driven | permitido |
| Consultar dashboards | permitido |
| Consultar el reporte clásico | permitido |
| Ver formularios y vistas | permitido |
| Crear notas | permitido |
| Editar notas propias o permitidas | permitido |
| Exportar datos visibles | permitido según privilegio de lectura |
| Crear registros manuales de agentes | no permitido |
| Editar inventario de agentes | no permitido para perfil lector |
| Borrar inventario de agentes | no permitido |
| Modificar flujos | no permitido |
| Modificar variables de entorno | no permitido |
| Modificar connection references | no permitido |
| Modificar agentes en origen | no permitido |

## Lectura organizativa

- usuario final: consulta y documenta;
- analista: filtra, exporta y revisa;
- administrador funcional: puede complementar gobierno si la organización lo define;
- administrador técnico: mantiene solución, conexiones y automatización.
