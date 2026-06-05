# Documento de inicio del proyecto

## Estado del documento

- Version: 0.4
- Fecha: 2026-06-05
- Estado: Borrador inicial revisable
- Referencia: Issue #1 "Crear documento de inicio del proyecto"

## 1. Contexto

Este repositorio arranca con una base minima y necesita una referencia comun para
alinear alcance, objetivos y siguientes pasos desde el inicio. Este documento
sirve como punto de partida para completar la definicion funcional y tecnica en
iteraciones cortas.

El objetivo funcional ya definido para el arranque es construir una aplicacion
que publique una API REST con una lista de procesos y sus estados. En esta
primera iteracion, la lista sera estatica. La implementacion debe realizarse en
Fortran.

## 2. Objetivo

Construir una aplicacion en Fortran que exponga una API REST para consultar una
lista de procesos y estados.

Objetivos de la primera iteracion:

- Publicar al menos un endpoint de lectura.
- Devolver una lista estatica de procesos con su estado asociado.
- Dejar trazado el esqueleto tecnico para evolucionar despues a datos dinamicos.
- Mantener trazabilidad documental y tecnica desde el inicio.

## 3. Alcance inicial

Incluido en esta version:

- Documento de inicio del proyecto dentro del repositorio.
- API REST inicial para consulta de procesos y estados.
- Lista estatica de procesos como origen de datos temporal.
- Implementacion base en Fortran.
- Estructura base de definicion con apartados funcionales y de gestion.

Fuera de alcance en esta version:

- Persistencia en base de datos.
- Escritura o modificacion de estados via API.
- Autenticacion y autorizacion.
- Integraciones externas.
- Despliegue productivo.

## 4. Entregables de esta iteracion

- Documento inicial del proyecto en el repositorio.
- Plantilla util con contexto, objetivos, alcance, supuestos, riesgos y
  proximos pasos.
- Base revisable para completar en siguientes iteraciones.

## 5. Stakeholders y responsables

Pendiente de completar:

- Sponsor o responsable de negocio.
- Responsable tecnico.
- Equipo participante.
- Interlocutores de validacion.

## 6. Supuestos iniciales

- El repositorio sera la fuente principal de trazabilidad documental inicial.
- El primer caso de uso es solo de consulta.
- La lista de procesos sera estatica en esta fase.
- Fortran es una restriccion tecnica explicita del proyecto.
- La capa HTTP o REST en Fortran requerira una decision tecnica temprana.

## 7. Riesgos iniciales

- Riesgo tecnico por la disponibilidad limitada de opciones maduras para exponer
  una API REST directamente en Fortran.
- Riesgo de sobrediseño si se intenta resolver desde el inicio necesidades no
  incluidas en el MVP.
- Riesgo de retrabajo si no se fija pronto el contrato del endpoint y el modelo
  de datos estatico.
- Riesgo de bloqueo si no se acuerda la estrategia de build y pruebas desde el
  inicio.

## 8. Dependencias

- Decision de la estrategia tecnica para servir HTTP en Fortran.
- Definicion del contrato JSON de la respuesta.
- Confirmacion del conjunto inicial de procesos y estados.
- Seleccion de build tool y estrategia de pruebas automatizadas.

## 9. Pendientes abiertos

Queda por definir:

- Contrato exacto del endpoint o endpoints iniciales.
- Modelo de datos de proceso y estado.
- Estrategia tecnica para exponer REST en Fortran.
- Estructura del proyecto, compilacion y pruebas.
- Criterios de exito del primer entregable.

Desglose trazado en GitHub:

- Issue #2: Definir problema y contexto de negocio.
- Issue #3: Identificar stakeholders y criterios de exito iniciales.
- Issue #4: Definir alcance funcional detallado y MVP.
- Issue #5: Documentar restricciones e integraciones.
- Issue #6: Definir hitos, calendario y responsables.
- Issue #7: Preparar version ejecutiva del documento de inicio.

Backlog tecnico inicial para empezar:

- Issue #8: Definir estrategia tecnica REST en Fortran.
- Issue #9: Definir contrato del endpoint de procesos y estados.
- Issue #10: Crear esqueleto del proyecto Fortran con build y tests.
- Issue #11: Definir modelo de datos estatico de procesos y estados.
- Issue #12: Implementar endpoint GET de procesos y estados.
- Issue #13: Documentar ejecucion local y uso de la API.

## 10. Proximos pasos

1. Validar el objetivo y contexto del proyecto.
2. Resolver Issue #8 para fijar la base tecnica en Fortran.
3. Resolver Issue #9 para cerrar el contrato del endpoint.
4. Ejecutar Issues #10, #11, #12 y #13 como MVP tecnico inicial.

## 11. Criterios de aceptacion cubiertos

Este documento cumple la base pedida por la issue:

- Existe un documento inicial en el repositorio.
- Identifica objetivos, alcance inicial y pendientes abiertos.
- Deja visible la informacion que falta por completar.

## 12. Historial de cambios

- 0.1 - Creacion del documento inicial.
- 0.2 - Desglose de pendientes trazado en issues de GitHub.
- 0.3 - Objetivo funcional concretado: API REST de procesos y estados en Fortran.
- 0.4 - Backlog tecnico inicial publicado para arrancar el MVP.