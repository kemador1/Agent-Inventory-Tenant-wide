# App, dashboards y reportes

## 1. App model-driven

- Nombre visible: `Agent Inventory tenant wide APP`
- Nombre lógico: `cr1d7_AgentControlHubtenantwide`
- Sitemap: `Agent Control Hub tenant-wide`

## 2. Navegación

La navegación expone dos entradas:

- `Dashboard`
- `Agents`

Esto confirma que la experiencia está diseñada para consumo y análisis del inventario, no para mantenimiento directo de registros por parte del usuario final.

## 3. Formularios de la entidad

La tabla `yb_agenttenantwide` contiene:

- formulario card `Information`
- formulario principal `Information`
- quick form `Information`

El formulario principal muestra:

- el conjunto de campos técnicos del inventario,
- un control de notas/timeline en la columna derecha.

La app tiene además `msdyn_TimelineModernization = true`, lo que refuerza la intención de uso colaborativo mediante notas.

## 4. Vistas incluidas

| Vista | Propósito |
| --- | --- |
| `Active agent tenant wides` | Vista principal operativa |
| `Inactive agent tenant wides` | Registros inactivos |
| `My agent tenant wides` | Registros propios |
| `agent tenant wide Associated View` | Relacionadas |
| `agent tenant wide Lookup View` | Lookup |
| `agent tenant wide Advanced Find View` | Advanced Find |
| `Quick Find Active agent tenant wides` | Búsqueda rápida |

## 5. Dashboard clásico

Nombre: `Agent Inventory – Tenant Overview`

Componentes:

- chart `agent by createdIn`
- chart `agentId by createdAt and createdIn`
- chart `agent by model`
- grid de `Active agent tenant wides`

Uso recomendado:

- análisis operativo,
- revisión rápida de distribución,
- entrada a registros detallados.

## 6. Dashboard ejecutivo

Nombre: `Agent Inventory – Overview Ejecutivo Tenant-wide`

Componentes:

- tres charts como filtros visuales,
- stream basado en la vista activa.

Uso recomendado:

- revisión ejecutiva,
- exploración filtrada por dimensiones clave,
- seguimiento temporal y de distribución.

## 7. Visualizaciones y medidas

| Visualización | Medida | Dimensión |
| --- | --- | --- |
| `agent by model` | `count(yb_agentid)` | `yb_modeljson` |
| `agent by createdIn` | `count(yb_agentid)` | `yb_createdin` |
| `agentId by createdAt and createdIn` | `count(yb_agentid)` | `yb_createdat` por mes, segmentado por `yb_createdin` |

Observaciones:

- `yb_modeljson` se usa como dimensión analítica aunque conceptualmente contiene un JSON o estructura técnica.
- Si el valor es largo o no normalizado, la calidad de la visualización puede degradarse.

## 8. Reporte

Nombre: `Inventario de Agentes Tenant-wide`

Características observadas:

- entidad base: `yb_agenttenantwide`
- columnas visibles: `yb_name`, `yb_displayname`
- agrupaciones: `yb_createdin`, `yb_modeljson`, `yb_createdby`
- descripción orientada a visibilidad de propietario, estado, tipo y fechas

## 9. Lectura funcional del front

La experiencia de usuario responde a un patrón de consumo:

- entrar por dashboard,
- filtrar o explorar por vistas,
- abrir ficha del agente,
- añadir notas o contexto,
- consultar reporte si aplica.

No se observan comandos o artefactos de edición avanzada del inventario dentro del paquete exportado.

