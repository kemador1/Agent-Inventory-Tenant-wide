# Manual de despliegue y configuración

## Identificación

- Solución: `kynagentinventorytenantwide`
- Versión candidata documentada: `2.2.0.2`
- Paquetes previstos: managed y unmanaged

## Prerrequisitos

- entorno con Dataverse;
- permisos de importación de soluciones;
- connection references válidas para:
  - Dataverse
  - Power Platform Admins V2
  - Office 365 Users
  - conector de correo utilizado por el flujo

## Pasos de importación

1. Importar la solución.
2. Resolver las connection references requeridas.
3. Configurar las variables de entorno.
4. Publicar personalizaciones.
5. Abrir el flujo principal y validar que no quedan errores de plantilla.
6. Ejecutar una prueba manual.

## Variables de entorno

- `kyn_Notificacincorreosinformesflujo`: lista de destinatarios del correo.
- `kyn_ClienteoEmpresaInformesflujo`: texto usado en asunto, cabecera y pie del correo.

## Verificaciones mínimas tras la importación

- la tabla `kyn_agenttenantwide` está disponible;
- la app abre correctamente;
- los dashboards aparecen en navegación;
- el reporte ligado a la tabla está disponible;
- el flujo se ejecuta y devuelve correo en español;
- un agente observado queda activo;
- un agente no observado queda inactivo;
- los `WebResources` visuales cargan sin error.

## Consideraciones de despliegue

- en esta candidata sí existen `WebResources` empaquetados;
- si se cambian nombres de recursos web, debe revisarse cualquier dependencia en formularios;
- las variables de entorno permiten reutilizar la solución en distintos tenants sin hardcodear branding o destinatarios.
