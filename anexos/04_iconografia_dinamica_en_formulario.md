# Iconografía dinámica en formulario

## Objetivo

Mostrar un icono SVG en el formulario del agente según el contenido de `kyn_modeljson` o `kyn_modelprovider`, sin depender de Power Automate.

## Componentes propuestos

- JavaScript de formulario: `form_webresources/kyn_agent_model_icon.js`
- HTML host del icono: `form_webresources/kyn_agent_model_icon_host.html`
- SVG ya cargados en Dataverse:
  - `kyn_chatgpt_icon`
  - `kyn_claude_ai_icon`
  - `kyn_copilot_icon`

## Cómo funciona

1. El script lee `kyn_modelprovider` y `kyn_modeljson`.
2. Intenta resolver proveedor y modelo.
3. Si el proveedor es conocido, carga el SVG correspondiente.
4. Si no reconoce el proveedor o el SVG falla, pinta un fallback visual genérico.

## Mapeo actual

- `OpenAI` -> `kyn_chatgpt_icon`
- `Anthropic` -> `kyn_claude_ai_icon`
- `Microsoft` -> `kyn_copilot_icon`
- `Google`, `Meta` u otros -> fallback visual

## Cableado recomendado en el formulario

### Web resource HTML

Insertar un recurso web HTML en el formulario principal con nombre de control:

- `WebResource_ModelIcon`

El nombre del recurso web debe coincidir con:

- `kyn_agent_model_icon_host.html`

### Biblioteca JavaScript

Agregar como biblioteca:

- `kyn_agent_model_icon.js`

### Eventos

- `OnLoad` del formulario:
  - función: `KYNAgentModelIcon.refreshIcon`
  - pasar `executionContext`: `Sí`

- `OnChange` de `kyn_modeljson`:
  - función: `KYNAgentModelIcon.refreshIcon`
  - pasar `executionContext`: `Sí`

- `OnChange` de `kyn_modelprovider`:
  - función: `KYNAgentModelIcon.refreshIcon`
  - pasar `executionContext`: `Sí`

## Observaciones

- no requiere flow;
- no modifica datos;
- solo resuelve presentación en el formulario;
- si más adelante cargas SVG para Google o Meta, basta con ampliar el diccionario `iconMap` del JavaScript.
