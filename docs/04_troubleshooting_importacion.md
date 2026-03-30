# 04 - Troubleshooting de importación

## Error: atributo inexistente en FetchXml
Síntoma:
- `entity doesn't contain attribute ... kyn_recipientemail ... kyn_agenttenantwide`

Causa:
- Vista de `kyn_agenttenantwide` con columnas de `kyn_suscripcionesdeinformes`.

Acción:
- Quitar `kyn_recipientemail` y `kyn_reportmodecode` de vistas/fetchxml de `kyn_agenttenantwide`.

## Error: Form XML id inválido
Síntoma:
- `Form XML ... 'id' attribute is invalid according to FormGuidType`

Causa:
- `cell id` en formulario con valor texto en lugar de GUID.

Acción:
- Reemplazar el `id` por GUID válido.

## Error en expresión Flow por empty(Integer)
Síntoma:
- `empty expects ... object/array/string. Provided value is Integer`

Causa:
- `empty()` aplicado a Choice numérico (`kyn_reportmodecode`).

Acción:
- Cambiar por `equals(item()?['kyn_reportmodecode'], null)`.

## No se envían correos
Revisar condición de envío.
Debe excluir `OFF/NONE`, no incluirlos.

Condición recomendada:

```text
@and(
  contains(trim(string(item()?['kyn_recipientemail'])), '@'),
  not(equals(outputs('Compose_RecipientMode'), 'NONE')),
  not(equals(outputs('Compose_RecipientMode'), 'OFF'))
)
```
