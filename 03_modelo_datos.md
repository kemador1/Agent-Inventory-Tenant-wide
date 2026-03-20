# Modelo de datos

## 1. Tabla principal

- Nombre lógico: `yb_agenttenantwide`
- Nombre visible: `Agent tenant wide`
- Entity set: `yb_agenttenantwides`
- Tipo de propiedad: `UserOwned`
- Versión introducida: `1.0`
- Notas: habilitadas
- Auditoría: no habilitada en la tabla exportada

## 2. Finalidad de la tabla

La tabla representa el inventario consolidado de agentes detectados en el tenant. Cada registro pretende reflejar el estado más reciente conocido de un agente, con metadatos suficientes para consulta, reporting y gobierno básico.

## 3. Clave funcional

La implementación usa como clave funcional de matching:

- `yb_agentid`
- `yb_environmentid`

No existe una clave alterna declarada en Dataverse. Eso implica:

- riesgo de duplicados si se ejecutan cargas concurrentes,
- riesgo de inserciones repetidas si el matching falla,
- ausencia de protección dura a nivel de base de datos.

## 4. Familias de campos

### Identificación

- `yb_name`
- `yb_agentid`
- `yb_resourceid`
- `yb_resourcetype`
- `yb_environmentid`
- `yb_tenantid`

### Presentación y propiedad

- `yb_displayname`
- `yb_createdby`
- `yb_ownerid`

### Trazabilidad temporal

- `yb_createdat`
- `yb_lastpublishedat`
- `yb_createdin`

### Metadatos técnicos

- `yb_schemaname`
- `yb_entraappid`
- `yb_isquarantined`
- `yb_modeljson`
- `yb_orchestrationjson`
- `yb_authenticationjson`

## 5. Decisiones de modelado observadas

### 5.1 El nombre funcional se almacena en dos campos

- `yb_name`: se rellena con `displayName`
- `yb_displayname`: también se rellena con `displayName`

Esto facilita vistas y formularios, pero duplica semántica.

### 5.2 Propietarios y creadores se almacenan como texto

`yb_createdby` y `yb_ownerid` no son lookups a usuario. El flujo intenta resolver el `displayName` del usuario con Office 365 Users y guarda ese valor como texto. Si no puede resolverlo, guarda el valor original recibido.

Implicaciones:

- buena legibilidad para consulta,
- baja capacidad para relacionar contra seguridad real,
- pérdida de trazabilidad fuerte por GUID.

### 5.3 El booleano se serializa como cadena

`yb_isquarantined` se persiste como `'1'` o `'0'`, no como tipo booleano nativo.

### 5.4 Campos JSON con longitud reducida

Los campos:

- `yb_modeljson`
- `yb_orchestrationjson`
- `yb_authenticationjson`

están modelados como `nvarchar(100)`. Para datos que conceptualmente son JSON, esto es una restricción severa.

Implicaciones:

- truncado potencial,
- pérdida de fidelidad semántica,
- charts y filtros sobre información posiblemente incompleta,
- riesgo de error si la API devuelve valores mayores.

## 6. Campos técnicos con especial relevancia

| Campo | Observación de diseño |
| --- | --- |
| `yb_resourceid` | Es `ntext` con capacidad mayor que el resto de campos técnicos y se usa en detección de cambios |
| `yb_createdat` | Solo se actualiza si el flujo entra en rama de update |
| `yb_lastpublishedat` | Se escribe, pero no forma parte de la condición de cambio |
| `yb_modeljson` | Además de persistencia, se usa como dimensión analítica del chart `agent by model` |
| `yb_createdin` | Se usa en charts y en el reporte |

## 7. Comportamiento de actualización

La condición de cambio del flujo compara estos campos:

- `yb_displayname`
- `yb_location`
- `yb_createdin`
- `yb_schemaname`
- `yb_entraappid`
- `yb_orchestrationjson`
- `yb_authenticationjson`
- `yb_modeljson`
- `yb_isquarantined`
- `yb_resourceid`
- `yb_resourcetype`
- `yb_tenantid`
- `yb_environmentid`

Campos que se escriben pero no disparan update por sí solos:

- `yb_name`
- `yb_createdat`
- `yb_createdby`
- `yb_ownerid`
- `yb_lastpublishedat`

Esto genera una limitación: si cambia solo uno de esos campos omitidos, el registro puede quedar desactualizado.

## 8. Estado y ciclo de vida del registro

La tabla usa `statecode` y `statuscode` estándar de Dataverse. Las vistas activas e inactivas existen en la app, pero la solución no añade estados de negocio específicos sobre el inventario.

## 9. Recomendación de evolución del modelo

- Crear `alternate key` sobre `yb_agentid + yb_environmentid`
- Convertir `yb_isquarantined` a tipo booleano o choice
- Separar JSON crudo de atributos analíticos normalizados
- Guardar `ownerId` y `createdBy` originales en GUID además del nombre mostrado
- Habilitar auditoría en la tabla

El detalle campo por campo se encuentra en [anexos/01_diccionario_campos.md](anexos/01_diccionario_campos.md).

