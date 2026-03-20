# Visión del producto

## 1. Qué es

`Agent Inventory Tenant-wide` es una extensión del enfoque CoE para visibilidad y gobierno de agentes de IA en Power Platform. Su propósito es concentrar en Dataverse un inventario utilizable por negocio, soporte, riesgo y gobierno, y exponerlo mediante una app model-driven con analítica operativa.

## 2. Problema que resuelve

Antes de una solución de este tipo, la organización suele tener estas limitaciones:

- Los agentes existen repartidos entre entornos, equipos y experiencias de creación distintas.
- No hay una vista única de propietarios, fechas, origen técnico, estado o modelo usado.
- La auditoría y el gobierno se vuelven manuales y lentos.
- El análisis de adopción y crecimiento no tiene base homogénea.
- La obsolescencia y los riesgos de agentes huérfanos pasan desapercibidos.

## 3. Por qué se hace

La solución se construye para cubrir cuatro necesidades empresariales:

1. Gobierno: saber qué agentes existen, dónde, desde cuándo y bajo qué contexto.
2. Cumplimiento: facilitar revisiones de propiedad, exposición y trazabilidad.
3. Operación: detectar altas, cambios y bajas sin trabajo manual de consolidación.
4. Adopción: medir crecimiento, distribución y uso de tecnologías de agente en el tenant.

## 4. Objetivos de negocio

- Disponer de una vista consolidada del inventario de agentes.
- Reducir silos entre entornos y equipos.
- Proveer un punto de consulta único para analistas y responsables de gobierno.
- Habilitar reporting ejecutivo y seguimiento de evolución.
- Crear una base para futuras políticas de control, certificación o remediación.

## 5. Alcance funcional deseado

La descripción de la solución apunta a un producto que debería:

- inventariar agentes de distintos orígenes,
- clasificar metadatos técnicos y operativos,
- identificar propietarios,
- permitir análisis de adopción y riesgo,
- sostener una capa de gobierno escalable.

## 6. Alcance real implementado en esta versión

Lo exportado en la versión `1.0.0.8` implementa de forma comprobable:

- una tabla de inventario `yb_agenttenantwide`,
- un flujo de sincronización que consulta `PowerPlatformResources`,
- una proyección de datos de agentes de tipo `microsoft.copilotstudio/agents`,
- una app model-driven de consulta,
- dashboards y un reporte,
- un rol de usuario de consulta con notas.

No se observa en el flujo exportado una consulta activa a otros tipos de recurso distintos de `microsoft.copilotstudio/agents`.

## 7. Usuarios objetivo

- Equipo CoE / gobierno Power Platform
- Responsables de IA y riesgo tecnológico
- Soporte funcional y técnico
- Auditores internos
- Usuarios consumidores del inventario con permiso de lectura

## 8. Beneficio esperado

- Menos dependencia de inventarios manuales.
- Mejor capacidad de revisión transversal del tenant.
- Menor tiempo para responder preguntas de gobierno.
- Mayor capacidad para detectar crecimiento, cambios o desaparición de agentes.
- Base estructurada para evolucionar hacia controles automáticos.

## 9. Indicadores clave de seguimiento

Las medidas implementadas o derivables del producto son:

- agentes creados por ejecución,
- agentes actualizados por ejecución,
- agentes eliminados por ejecución,
- agentes procesados por ejecución,
- incidencias por ejecución,
- número de agentes por `createdIn`,
- número de agentes por `modelJson`,
- evolución temporal mensual por `createdAt`.

## 10. Conclusión de producto

La solución ya funciona como inventario centralizado y capa de observabilidad básica. Sin embargo, todavía debe evolucionar para cerrar la distancia entre la visión declarada del producto y el alcance técnico actualmente implementado.

