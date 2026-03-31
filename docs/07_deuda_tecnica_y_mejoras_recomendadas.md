# Deuda técnica y mejoras recomendadas

## Principio

Esta sección no describe una intención futura abstracta. Recoge mejoras derivadas del estado real actual del repositorio y de la solución exportada.

## Hallazgos actuales

### 1. Variables legacy todavía presentes en el flujo

Detectadas en el workflow JSON:

- `Initialize_variable_varDebugLog`
- `Init_varCreatedAgentsHtml`
- `Init_varCreatedNonSystemHtml`

Impacto:

- añaden complejidad;
- dificultan mantenimiento;
- contradicen el objetivo de correo ejecutivo simplificado.

Recomendación:

- retirarlas junto con cualquier acción que dependa de ellas.

### 2. Web resource residual de suscripciones

Detectado en `solution.xml` y en `WebResources/`:

- `kyn_Report_Subscriptions`

Impacto:

- confunde la arquitectura funcional;
- duplica posibles enfoques de gestión de suscripciones;
- puede generar problemas de importación si no está alineado con la app.

Recomendación:

- retirarlo si la gestión ya es model-driven;
- si todavía se usa, documentar exactamente su ubicación y propósito.

### 3. Inconsistencia entre parámetros del flujo y variables exportadas

El flujo referencia:

- `kyn_UrlAppGeneralAgentInventory`
- `kyn_UrlVistaAgentesCreadosAgentInventory`
- `kyn_UrlVistaAgentesEliminadosAgentInventory`

Pero en el repositorio solo existe:

- `kyn_ClienteoEmpresaInformesflujo`

Impacto:

- despliegues incompletos;
- correos sin enlaces o con comportamiento inconsistente;
- documentación difícil de sostener.

Recomendación:

- exportar también esas variables de entorno;
- o eliminar su uso del flujo si el diseño final no las necesita.

### 4. Columnas legacy en `kyn_agenttenantwide`

Detectadas:

- `kyn_modelNormalized`
- `kyn_originNormalized`

Impacto:

- ruido en el modelo;
- posibilidad de vistas/formularios inconsistentes;
- dificultad para saber qué campos son canónicos.

Recomendación:

- confirmar si todavía tienen uso real;
- si no lo tienen, retirarlas de formularios, vistas, flujo y metadatos.

### 5. Mezcla de responsabilidades en un solo flujo

El flujo actual hace:

- descubrimiento;
- enriquecimiento básico;
- persistencia;
- limpieza;
- notificación.

Impacto:

- más difícil de activar, probar y mantener;
- más difícil de aislar fallos;
- mayor fragilidad al tocar solo el bloque de correo.

Recomendación:

- separar en una siguiente versión:
  - sincronización de inventario;
  - notificación por correo.

## Priorización recomendada

### Prioridad alta

1. eliminar variables legacy del flujo;
2. alinear variables de entorno;
3. decidir el destino de `kyn_Report_Subscriptions`;
4. verificar activación estable del flujo.

### Prioridad media

1. limpiar columnas legacy del modelo;
2. revisar formularios y vistas para asegurar coherencia con el modelo actual;
3. simplificar HTML del correo si sigue creciendo.

### Prioridad estructural

1. separar sincronización y notificación;
2. considerar una tabla de ejecuciones o cola de reportes si se quiere desacoplar bien el envío;
3. regenerar una versión de solución saneada y coherente con la documentación.

## Criterio de calidad para la siguiente versión

La siguiente versión debería cumplir como mínimo:

- sin residuos de `reportmode` si ya no existe funcionalmente;
- sin web resources huérfanos;
- con variables de entorno exportadas de forma completa;
- con flujo activable sin expresiones parcheadas a posteriori;
- con documentación alineada exactamente con el contenido del paquete.
