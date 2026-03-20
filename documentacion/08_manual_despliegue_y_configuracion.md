# Manual de despliegue y configuración

## Identificación

- Solución: `kynagentinventorytenantwide`
- Versión: `2.2.0.0`
- Tipo: unmanaged

## Prerrequisitos

- entorno Dataverse operativo;
- permisos para importar solución;
- connection references válidas para Dataverse, Power Platform Admins V2, Office 365 Outlook y Office 365 Users.

## Configuración

1. Importar la solución.
2. Resolver las connection references.
3. Informar `kyn_Notificacincorreosinformesflujo`.
4. Informar `kyn_ClienteoEmpresaInformesflujo` si se quiere personalizar el correo.
5. Publicar y probar una ejecución manual.

## Validaciones mínimas

- el flujo principal se abre sin errores de plantilla;
- el correo llega en español;
- el asunto y cabecera reflejan la empresa/cliente configurado;
- el log de cambios muestra campo, valor anterior y valor nuevo;
- un agente no observado pasa a inactivo sin borrado físico;
- un agente que reaparece vuelve a activo.
