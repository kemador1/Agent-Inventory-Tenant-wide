# KYN Agent Inventory Tenant-wide

Solución Power Platform para inventariar y gobernar agentes a nivel tenant en Microsoft Dataverse, con sincronización, trazabilidad, reporting ejecutivo y documentación completa.

---

## Índice de documentación

- [01_vision_producto.md](01_vision_producto.md)
- [02_arquitectura_funcional_y_tecnica.md](02_arquitectura_funcional_y_tecnica.md)
- [03_modelo_datos.md](03_modelo_datos.md)
- [04_flujo_inventario_y_automatizacion.md](04_flujo_inventario_y_automatizacion.md)
- [05_app_dashboards_reportes.md](05_app_dashboards_reportes.md)
- [06_seguridad_roles_y_gobierno.md](06_seguridad_roles_y_gobierno.md)
- [07_manual_usuario_final.md](07_manual_usuario_final.md)
- [08_manual_despliegue_y_configuracion.md](08_manual_despliegue_y_configuracion.md)
- [09_manual_operacion_y_mantenimiento.md](09_manual_operacion_y_mantenimiento.md)
- [10_riesgos_limitaciones_y_proximos_pasos.md](10_riesgos_limitaciones_y_proximos_pasos.md)
- [11_bienvenida_power_platform.html](11_bienvenida_power_platform.html)
- Anexos:
  - [anexos/01_diccionario_campos.md](anexos/01_diccionario_campos.md)
  - [anexos/02_variables_y_expresiones_del_flujo.md](anexos/02_variables_y_expresiones_del_flujo.md)
  - [anexos/03_matriz_de_permisos.md](anexos/03_matriz_de_permisos.md)
  - [anexos/04_iconografia_dinamica_en_formulario.md](anexos/04_iconografia_dinamica_en_formulario.md)

---

## Resumen ejecutivo

`KYN Agent Inventory Tenant-wide` es una solución destinada a centralizar el inventario y operación de agentes creados con Microsoft Copilot Studio a escala tenant, permitiendo su consulta, trazabilidad y reporting en Microsoft Dataverse para organizaciones con necesidades de gobierno y control avanzadas.

### Características principales
- Inventario automático tenant-wide de agentes tipo Copilot Studio (copilot bots).
- Sincronización y conciliación periódica con el catálogo real en Azure/Dataverse.
- Trazabilidad del ciclo de vida de cada agente (alta, cambios, baja lógica, reactivación).
- Dashboard ejecutivo y reporting reutilizable.
- Notificaciones automáticas por correo ante cambios relevantes.
- Configuración y personalización a través de variables de entorno.

---

## ¿De dónde salen los agentes y cómo se obtienen?

Los **agentes** inventariados son bots o agentes conversacionales creados desde Microsoft Copilot Studio y desplegados a nivel tenant en la organización.  
La solución obtiene la lista completa de agentes conectándose a la API oficial de Microsoft Copilot Studio:

- **Fuente:** `microsoft.copilotstudio/agents` API
- **Método:** Llamada a la API en workflows automatizados de Power Automate y Power Apps.
- **Persistencia:** Consolidación y almacenamiento en tablas de Dataverse (ej: `kyn_agenttenantwide`).

### Proceso de obtención y sincronización
1. Se ejecuta un flujo de Power Automate configurado con credenciales de servicio.
2. El flujo realiza una petición `GET` a la API `microsoft.copilotstudio/agents` para listar todos los agentes del tenant.
3. La respuesta se procesa y se sincroniza en Dataverse:
    - Agentes nuevos: se marcan como activos.
    - Agentes no presentes: se marcan como inactivos.
    - Cambios relevantes (nombre, owner, etc) se registran para trazabilidad.
4. Se generan notificaciones y actualizaciones en dashboards automáticamente.

---

## Mejoras y ampliaciones recomendadas

- Integrar filtrados sofisticados o segmentación por departamento/entorno.
- Añadir triggers avanzados (notificación por Teams, disparo al detectar baja masiva).
- Integración con CI/CD de soluciones Power Platform.
- Mejorar la auditoría e historificación de cambios (logs detallados).
- Exponer la API como microservicio REST para otros sistemas.
- Automatizar el enrolado de nuevos agentes vía flujos serverless.

---

## Documentación oficial Microsoft Copilot Studio API

- API principal utilizada: [Copilot Studio API Reference](https://learn.microsoft.com/en-us/copilot-studio/reference/api/)
- Documentación de operaciones soportadas:  
  - Listar agentes: [`GET /agents`](https://learn.microsoft.com/en-us/copilot-studio/reference/api/agents-list)
  - Crear/actualizar agentes
  - Cambiar parámetros de despliegue
  - Recuperar detalles de agente
- Parámetros principales: tenantId, agentId, state, owner, modifiedDate, etc.
- Opciones avanzadas e integración: [Microsoft Copilot Studio docs](https://learn.microsoft.com/en-us/copilot-studio/)

---

## Instalación y despliegue

1. Descarga el archivo `kynagentinventorytenantwide_*.zip` de la última release.
2. Importa la solución desde el Power Platform Admin Center (selecciona tu entorno adecuado).
3. Configura variables de entorno (correo, branding, parámetros API) y usuarios con rol adecuado.
4. Consulta la [documentación técnica](./02_arquitectura_funcional_y_tecnica.md) y los manuales para integración, operación y despliegue.

---

## Alcance y limitaciones

- **Alcance:** Descubrimiento y gestión de agentes desde Copilot Studio, almacenamiento en Dataverse, operación y reporting multi-entorno.
- **Fuera de alcance:** Administración directa del origen de los agentes (alta/baja desde la solución; esta es sólo inventario/consulta).