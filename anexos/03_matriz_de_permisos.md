# Matriz de permisos del rol `Usuario Basico Agent Tenant-Wide ROLE`

## 1. Resumen ejecutivo

El rol está orientado a consulta y colaboración ligera sobre notas. No concede mantenimiento sobre la tabla de inventario.

## 2. Entidad `yb_agenttenantwide`

| Privilegio | Nivel |
| --- | --- |
| `Read` | Global |
| `Append` | Global |
| `Append To` | Global |
| `Create` | No concedido |
| `Write` | No concedido |
| `Delete` | No concedido |
| `Assign` | No concedido |
| `Share` | No concedido |

## 3. Notas

| Privilegio | Nivel |
| --- | --- |
| `CreateNote` | Global |
| `ReadNote` | Global |
| `WriteNote` | Global |
| `DeleteNote` | Basic |
| `AppendNote` | Global |
| `AppendToNote` | Global |

## 4. Reportes y experiencia de consulta

| Privilegio | Nivel |
| --- | --- |
| `ReadReport` | Basic |
| `ReadSavedQueryVisualizations` | Global |
| `ReadSystemForm` | Global |
| `ReadQuery` | Global |
| `ReadAppModule` | Global |

## 5. Workflows y procesos

| Privilegio | Nivel |
| --- | --- |
| `prvFlow` | Global |
| `prvWorkflowExecution` | Global |
| `prvReadWorkflow` | Global |
| `prvReadWorkflowSession` | Global |
| `prvCreateWorkflow` | Basic |
| `prvWriteWorkflow` | Basic |
| `prvDeleteWorkflow` | Basic |

## 6. Lectura práctica de permisos

### Permitido

- consultar inventario,
- abrir formularios y dashboards,
- crear y editar notas,
- leer reportes y charts.

### No permitido sobre inventario

- crear registros de agentes,
- editar registros de agentes,
- borrar registros de agentes.

## 7. Conclusión

La matriz de permisos es coherente con un rol de usuario final o analista de consulta, no con un rol de administrador de inventario.

