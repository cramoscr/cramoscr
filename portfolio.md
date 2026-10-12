# Project Portfolio

| Proyecto | Estado | Tarea actual | Próxima actividad |
|---|---|---|---|
| [Fabrícamelo](https://github.com/cramoscr/fabricamelo) | ACTIVE — VOICE-FIRST / FAB-009 COMPLETED; FAB-010 MERGE; FAB-011 IN PROGRESS | Integración de Alexa («mi taller») con Cirios-App mediante Firebase Functions y APIs; flujo de pedidos y consultas de pedidos desarrollado. FAB-009 cerrado. Trabajo posterior de integración/merge y FAB-011 en evolución. | Verificar el estado real de FAB-010/FAB-011, continuar las funcionalidades acordadas y mantener CI/CD controlado. |
| [Intent-Based-UI (IBUI)](https://github.com/cramoscr/intent-based-ui) | ACTIVE — IBUI-001 VALIDATED; IBUI-002 IN DEVELOPMENT | IBUI-001: interfaz móvil React/MUI publicada en Firebase Hosting y validada en celular. IBUI-002: especificación aprobada y primera implementación de catálogo adaptativo (tarjetas con imagen dummy, lista, detalle y comparación) guardada en `feature/ibui-001-react-mui`, commit `1fa1644`; sin despliegue de IBUI-002. | Próxima sesión: implementar CI/CD de GitHub Actions → Firebase Hosting siguiendo el patrón de Fabrícamelo y activación explícita «publica en producción». Después validar build, resolver acceso seguro a `catalogApi` de Cirios-App, probar catálogo real en móvil y publicar solo con autorización. |
| [Cirios-App](https://github.com/cramoscr/cirios-app) | ACTIVE — ERP/POS / PILOT CANDIDATE | Aplicación de tienda y taller, backend Firestore y APIs consumidas por Fabrícamelo. ADR-UX-001 establece experiencias Tienda y Taller. Seleccionada como primer laboratorio de IBUI. | Continuar evolución funcional propia; mantener los experimentos de IBUI aislados del trabajo de producción. |
| Distillery Project | ACTIVE — DISCOVERY | Metodología de evaluación de ideas y Distillery-HeartCare en definición; propuesta de runs con corpus metodológico por idea. | Refinar dimensiones de evaluación y probar un run acotado antes de ampliar implementación. |
| OCI GnSys | FREEZE | Laboratorios OCI y evidencia práctica preservados. | Sin actividad hasta decidir reactivación. |
| Cáritas App / SIISPA | CLOSED / TRANSITION | Cierre o sustitución del producto comunicado en octubre de 2026; experiencia y documentación histórica preservadas. | Solo actividades de transición o conservación que sean necesarias; no se presupone nueva expansión. |

_Actualizado: 2026-10-11 — avance de IBUI-001/002 y planificación del siguiente paso CI/CD._

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


## IBUI — avance, pendientes y siguiente paso

- **IBUI-001:** prototipo React/MUI de «Mi Taller» terminado, desplegado en Firebase Hosting (`fabricamelo-lab`, sitio `fabriquemelo-app`) y validado visualmente en un teléfono móvil.
- **IBUI-002:** aprobado catálogo adaptativo. Inicio: sugerencias tipo burbuja, sin tarjetas; resultados: tarjetas para exploración, lista compacta para catálogos extensos, detalle y comparación básica. Los datos deben provenir del catálogo real; el espacio de imagen utiliza contenido provisional. Se pospone ampliar el API para imágenes.
- **Código:** implementación inicial en `intent-based-ui/software/app/src/App.jsx`, rama **`feature/ibui-001-react-mui`**, commit **`1fa1644`**. No se ha comprobado aún compilación ni integración completa y no se ha desplegado IBUI-002. Se creó una rama adicional `feature/ibui-002-catalog` durante la exploración, pero por decisión expresa se continuará trabajando en la rama de IBUI-001; no usar la rama adicional como base de desarrollo.
- **Dependencia técnica:** el `catalogApi` de Cirios-App devuelve `products` con `name` y `price` y está protegido mediante IAM para consumidores autorizados. El frontend requiere una vía de acceso segura; no exponer credenciales ni abrir el API indiscriminadamente. No cambiar el contrato del API por ahora.
- **Pendientes:** validar build; implementar conexión segura y verificar CORS/autorización; probar consultas reales, filtrado, estados vacío/error y vistas responsivas; revisar y cerrar OpenSpec; validar en celular; desplegar solo con aprobación.
- **Próximo paso acordado (siguiente sesión):** implementar CI/CD para IBUI siguiendo el patrón ya probado en Fabrícamelo (GitHub Actions, Firebase Hosting aislado y disparador controlado mediante «publica en producción»). No confundir implementación del workflow con autorización para publicar.

## Archivo histórico — Mis viejos fracazos

- **Repositorio privado:** [`cramoscr/my-seniority-project-private`](https://github.com/cramoscr/my-seniority-project-private)
- **Carpeta:** [`mis-viejos-fracazos/`](https://github.com/cramoscr/my-seniority-project-private/tree/main/mis-viejos-fracazos)
- **Propósito:** conservar y analizar experiencias históricas de proyectos y negocios, incluidos los aprendizajes técnicos, comerciales y personales. Esta referencia es privada y no implica publicar su contenido.
