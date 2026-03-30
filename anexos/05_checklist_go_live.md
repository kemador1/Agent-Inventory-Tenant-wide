# Checklist Go-Live

## 1) Importación
- [ ] Importación de `kynagentinventorytenantwide_2_7_0_7_managed.zip` completada sin errores críticos.
- [ ] Solución publicada correctamente.

## 2) Datos y modelo
- [ ] Tabla `kyn_agenttenantwide` visible y operativa.
- [ ] Tabla `kyn_suscripcionesdeinformes` visible y operativa.
- [ ] Columnas de suscripción (`kyn_recipientemail`, `kyn_reportmodecode`) disponibles en formulario.

## 3) Flujo
- [ ] Flujo principal activado.
- [ ] Conexiones sin errores.
- [ ] Ejecución manual completada.

## 4) Notificaciones
- [ ] Suscripción con modo `Complete report` recibe correo.
- [ ] Suscripción con modo `Do not send report` no recibe correo.
- [ ] Correos inválidos se omiten y quedan trazas en ejecución.

## 5) Seguridad
- [ ] Roles asignados a usuarios finales.
- [ ] Solo perfiles autorizados editan suscripciones.

## 6) Operación
- [ ] Responsable de soporte definido.
- [ ] Runbook y troubleshooting accesibles.
- [ ] Ventana de revisión post-go-live acordada (24-72h).
