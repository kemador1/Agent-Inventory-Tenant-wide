# Manual de usuario final

## 1. Objetivo del manual

Este manual describe cómo usar el producto como consumidor del inventario, sin asumir permisos de administración.

## 2. Perfil al que aplica

- usuarios con acceso a la app,
- analistas,
- responsables de gobierno,
- soporte funcional con rol de consulta.

## 3. Qué encontrará el usuario

La app ofrece:

- un dashboard de entrada,
- acceso a la lista de agentes,
- fichas detalladas de cada agente,
- gráficos de distribución,
- posibilidad de registrar notas,
- reporte del inventario.

## 4. Acceso

1. Abrir la app `Agent Inventory tenant wide APP`.
2. Entrar en `Dashboard` para obtener una visión general.
3. Ir a `Agents` para navegar por el inventario detallado.

## 5. Uso del dashboard

En el dashboard el usuario puede:

- ver el número de agentes por origen (`createdIn`),
- revisar la evolución temporal por mes,
- visualizar la distribución por modelo,
- abrir el grid de agentes activos.

Uso recomendado:

- empezar por el dashboard para detectar áreas relevantes,
- aplicar filtros visuales si se usa el dashboard ejecutivo,
- después abrir registros concretos.

## 6. Uso de la lista de agentes

Desde `Agents`, el usuario puede:

- cambiar de vista,
- usar búsqueda rápida,
- ordenar columnas,
- abrir un agente concreto para revisar detalle.

## 7. Lectura de la ficha de agente

La ficha principal muestra, entre otros:

- nombre y display name,
- identificadores del agente y del entorno,
- creador y propietario resueltos,
- fechas de creación y última publicación,
- tipo de recurso,
- schema name,
- estado de cuarentena,
- metadatos técnicos,
- panel de notas.

## 8. Uso de notas

El usuario sí puede:

- crear notas,
- editar notas,
- dejar observaciones funcionales,
- documentar hallazgos o incidencias.

Buenas prácticas:

- usar notas para contextualizar riesgos, revisiones o validaciones,
- no usar notas para corregir datos maestros del inventario,
- incluir fecha y motivo del comentario.

## 9. Uso de reportes

Si el reporte está visible y publicado en el entorno, el usuario puede:

- abrir `Inventario de Agentes Tenant-wide`,
- consultar agrupaciones por `createdIn`, `modelJson` y `createdBy`,
- exportar o revisar resultados según los permisos del entorno.

## 10. Qué puede hacer y qué no puede hacer

### Puede

- consultar inventario,
- filtrar y buscar,
- analizar dashboards,
- leer reportes,
- registrar notas.

### No puede

- crear agentes en la tabla,
- modificar campos del agente,
- borrar registros del inventario,
- alterar el flujo de sincronización,
- cambiar la lógica de gobierno.

## 11. Comportamientos esperables

- Si abre un registro, verá campos mayoritariamente informativos.
- Si intenta modificar la ficha del agente, el rol no debería permitir persistir cambios en la entidad.
- Sí podrá trabajar sobre notas porque el rol lo habilita.

## 12. Preguntas frecuentes

### ¿Por qué no puedo editar un agente?

Porque el inventario es gestionado por sincronización automática y el rol no concede permisos de escritura sobre `yb_agenttenantwide`.

### ¿Puedo crear observaciones sobre un agente?

Sí. Debe usar notas en la ficha del registro.

### ¿Los datos cambian en tiempo real?

No necesariamente. Dependen de la última ejecución del flujo de inventario.

### ¿Qué hago si un agente no aparece?

Debe reportarlo al equipo administrador, porque puede deberse a sincronización, alcance de descubrimiento o permisos.

## 13. Recomendaciones al usuario final

- usar siempre dashboards y vistas antes de sacar conclusiones,
- comprobar si el dato observado parece consistente con la última actualización,
- usar notas para enriquecer el contexto,
- escalar al administrador cualquier corrección estructural.

