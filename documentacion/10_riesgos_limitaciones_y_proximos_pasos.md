# Riesgos, limitaciones y próximos pasos

## Riesgos actuales

| Riesgo | Estado | Impacto | Mitigación |
| --- | --- | --- | --- |
| cambios no materiales por formato de datos | mitigado | medio | comparación restringida a campos estables |
| visión parcial del origen | mitigado | alto | inactivación solo tras ausencias consecutivas, sin borrado duro |
| branding de correo no configurado | mitigado | bajo | variable de entorno de empresa/cliente |

## Limitaciones

- la solución no calcula telemetría real por agente de Copilot Chat/BizChat;
- algunos campos legacy permanecen en la tabla por compatibilidad, aunque el flujo actual no dependa de ellos.

## Próximos pasos recomendados

- depurar campos legacy si se confirma que no se usarán;
- añadir scheduler si se quiere operación diaria automática;
- formalizar el umbral definitivo de inactivación por ausencias consecutivas;
- ampliar el correo con enlaces directos a vistas o dashboards.
