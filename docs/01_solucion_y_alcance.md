# Solución y alcance

## Objetivo

`Agent Inventory Tenant-wide` es una solución Power Platform diseñada para centralizar el inventario de agentes a nivel tenant, normalizar su visibilidad operativa y ofrecer una experiencia de consulta y seguimiento desde una app model-driven.

El flujo principal consulta recursos del tenant, sincroniza los datos en Dataverse, detecta altas, cambios y registros ausentes, y después emite un correo de resumen a los destinatarios suscritos.

## Alcance funcional actual

La solución actual cubre estos escenarios:

- descubrimiento periódico de agentes mediante conector Power Platform Admin;
- consolidación de inventario en Dataverse;
- actualización de registros existentes;
- creación de registros nuevos;
- marcado de registros ausentes o no detectados en la ejecución actual;
- navegación de los datos desde app model-driven y dashboard;
- suscripción de destinatarios de correo mediante tabla dedicada;
- envío de un resumen diario por correo electrónico.

## Componentes incluidos

### Dataverse

- `kyn_agenttenantwide`
  - inventario principal de agentes.
- `kyn_suscripcionesdeinformes`
  - lista de destinatarios para el resumen por correo.

### Automatización

- flujo Power Automate:
  - `KYN Agent Inventory tenant-wide`

### Experiencia de usuario

- app model-driven:
  - `kyn_AgentControlHubtenantwide`
- dashboard:
  - `Agent Inventory – Tenant Overview`
- informe:
  - reporte RDL incluido en `Reports/`

### Recursos visuales

Web resources identificados:

- `kyn_Bienvenida_Agent_Inventory`
- `kyn_chatgpt_icon`
- `kyn_claude_ai_icon`
- `kyn_copilot_icon`
- `kyn_copilo_ticon`
- `kyn_dashboard`
- `kyn_kyn_agent_model_icon`
- `kyn_kyn_agent_model_icon_host`
- `kyn_Report_Subscriptions`

## Público objetivo

- responsables de gobierno de Power Platform;
- equipos de arquitectura y cumplimiento;
- administradores del tenant;
- usuarios autorizados que consumen el inventario desde la app;
- destinatarios del resumen operacional por correo.

## Alcance técnico observado

La solución actual está exportada como paquete `managed` y se encuentra descomprimida en la raíz del repositorio. Esto tiene implicaciones importantes:

- `solution.xml` y `customizations.xml` son la referencia principal del estado actual;
- cualquier discrepancia entre estos XML y el contenido del flujo JSON debe considerarse deuda técnica;
- la documentación debe basarse en lo que realmente existe hoy, no en iteraciones anteriores ni en intenciones de diseño no materializadas.
