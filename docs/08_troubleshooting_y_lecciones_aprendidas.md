# 08 - Troubleshooting y lecciones aprendidas

## Errores relevantes observados

### 1. Vistas con atributos de entidad equivocada

Se detectaron vistas de `kyn_agenttenantwide` que referenciaban `kyn_recipientemail` y `kyn_reportmodecode`, atributos que pertenecen a `kyn_suscripcionesdeinformes`. Este tipo de error rompe importacion y calculo de dependencias.

### 2. Formularios con identificadores invalidos

Se detecto un `cell id` textual en lugar de GUID. En soluciones Dataverse, el XML de formulario debe respetar completamente el esquema esperado por la plataforma.

### 3. Configuracion funcional ubicada en HTML

La configuracion de reportes no debe residir en una representacion HTML. Debe residir en la tabla y en la app. El HTML puede presentar, pero no gobernar.

### 4. Expresiones con tipado incorrecto

Aplicar `empty()` a un valor entero procedente de choice provoca fallo de expresion. Power Automate exige respetar tipo de dato en cada funcion.

### 5. Condicion de envio invertida

Una condicion mal construida puede hacer que solo se intente enviar cuando el modo sea `OFF` o `NONE`. Este error es pequeno a nivel de diseno pero grande a nivel de operacion.

## Lecciones aprendidas

- en Power Platform no basta con que el flujo funcione aislado;
- la calidad real esta en la coherencia entre paquete, metadata, app y automatizacion;
- la documentacion debe acompañar esa coherencia y no limitarse a notas sueltas.

## Recomendacion final

Toda evolucion futura deberia seguir una practica disciplinada:

1. cambiar modelo;
2. ajustar vistas y formularios;
3. ajustar flujo;
4. validar importacion;
5. actualizar documentacion.
