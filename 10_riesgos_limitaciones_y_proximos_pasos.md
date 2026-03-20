# Riesgos, limitaciones y próximos pasos

## 1. Riesgos y limitaciones actuales

| Tema | Evidencia observada | Impacto | Acción recomendada |
| --- | --- | --- | --- |
| Cobertura real menor que la visión | La consulta del flujo filtra solo `microsoft.copilotstudio/agents` | El producto no inventaria todo el universo deseado | ampliar conectores y lógica de descubrimiento |
| Trigger manual | El flujo usa disparador `Button` | No hay sincronización periódica nativa | añadir scheduling |
| Borrado por visión parcial | Cleanup elimina cualquier registro no procesado | Riesgo de bajas falsas | introducir soft delete, doble validación o umbral de protección |
| Sin alternate key | Matching solo lógico por `agentId + environmentId` | Riesgo de duplicados | crear clave alterna en Dataverse |
| JSON en 100 caracteres | `yb_modeljson`, `yb_orchestrationjson`, `yb_authenticationjson` son `nvarchar(100)` | truncado y analítica pobre | ampliar capacidad o desnormalizar |
| Change detection incompleta | No compara `createdBy`, `ownerId`, `createdAt`, `lastPublishedAt`, `yb_name` | inventario potencialmente desactualizado | alinear condición con payload de update |
| Sin auditoría | `IsAuditEnabled=0` | menor trazabilidad de cambios | habilitar auditoría |
| Dependencias faltantes | Solución declara missing dependencies | riesgo de UX incompleta o importación parcial | resolver prerequisitos de plataforma |

## 2. Deuda funcional detectada

- La descripción del producto promete una cobertura más amplia que la implementada.
- La capa analítica se apoya en campos técnicos poco normalizados.
- La operación de borrado es demasiado agresiva para un inventario de gobierno.

## 3. Próximos pasos prioritarios

### Prioridad alta

1. Programar el flujo.
2. Incorporar `alternate key`.
3. Desactivar borrado duro o protegerlo con validaciones.
4. Corregir la condición de detección de cambios.
5. Ampliar longitud de campos que guardan JSON.

### Prioridad media

1. Normalizar dimensiones analíticas:
   - modelo,
   - origen,
   - estado de cuarentena,
   - tipo de agente.
2. Guardar identificadores técnicos y nombres resueltos por separado.
3. Añadir auditoría y control de versiones del inventario.

### Prioridad estratégica

1. Ampliar descubrimiento a más orígenes de agente.
2. Incorporar clasificación de riesgo o certificación.
3. Añadir indicadores de uso, criticidad, owner funcional y estado de revisión.
4. Preparar reporting ejecutivo más robusto y exportable.

## 4. Roadmap sugerido

### Fase 1. Estabilización

- scheduling
- clave alterna
- revisión de campos
- hardening del cleanup

### Fase 2. Calidad del dato

- normalización
- auditoría
- catálogo de orígenes y modelos
- enriquecimiento de metadatos

### Fase 3. Gobierno avanzado

- scoring de riesgo
- certificación de agentes
- workflows de revisión
- reporting de cumplimiento

## 5. Criterios de madurez objetivo

La solución debería considerarse madura cuando:

- inventarie más de un origen de agente,
- tenga ejecución programada estable,
- no permita duplicados,
- no pueda borrar masivamente por visión parcial,
- disponga de datos analíticos normalizados,
- tenga manuales y operación formalizados.

