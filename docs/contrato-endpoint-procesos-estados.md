# Contrato del endpoint de procesos y estados

## Estado

- Fecha: 2026-06-05
- Referencia: Issue #9 "Definir contrato del endpoint de procesos y estados"
- Estado: Contrato inicial aprobado para el MVP
- Decision tecnica relacionada: docs/estrategia-tecnica-rest-fortran.md

## Objetivo del contrato

Fijar un contrato HTTP y JSON pequeno, estable y suficiente para el MVP inicial
de consulta de procesos y estados.

Este contrato define solo la interfaz externa del primer endpoint. No fija aun el
conjunto concreto de procesos, que se resolvera en la Issue #11.

## Endpoint inicial

- Metodo: GET
- Ruta: /api/processes
- Content-Type de respuesta: application/json
- Autenticacion: no requerida en el MVP

## Semantica

El endpoint devuelve la lista actual de procesos conocidos por el sistema y el
estado asociado a cada uno.

Durante el MVP la fuente de datos sera estatica, pero el contrato no depende de
que los datos sean estaticos o dinamicos.

## Respuesta de exito

Codigo HTTP:

- 200 OK

Cuerpo JSON:

```json
{
  "processes": [
    {
      "id": "IMPORT_CUSTOMERS",
      "name": "Import customers",
      "status": "pending"
    }
  ]
}
```

## Esquema del payload

La respuesta sera un objeto JSON con esta forma:

- processes: array obligatorio.

Cada elemento de processes tendra estos campos obligatorios:

- id: string estable que identifica el proceso dentro del sistema.
- name: string legible para humanos.
- status: string con el estado actual del proceso.

## Valores iniciales permitidos para status

Para el MVP se fijan estos valores validos:

- pending
- running
- completed
- failed

No se definen estados adicionales en esta iteracion.

## Reglas del contrato

- La ruta inicial del MVP no acepta query parameters.
- La respuesta siempre sera JSON, tambien cuando la lista este vacia.
- Si no existen procesos definidos todavia, el endpoint respondera 200 OK con
  processes vacio.
- El orden de la lista no forma parte del contrato funcional en esta iteracion.

Ejemplo con lista vacia:

```json
{
  "processes": []
}
```

## Casos fuera de alcance del contrato inicial

En esta iteracion no se fijan todavia estos puntos:

- Paginacion.
- Filtros o busquedas.
- Versionado de API.
- Endpoint de detalle por proceso.
- Operaciones de escritura.
- Modelo de error JSON comun para toda la API.

## Criterios de aceptacion de la Issue #9

La issue se considera cerrada si quedan definidos estos puntos:

- Existe un metodo y una ruta concretos para el MVP.
- Existe una forma JSON de respuesta definida.
- Existen campos obligatorios minimos para cada proceso.
- Existen valores iniciales permitidos para el estado.
- Queda claro lo que se difiere a las issues siguientes.

## Impacto en las siguientes issues

- Issue #10 debe crear el esqueleto ejecutable y de pruebas sobre esta ruta.
- Issue #11 debe definir el conjunto estatico inicial de procesos respetando
  este esquema.
- Issue #12 debe implementar GET /api/processes y devolver este payload.
- Issue #13 debe documentar la llamada HTTP y ejemplos de uso del endpoint.