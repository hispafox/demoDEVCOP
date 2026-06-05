# Estrategia tecnica REST en Fortran

## Estado

- Fecha: 2026-06-05
- Referencia: Issue #8 "Definir estrategia tecnica REST en Fortran"
- Estado: Decision adoptada para el MVP

## Decision adoptada

Para el MVP se adopta una arquitectura mixta y deliberadamente pequena:

- El nucleo funcional y el modelo de datos se implementaran en Fortran.
- La serializacion JSON se realizara con JSON-Fortran.
- La exposicion HTTP se resolvera mediante un servidor embebido en C con una
  interfaz minima hacia Fortran a traves de ISO_C_BINDING.
- La herramienta de build principal sera fpm.
- Las pruebas automatizadas se dividiran en pruebas unitarias del nucleo en
  Fortran y una prueba minima de integracion del endpoint cuando exista el
  ejecutable del servidor.

## Opcion concreta seleccionada

La opcion seleccionada para servir HTTP es integrar CivetWeb como servidor HTTP
embebido y encapsular su uso detras de un adaptador pequeno propio.

El adaptador tendra solo estas responsabilidades:

- Arrancar el servidor en un puerto configurable.
- Registrar el handler del endpoint GET inicial.
- Llamar al codigo Fortran para obtener la respuesta del caso de uso.
- Escribir la respuesta HTTP con codigo 200 y content-type application/json.

El codigo Fortran no conocera detalles de sockets ni de la libreria HTTP. Solo
debera devolver el payload JSON o la estructura de datos que luego se
serializara.

## Justificacion

Esta decision se toma por pragmatismo tecnico:

- Implementar sockets HTTP directamente en Fortran desde el primer MVP aumenta
  riesgo y retrabajo.
- CivetWeb es una libreria embebible, pequena, madura y multiplataforma,
  incluida Windows, que reduce el trabajo no funcional.
- fpm encaja bien con un repositorio pequeno y permite compilar, ejecutar tests
  y gestionar dependencias Fortran sin sobrecargar el arranque.
- JSON-Fortran es una opcion conocida y mantenida para generar JSON desde
  Fortran moderno.

## Opciones descartadas

### HTTP implementado a mano en Fortran

Se descarta para el MVP porque obliga a resolver sockets, parsing HTTP,
cabeceras y portabilidad demasiado pronto.

### Framework web externo fuera del proceso Fortran

Se descarta porque diluye la restriccion tecnica de que la implementacion sea en
Fortran y complica la trazabilidad del MVP.

### CMake como build principal

Se descarta como herramienta principal del MVP porque fpm ofrece un flujo mas
simple para arrancar rapido con estructura, dependencias y tests. CMake puede
aparecer despues si la integracion mixta Fortran y C crece mas de lo previsto.

## Estructura inicial propuesta

El esqueleto del proyecto debera nacer con esta forma:

- app/: punto de entrada del servidor.
- src/: logica Fortran del dominio, modelo y serializacion.
- csrc/: adaptador C minimo para iniciar CivetWeb y conectar handlers.
- test/: pruebas unitarias de Fortran y pruebas de integracion basicas.
- vendor/ o dependencia declarada: codigo de tercero que se decida fijar para
  CivetWeb.

## Build tool y flujo local

La herramienta principal sera fpm.

Decisiones de build:

- fpm sera la entrada estandar para build y tests del codigo Fortran.
- El compilador Fortran objetivo para arrancar sera gfortran por disponibilidad.
- Se admitira enlazado con C para el adaptador HTTP.
- La version inicial no requiere HTTPS, servicio Windows ni configuracion
  avanzada del servidor.

Flujo esperado del MVP:

- Compilar la libreria y el ejecutable del servidor.
- Ejecutar tests unitarios del dominio y serializacion.
- Levantar el binario del servidor para validar el endpoint GET.

## Estrategia de pruebas automatizadas

Se fija este enfoque desde el inicio:

- Pruebas unitarias en Fortran para el modelo de proceso y estado.
- Pruebas unitarias en Fortran para la generacion del JSON del payload.
- Una prueba de integracion minima que invoque el endpoint y verifique codigo
  HTTP 200 y estructura JSON esperada.

La prioridad de las pruebas sera proteger primero el comportamiento funcional,
no el servidor HTTP completo.

## Riesgos y limitaciones del enfoque

- La integracion Fortran y C introduce una frontera adicional de build y
  depuracion.
- La capa HTTP no sera puramente Fortran, aunque la logica de negocio si.
- Puede haber ajustes especificos de toolchain en Windows para enlazar Fortran y
  C con el mismo conjunto de compiladores.
- Si la integracion de CivetWeb con fpm resulta mas costosa de lo esperado, la
  siguiente alternativa sera mantener fpm para el nucleo y usar CMake solo como
  orquestador de build mixto.

## Criterios de salida para la issue #8

La issue se considera resuelta si quedan fijados estos puntos:

- Existe una decision explicita sobre como servir HTTP.
- Existe una herramienta de build definida.
- Existe un enfoque inicial de pruebas automatizadas.
- Los riesgos y tradeoffs quedan documentados.

## Impacto en las siguientes issues

- Issue #9 debe definir el contrato del endpoint sobre esta base.
- Issue #10 debe crear el esqueleto fpm con la separacion app, src, csrc y test.
- Issue #11 debe implementar el modelo y los datos estaticos en Fortran.
- Issue #12 debe conectar el handler HTTP con la logica Fortran y devolver JSON.
- Issue #13 debe documentar compilacion, validacion local y limitaciones del
  MVP.