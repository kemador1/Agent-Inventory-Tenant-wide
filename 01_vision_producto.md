# Visión de producto

## Objetivo

`Agent Inventory Tenant-wide` es una solución de Power Platform orientada a construir y operar un inventario centralizado de agentes a nivel tenant. Su propósito es ofrecer una vista única, trazable y explotable de los agentes descubiertos en el origen soportado, consolidando el dato en Dataverse y poniéndolo a disposición de negocio, gobierno y soporte.

## Problema que resuelve

En entornos con múltiples agentes, distintos equipos y diferentes formas de creación, suele existir:

- falta de inventario único;
- ausencia de ownership técnico visible;
- baja trazabilidad sobre altas, cambios y desapariciones;
- reporting disperso o no reutilizable;
- dificultad para distinguir entre registros activos, inactivos o no observados recientemente.

La solución corrige este problema centralizando el inventario y automatizando la sincronización con un criterio operativo claro.

## Valor de negocio

- reduce el esfuerzo manual de inventariado;
- aporta una base consistente para gobierno y revisión;
- facilita análisis operativo y reporting ejecutivo;
- separa consumo del inventario de la administración técnica de la solución;
- deja evidencia explícita de qué cambios han provocado una actualización;
- mejora la adopción controlada de agentes al disponer de estado, owner y contexto técnico.

## Alcance real de la release `2.2.0.3`

Esta versión:

- descubre recursos `microsoft.copilotstudio/agents`;
- sincroniza el inventario en la tabla `kyn_agenttenantwide`;
- crea y actualiza registros con clave funcional `agentId + environmentId`;
- recalcula el estado operativo del registro en cada sincronización;
- marca como inactivo un agente no observado en la ejecución actual;
- reactiva automáticamente un agente si vuelve a aparecer;
- genera un correo operativo en español con branding por cliente o empresa;
- expone el dato mediante app model-driven, dashboards y reporte clásico;
- incluye recursos web HTML/SVG para navegación, bienvenida e iconografía.

## Qué no hace esta versión

- no crea ni modifica agentes en origen;
- no calcula coste real PAYG por agente;
- no ofrece telemetría;
- no realiza borrado físico automático del inventario;

## Resultado esperado

El resultado es un producto operativo completo para inventario y supervisión de agentes, con base de datos propia, automatización, app de consulta, visualización, controles de seguridad y documentación formal de explotación.
