# Project Portfolio

| Proyecto | Estado | Tarea actual | Próxima actividad |
|---|---|---|---|
| [Fabrícamelo](https://github.com/cramoscr/fabricamelo) | ACTIVE — VOICE-FIRST / FAB-009 COMPLETED; FAB-010 MERGE; FAB-011 IN PROGRESS | Integración de Alexa («mi taller») con Cirios-App mediante Firebase Functions y APIs; flujo de pedidos y consultas de pedidos desarrollado. FAB-009 cerrado. Trabajo posterior de integración/merge y FAB-011 en evolución. | Verificar el estado real de FAB-010/FAB-011, continuar las funcionalidades acordadas y mantener CI/CD controlado. |
| [Intent-Based-UI (IBUI)](https://github.com/cramoscr/intent-based-ui) | ACTIVE — DISCOVERY / PUBLIC EXPERIMENT | Repositorio público independiente creado bajo Apache 2.0. Visión, roadmap, backlog y estructura inicial documentados. ADR-001 aprobado: consistencia visual inicial con Cirios-App y separación entre modelo de interacción y tema visual. | Inspeccionar los estilos reales de Cirios-App; especificar y prototipar dos intenciones: «Crear pedido para Marvin» (Taller) y «Buscar cirio pascual» (Tienda), sin cambios en producción. |
| [Cirios-App](https://github.com/cramoscr/cirios-app) | ACTIVE — ERP/POS / PILOT CANDIDATE | Aplicación de tienda y taller, backend Firestore y APIs consumidas por Fabrícamelo. ADR-UX-001 establece experiencias Tienda y Taller. Seleccionada como primer laboratorio de IBUI. | Continuar evolución funcional propia; mantener los experimentos de IBUI aislados del trabajo de producción. |
| Distillery Project | ACTIVE — DISCOVERY | Metodología de evaluación de ideas y Distillery-HeartCare en definición; propuesta de runs con corpus metodológico por idea. | Refinar dimensiones de evaluación y probar un run acotado antes de ampliar implementación. |
| OCI GnSys | FREEZE | Laboratorios OCI y evidencia práctica preservados. | Sin actividad hasta decidir reactivación. |
| Cáritas App / SIISPA | CLOSED / TRANSITION | Cierre o sustitución del producto comunicado en octubre de 2026; experiencia y documentación histórica preservadas. | Solo actividades de transición o conservación que sean necesarias; no se presupone nueva expansión. |

_Actualizado: 2026-10-11 — incorporación de IBUI y actualización del estado del portafolio._

## Convención operativa CI/CD

En `cirios-app`, los commits normales no disparan CI/CD. La frase clave **`publica en producción`** indica autorización explícita para actualizar `.github/trigger-ci-cd` y crear un commit técnico que active el workflow de build y deploy.

## Nota de alcance — IBUI

IBUI es un proyecto de investigación y prototipado independiente, no una funcionalidad terminada ni un framework publicado. El primer piloto se realizará con Cirios-App, sin alterar producción ni bloquear FAB-011.

## Convención transversal de desarrollo — OpenSpec por feature

**Acuerdo ratificado: 2026-10-11.** Aplica a Fabrícamelo, Intent-Based-UI y futuros proyectos, salvo decisión explícita en contrario.

- **Cada feature o cambio tiene su propia carpeta de OpenSpec**, siguiendo el patrón ya utilizado en Fabrícamelo: `specifications/openspec/changes/<feature-id>-<slug>/`.
- En esa carpeta se agrupan `proposal.md` (alcance y motivación), `design.md` (diseño y decisiones), `tasks.md` (plan, implementación, verificación y cierre) y `specs/<capability>/spec.md` (requisitos y escenarios, cuando aplique).
- El **código ejecutable** permanece en `software/` o en la estructura de código propia del proyecto; no se duplica dentro de OpenSpec. `tasks.md` conserva la trazabilidad hacia la implementación y pruebas.
- Se debe **revisar la convención y estructura existente del repositorio antes de crear archivos**, evitando carpetas paralelas, especificaciones duplicadas o una metodología distinta sin aprobación.
- Flujo de trabajo: **definir feature → propuesta → diseño → especificación → tareas → implementación → pruebas → cierre**, manteniendo el estado real en los archivos.
- **IBUI-002**: el lugar canónico es `intent-based-ui/specifications/openspec/changes/ibui-002-adaptive-catalog/`. Queda pendiente eliminar la copia inicial en `intent-based-ui/openspec/changes/` para evitar duplicación. No confundir documentación creada con código implementado o desplegado.

