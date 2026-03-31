# App, dashboard y seguridad

## App model-driven

Componente:

- `kyn_AgentControlHubtenantwide`

Función:

- ofrecer la experiencia principal de navegación de la solución;
- exponer el inventario de agentes;
- exponer la tabla de suscripciones;
- servir como punto de entrada operativo para usuarios autorizados.

## Navegación observada

En el sitemap se identifican al menos estas áreas:

- dashboard;
- entidad `kyn_agenttenantwide`;
- entidad `kyn_suscripcionesdeinformes`.

Esto es consistente con el objetivo funcional:

- consultar inventario;
- revisar panel de situación;
- mantener destinatarios del informe.

## Dashboard

Componente:

- `Agent Inventory – Tenant Overview`

Función:

- condensar visualmente el estado del inventario;
- dar acceso a vistas agregadas sin entrar directamente a la tabla.

## Seguridad

Rol identificado:

- componente raíz tipo `20` con id `{94fb8dce-ab35-4185-b5d3-744b74be8276}`

En `customizations.xml` se observan privilegios sobre:

- lectura de app module;
- lectura de `kyn_agenttenantwide`;
- privilegios estándar de workflow y configuración de usuario;
- privilegios globales relevantes de append/append to.

## Enfoque recomendado de seguridad

La seguridad funcional debería seguir este criterio:

- lectores:
  - acceso de lectura al inventario;
  - acceso al dashboard;
  - acceso a la app;
- operadores:
  - además, mantenimiento de suscripciones;
- administradores:
  - gobierno del flujo, conexiones y solución.

## Observaciones de UX y gobierno

La dirección correcta de la solución es que la gestión de suscripciones viva en la app, no en HTML embebido. El estado actual, no obstante, muestra una incoherencia:

- existe una entidad de suscripciones usable en model-driven app;
- pero sigue existiendo el web resource `kyn_Report_Subscriptions` como componente raíz.

Recomendación:

- si la gestión de suscripciones ya se resuelve con la entidad y su formulario, retirar ese web resource de la solución;
- si sigue cumpliendo una función real, documentarla expresamente y dejar claro dónde se usa.
