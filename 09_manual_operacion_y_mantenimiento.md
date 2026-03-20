# Manual de operación y mantenimiento

## 1. Objetivo

Este documento describe cómo operar el producto, mantener su calidad y gestionar incidencias.

## 2. Modelo operativo recomendado

### Operación diaria o por ejecución

- lanzar el flujo según el calendario acordado,
- revisar el resumen de creados, actualizados, eliminados, procesados y errores,
- validar si las bajas detectadas son coherentes.

### Operación semanal

- revisar dashboards,
- detectar crecimientos anómalos,
- revisar agentes sin contexto funcional,
- comprobar si hay errores recurrentes.

### Operación mensual

- revisar configuración de connection references,
- validar destinatarios de notificación,
- revisar calidad del dato y duplicados,
- exportar versión de solución y evidencias de configuración.

## 3. Runbook de ejecución

1. Ejecutar el flujo `Agent Inventory tenant wide`.
2. Esperar a que finalice la paginación y la sincronización.
3. Revisar el correo de resultado o el historial de ejecución.
4. Analizar:
   - `created`
   - `updated`
   - `deleted`
   - `processed`
   - `errors`
5. Validar el dashboard y una muestra de registros.

## 4. Controles de salud

### Control 1. El flujo termina correctamente

Señal:

- estado de ejecución correcto,
- sin crecimiento inesperado de errores.

### Control 2. La relación `procesados` vs `eliminados` es razonable

Señal de riesgo:

- alto volumen de `deleted` respecto a histórico,
- `processed` anormalmente bajo.

### Control 3. Los dashboards muestran datos recientes

Señal:

- charts con valores consistentes con la ejecución.

### Control 4. No hay duplicados de clave funcional

Comprobar si existen varios registros con la misma combinación `agentId + environmentId`.

## 5. Incidencias comunes

### 5.1 No aparecen agentes esperados

Posibles causas:

- el flujo no se ha ejecutado,
- el alcance fuente no incluye ese tipo de agente,
- hay problemas de permisos del conector admin,
- hubo errores por agente.

### 5.2 Se eliminaron registros válidos

Posibles causas:

- la fuente devolvió visión parcial,
- hubo cambios de permisos o alcance,
- el cleanup ejecutó borrado con lista incompleta.

Acción recomendada:

- pausar ejecuciones,
- revisar histórico,
- restaurar datos si procede,
- corregir lógica antes de volver a ejecutar.

### 5.3 Los dashboards muestran categorías raras en modelo

Posible causa:

- `yb_modeljson` guarda estructura técnica o texto no normalizado.

### 5.4 El correo no llega

Posibles causas:

- variable de entorno no configurada,
- referencia de conexión de Outlook mal resuelta,
- permisos del invocador.

## 6. Mantenimiento preventivo

- revisar periódicamente límites de longitud de campos técnicos,
- verificar que la lógica de change detection sigue alineada con los campos realmente importantes,
- revisar si nuevos tipos de agente deben entrar en el inventario,
- comprobar dependencias de soluciones base tras actualizaciones de plataforma.

## 7. Mantenimiento evolutivo prioritario

- programar ejecución periódica,
- endurecer la identidad funcional con `alternate key`,
- normalizar modelos y estados,
- ampliar cobertura a más orígenes de agentes,
- auditar y endurecer borrados.

## 8. Gestión del cambio

Cada cambio debería pasar por:

1. análisis de impacto en fuente,
2. revisión de modelo de datos,
3. prueba en entorno no productivo,
4. validación de dashboards y reportes,
5. actualización de esta documentación.

## 9. Copia, recuperación y trazabilidad

Recomendaciones:

- mantener exportaciones versionadas de la solución,
- documentar valores de variables de entorno por entorno,
- mantener evidencia de connection references,
- conservar histórico de ejecuciones del flujo.

## 10. Responsabilidades sugeridas

| Rol operativo | Responsabilidad |
| --- | --- |
| Administrador Power Platform | conexiones, importación, permisos y soporte técnico |
| Owner funcional CoE | validación de alcance, calidad del inventario y roadmap |
| Analista de gobierno | consumo, revisión, anotación y escalado |

