# Resumen ejecutivo del proyecto

## Estado

- Fecha: 2026-06-05
- Estado: Base tecnica y contrato inicial decididos
- Referencia principal: docs/inicio-proyecto.md
- Decision tecnica: docs/estrategia-tecnica-rest-fortran.md
- Contrato API: docs/contrato-endpoint-procesos-estados.md

## Resumen

El proyecto consiste en desarrollar una aplicacion en Fortran que publique una
API REST para consultar una lista de procesos y estados. La primera iteracion se
limita a un caso de uso simple de lectura con datos estaticos, con el objetivo
de validar rapido el contrato de la API y la base tecnica.

## Objetivo ejecutivo

Entregar un primer MVP que permita exponer por HTTP una lista de procesos y
estados, dejando listo un punto de partida tecnico y funcional sobre el que
evolucionar en iteraciones posteriores.

## Alcance del MVP

- Un endpoint GET de consulta.
- Lista estatica de procesos y estados.
- Respuesta en JSON.
- Base de compilacion y validacion local.

## Fuera de alcance por ahora

- Persistencia en base de datos.
- Operaciones de escritura.
- Autenticacion y autorizacion.
- Integraciones externas.
- Despliegue productivo.

## Riesgos principales

- La eleccion de Fortran obliga a resolver pronto la estrategia para servir HTTP.
- Si no se fija rapido el contrato JSON, puede haber retrabajo temprano.
- La falta de definiciones operativas y de responsables puede ralentizar el
  avance despues del MVP inicial.

## Pendientes criticos

- Definir el modelo de datos estatico de procesos y estados.
- Preparar esqueleto, build y pruebas.

## Proximos pasos

1. Montar el esqueleto del proyecto con compilacion y pruebas.
2. Definir el modelo de datos estatico de procesos y estados.
3. Implementar el endpoint GET.
4. Documentar compilacion, validacion local y uso de la API.