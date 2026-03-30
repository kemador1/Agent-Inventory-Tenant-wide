# 01 - Resumen funcional

## Objetivo
Centralizar el inventario de agentes del tenant, facilitar gobierno y habilitar reportes por suscripción de usuario.

## Componentes principales
- Tabla principal de inventario: `kyn_agenttenantwide`
- Tabla de suscripciones: `kyn_suscripcionesdeinformes`
- Flujo principal: `KYN Agent Inventory tenant-wide_ whitout UPN search`
- App model-driven: módulo con acceso a inventario y suscripciones

## Principios de diseño
- Las tablas reflejan únicamente los datos necesarios de la consulta.
- Configuración de destinatarios y modo de reporte en tabla/app (no hardcoded en HTML).
- Compatibilidad con fallback legacy para `kyn_reportmode` mientras exista dato histórico.

## Lógica de suscripción
Cada fila activa de `kyn_suscripcionesdeinformes` define:
- Email destino (`kyn_recipientemail`)
- Tipo de reporte (`kyn_reportmodecode`)

## Regla de envío recomendada
Enviar solo si:
- Email válido (longitud mínima o contiene `@`)
- Modo distinto de `OFF` y `NONE`

Expresión recomendada de condición:

```text
@and(
  contains(trim(string(item()?['kyn_recipientemail'])), '@'),
  not(equals(outputs('Compose_RecipientMode'), 'NONE')),
  not(equals(outputs('Compose_RecipientMode'), 'OFF'))
)
```
