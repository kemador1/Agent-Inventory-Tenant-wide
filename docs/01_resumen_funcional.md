# 01 - Resumen funcional

## Proposito

`Agent Inventory Tenant-wide` es una solucion de gobierno y observabilidad sobre agentes desplegados en el tenant. Su funcion principal es consolidar informacion tecnica y operativa en Dataverse, exponerla en una app model-driven y distribuir reportes segun reglas de suscripcion gestionadas por los propios usuarios autorizados.

## Alcance funcional

- Inventario centralizado de agentes en una tabla maestra.
- Persistencia consistente de metadatos relevantes para gobierno y seguimiento.
- App model-driven para consulta de inventario y administracion de suscripciones.
- Flujo automatizado de sincronizacion e informes.
- Modelo de suscripcion por usuario para controlar si recibe reporte y que tipo de contenido recibe.

## Problema de negocio que resuelve

Antes de esta solucion, la visibilidad sobre agentes podia quedar distribuida en varias fuentes, con trazabilidad limitada y sin una forma coherente de informar a cada interesado. La solucion elimina ese desacoplamiento y establece una capa unica de control:

- una fuente maestra de inventario;
- una experiencia operacional unica dentro de Power Platform;
- una politica de reporte gestionada desde la propia app.

## Capacidades principales

### Inventario tenant-wide

El flujo principal consulta el origen definido, procesa cada registro y sincroniza la tabla `kyn_agenttenantwide`. La intencion de diseno es que la tabla conserve los atributos realmente relevantes del origen y no se convierta en un contenedor generico sin gobierno.

### Suscripciones de reportes

La tabla `kyn_suscripcionesdeinformes` centraliza la configuracion de distribucion:

- `kyn_name`: identificador funcional del registro;
- `kyn_recipientemail`: destinatario real;
- `kyn_reportmodecode`: modo de reporte soportado por la solucion;
- `kyn_reportmode`: compatibilidad heredada para fallback.

### Modos de reporte

La solucion trabaja con modos claros de consumo:

- `148250000`: Complete report (all agents)
- `148250001`: Created agents only
- `148250002`: Created by users (exclude system)
- `148250003`: Changes only since last run
- `148250004`: Do not send report

## Resultado esperado

El resultado esperado no es solo un flujo que funciona. El resultado esperado es una solucion de Power Platform coherente, donde:

- el modelo de datos soporta el flujo;
- la app soporta la operacion;
- las suscripciones soportan la comunicacion;
- la documentacion soporta despliegue, soporte y evolucion.
