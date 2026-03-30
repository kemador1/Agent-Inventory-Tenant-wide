# 03 - Modelo de datos y gobierno

## Objetivo del modelo

El modelo de datos esta orientado a representar inventario y configuracion operativa sin introducir campos redundantes o residuos de iteraciones anteriores.

## Entidades principales

### `kyn_agenttenantwide`

Tabla maestra de inventario. Su responsabilidad es almacenar los atributos consolidados del agente detectado por la consulta tenant-wide y servir de base a vistas, dashboards, filtros y reportes.

Categorias de informacion representadas en esta tabla:

- identificacion del agente;
- metadatos de publicacion;
- origen y ubicacion;
- datos de propietario o creador;
- indicadores tecnicos y de estado;
- informacion de sincronizacion.

### `kyn_suscripcionesdeinformes`

Tabla de configuracion de suscripciones. Su responsabilidad es definir quien recibe informe y bajo que criterio.

Campos funcionales clave:

- `kyn_name`
- `kyn_recipientemail`
- `kyn_reportmodecode`
- `kyn_reportmode`

## Gobierno del dato

### Regla 1. Coherencia de nombres

Siempre que sea posible, los nombres funcionales deben alinearse con el significado real del dato procedente de la consulta. Si se introduce una columna nueva, debe existir una justificacion funcional o tecnica.

### Regla 2. No arrastrar columnas obsoletas

Campos legacy o normalizados que ya no se usan no deben seguir apareciendo en:

- tablas;
- formularios;
- vistas;
- fetchxml;
- componentes de app.

### Regla 3. Suscripciones como configuracion, no como presentacion

Las reglas de correo no pertenecen al HTML del reporte. Pertenecen al modelo de datos y a la app.

## Modos de reporte como dato gobernado

El modo de reporte debe estar gobernado mediante choice:

- evita texto libre inconsistente;
- permite control de valores soportados;
- mejora validacion del flujo;
- reduce errores de importacion y de operacion.

## Riesgos de gobierno identificados

- vistas con atributos de una entidad equivocada;
- formularios que conservan controles de campos retirados;
- dependencia de columnas legacy sin plan de retirada;
- configuraciones de notificacion fuera del modelo oficial.

## Recomendacion operativa

Todo cambio futuro en el modelo debe validarse con una lista minima:

1. la columna existe en Dataverse;
2. la vista correcta la referencia;
3. el formulario correcto la presenta;
4. el flujo correcto la consume;
5. la documentacion correcta la describe.
