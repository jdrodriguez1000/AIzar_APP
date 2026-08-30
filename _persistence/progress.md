# progress.md

> **Archivo principal del proyecto.** Da la vision general: como va el proyecto, cual es el
> avance, que es lo ultimo realizado y cual es el siguiente paso.
> **No detalla tareas** — el detalle de tareas vive en `tasks.md`.

---

## Indice

| Seccion | Contenido |
|---|---|
| [1. Estado general](#1-estado-general) | Etapa actual, salud del proyecto, avance |
| [2. Ultimo realizado](#2-ultimo-realizado) | Lo mas reciente que quedo terminado |
| [3. Siguiente paso](#3-siguiente-paso) | Que sigue ahora |
| [4. Hitos](#4-hitos) | Hitos del proyecto y su estado |
| [5. Bitacora](#5-bitacora) | Sesiones `S-XXX` (una jornada cada una, no un dia) |
| [6. Mapa de persistencia](#6-mapa-de-persistencia) | Que se registra en cada archivo |

### Sesiones

> Una sesion es una **jornada** de trabajo (manana, tarde, noche o dia completo). Puede haber
> varias en la misma fecha; cada una lleva su propio `S-XXX` (D-009).

| Codigo | Sesion | Fecha | Etapa |
|---|---|---|---|
| [S-001](#s-001---metodo-de-trabajo-persistencia-y-protocolo-de-cierre) | Metodo de trabajo, persistencia y protocolo de cierre | 2026-08-28 | 000_preproject |
| [S-002](#s-002---informe-de-cierre-para-la-terminal-auditora) | Informe de cierre para la terminal auditora | 2026-08-28 | 000_preproject |
| [S-003](#s-003---canal-de-vuelta-de-la-auditoria-aceptado-e-implementado) | Canal de vuelta de la auditoria aceptado e implementado | 2026-08-28 | 000_preproject |
| [S-004](#s-004---los-datos-propios-del-proyecto-se-extraen-a-projectmd) | Los datos propios del proyecto se extraen a `PROJECT.md` | 2026-08-28 | 000_preproject |
| [S-005](#s-005---el-metodo-vertical-se-incorpora-y-se-ajusta-al-vocabulario-propio) | El metodo VERTICAL se incorpora y se ajusta al vocabulario propio | 2026-08-28 | 000_preproject |
| [S-006](#s-006---la-guia-transversal-_globalguidemd-se-analiza-y-se-ajustan-sus-primeros-cuatro-puntos) | La guia transversal `_global/guide.md` se analiza y se ajustan sus primeros cuatro puntos | 2026-08-28 | 000_preproject |
| [S-007](#s-007---_global-se-declara-en-projectmd-y-se-cierra-dt-003) | `_global/` se declara en `PROJECT.md` y se cierra DT-003 | 2026-08-30 | 000_preproject |

---

## 1. Estado general

| Campo | Valor |
|---|---|
| Etapa actual | `000_preproject` |
| Ultima actualizacion | 2026-08-30 |
| Salud | En marcha |
| Avance de la etapa | Metodo de trabajo, persistencia, repositorio, ciclo completo inicio/cierre, canal de vuelta con la auditoria, datos propios del proyecto en `PROJECT.md`, el metodo VERTICAL incorporado y ajustado, la guia transversal `_global/guide.md` incorporada con sus primeros cuatro puntos de ajuste resueltos, y ahora `_global/` declarada en la tabla «Carpetas propias» de `PROJECT.md` (D-031), con DT-003 pagada entera; quedan cinco puntos del analisis de la guia para la proxima sesion (T-020 a T-024) y alcance del proyecto pendiente |
| Bloqueos activos | Alcance y objetivo del proyecto sin definir (T-004); bloquea a su vez T-016 y el diseño de la fase Prototipo |

---

## 2. Ultimo realizado

Sesion corta dedicada a preparar el arranque de la auditoria pendiente (informes `S-002` a
`S-006`, todos `Pendiente`). Se detecto que `PROJECT.md` no declaraba `_global/` en su tabla
«Carpetas propias» pese a que `S-006` la incorporo al repositorio — la deuda ya estaba anotada
como **DT-003**, propuesta y sin confirmar. El usuario confirmo cerrarla:

- **D-031** — `_global/` entra en la tabla «Carpetas propias» de `PROJECT.md`, con tres notas: se
  copia por proyecto con sello de version y no se comparte (D-028), `sources/GUIDE.md` es de solo
  lectura (C-005), y se versiona entera, sin ninguna exclusion en `.gitignore`.
- **DT-003** pasa a `Implementada` (pagada el 2026-08-30, S-007), con las dos mitades resueltas:
  la fila en `PROJECT.md` (edicion), y la comprobacion de si hacia falta alguna exclusion en
  `.gitignore` (verificacion: no hacia falta ninguna, los tres archivos son registro del proyecto).

No hubo construccion de producto ni cambios de codigo.

---

## 3. Siguiente paso

Retomar los puntos 5 a 9 del analisis de `_global/guide.md`, en el orden del listado: **T-020**
(nivel de concrecion de `RR-003`), **T-021** (regla de asignacion de codigos `RR-NNN`), **T-022**
(huecos de cobertura del recetario — decidir que entra y que se poda), **T-023** (fechas
huerfanas en la cabecera) y **T-024** (contradiccion menor del §1). En paralelo sigue pendiente
recibir del usuario el alcance y el objetivo del proyecto (T-004) para poder cerrar la etapa
`000_preproject`, y sigue abierto todo el ciclo de auditoria: `_audit/index.md` mantiene S-002 a
S-006 en `Pendiente`, sin ninguna auditoria entregada todavia por el auditor.

---

## 4. Hitos

| Hito | Etapa | Estado |
|---|---|---|
| `H-01` Metodo de trabajo y persistencia definidos | 000_preproject | Completado |
| `H-02` Ciclo de inicio y cierre de sesion operativo | 000_preproject | Completado |
| `H-03` Alcance y objetivo del proyecto definidos | 000_preproject | Pendiente |
| `H-04` Definicion tecnica (stack y arquitectura) | por definir | Pendiente |

---

## 5. Bitacora

### S-001 - Metodo de trabajo, persistencia y protocolo de cierre
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — primera jornada del repositorio; sin commit previo
  (este cierre es el commit inicial).
- **Que quedo hecho:** se crearon los siete archivos de `_persistence/` con indice por ancla,
  convenciones y codificacion propia (`T/D/C/A/L/DT`), con `S-XXX`/`H-nn` en `progress.md` e
  Importancia/Urgencia en `tasks.md` y `debt_tec.md`. Se creo `CLAUDE.md` con la identidad de
  `executor`, el rol de `auditor` y las secciones de Inicio de sesion, Registro del porque y
  Cierre de sesion. Se inicializo git en `main`, enlazado al remoto
  `https://github.com/jdrodriguez1000/AIzar_APP.git`, con `.gitignore` (incluye `temporal/`). Se
  crearon la skill `protocol-close` y el agente `session-closer` (sonnet), y la skill
  `protocol-start` y el agente `session-starter` (haiku). El material de partida vino de
  `temporal/` (skills y agentes de otro proyecto), analizado y adaptado a esta estructura.
- **Siguiente paso concreto:** recibir del usuario el alcance y el objetivo del proyecto (T-004)
  para poder cerrar la etapa `000_preproject`.

---

### S-002 - Informe de cierre para la terminal auditora
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — segunda jornada del repositorio, sobre el commit
  inicial `868ea7c` (S-001).
- **Que quedo hecho:** el cierre gana un Paso 6b obligatorio en `protocol-close` que escribe
  `_audit/S-XXX.md` **antes** del `git add`, para que quede dentro del mismo commit que describe
  y el auditor pueda anclar cada afirmacion a un `git show` real (T-012, D-016). El cambio se
  propago a la tabla de actores de `protocol-close` y `protocol-start`, al agente
  `session-closer`, y a `CLAUDE.md`. Se reescribio A-001: la **ida** del informe deja de ser
  supuesto (la fija D-016); queda abierto solo el **canal de vuelta** de las observaciones del
  auditor.
- **Siguiente paso concreto:** recibir del usuario el alcance y el objetivo del proyecto (T-004)
  para poder cerrar la etapa `000_preproject`.

### S-003 - Canal de vuelta de la auditoria aceptado e implementado
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — tercera jornada del repositorio, sobre el commit
  `dced7b5` (S-002).
- **Que quedo hecho:** se creo `_audit/index.md` con estado por fila para saber que sesiones
  faltan por auditar, en vez de asumir cual es "la ultima" (D-017, T-013). El auditor entrego su
  propuesta de canal de vuelta (`AIzar_Auditor/_review/CANAL.md`); se evaluo segun D-003 —se
  verifico primero que la carpeta existiera y fuera legible— y se acepto (D-018, T-014, primera
  tarea con `Origen: auditor`). Tres puntos suyos mejoraron la propuesta propia: el veredicto
  `Aceptado — pendiente`, el desempate por reversibilidad, y que un rechazo por coste sin `DT-XXX`
  sea por si solo un hallazgo. Se cerraron T-005, T-010 y A-001 (`Confirmado`); D-011 quedo
  `Revocada por D-018`. El auditor notifico ademas que audita la seccion 0 fila a fila con tres
  exigencias no escritas en `protocol-close`: se anadieron (D-019, T-015), porque `session-closer`
  no lee conversaciones, solo su skill. Se acepto tambien su limitacion del inventario de acciones
  irreversibles, vacio hasta que exista alcance (D-020, T-016, depende de T-004).
- **Sin auditoria pendiente de responder:** `_review/index.md` del auditor existe pero su tabla
  esta vacia — no hay ninguna auditoria entregada todavia. La fila de S-002 en `_audit/index.md`
  sigue en `Pendiente`.
- **Siguiente paso concreto:** recibir del usuario el alcance y el objetivo del proyecto (T-004)
  para poder cerrar la etapa `000_preproject`.

---

### S-004 - Los datos propios del proyecto se extraen a `PROJECT.md`
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — cuarta jornada del repositorio, sobre el commit
  `ec8e982` (S-003).
- **Que quedo hecho:** al preguntarse que haria falta para reutilizar este metodo en otros
  proyectos, se midio cuanto habia atado a AIzar: 17 menciones (nombre, rutas absolutas, remoto)
  repartidas en las dos skills, los dos agentes y `CLAUDE.md`. Se creo `PROJECT.md` en la raiz con
  identidad, rutas, control de versiones, carpetas propias y codigos; los protocolos, agentes,
  `CLAUDE.md` y `_audit/index.md` dejan de llevar esos datos dentro y los leen de ahi:
  `protocol-start` en su Paso 1b (primero, porque sin el no tiene las rutas de los pasos
  siguientes) y `protocol-close` al empezar el Paso 1 (D-021, T-017). Se aprovecho el cambio para
  generalizar tres menciones coyunturales — "el alcance de AIzar no esta definido (T-004)" — por
  una regla condicional que comprueba si el alcance esta registrado, en vez de asumir que sigue
  sin estarlo. Verificado tras el cambio: cero menciones especificas en `.claude/` y `CLAUDE.md`.
- **Lo que se dejo tal cual, a proposito:** `_audit/S-003.md` sigue mencionando "AIzar" fuera de
  `PROJECT.md`. No se toca: D-018 establece que un informe de auditoria ya entregado no se
  reescribe.
- **Sin auditoria pendiente de responder:** el tablero del auditor (`_review/index.md`) sigue con
  su tabla vacia — no hay ninguna auditoria entregada todavia. Las filas de S-002 y S-003 en
  `_audit/index.md` siguen en `Pendiente`.
- **Siguiente paso concreto:** recibir del usuario el alcance y el objetivo del proyecto (T-004)
  para poder cerrar la etapa `000_preproject`.

---

### S-005 - El metodo VERTICAL se incorpora y se ajusta al vocabulario propio
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — quinta jornada del repositorio, sobre el commit
  `31e2ff7` (S-004).
- **Que quedo hecho:** se incorporo `_methodology/` (`000_method.md` canonico del metodo
  VERTICAL, mas tres fuentes en `sources/`), se analizo entero y se ajusto contra el vocabulario
  ya en uso, una decision a la vez:
  - **D-022** — Feature y Scenario cambian a `FT-`/`SC-`; `T-` se fusiona en la tarea del
    proyecto con `Origen` obligatorio (canonico §46, nuevas §46.1 y §46.2, nota en §47, Anexo
    A.13).
  - **D-024** — el veredicto de los Gates se reparte en tres actos: evidencia (`executor`),
    dictamen (`auditor`), veredicto (**el usuario**). Escrito en `PROJECT.md` y `CLAUDE.md`; el
    canonico no se toca, porque su §32 manda escribir la asignacion fuera del documento.
  - **D-025** — trazabilidad por declaracion hacia arriba, sin indice central; se declara
    `_product/` (aun no creada) para cuando entre Descubrimiento (canonico nueva §47.1, Anexo
    A.14).
  - **D-026** — las etapas del proyecto son las de VERTICAL; `000_preproject` es la unica
    excepcion, y se abandona al cerrar T-004.
  - **D-027** — los ajustes internos de cada fase se aplazan a cuando se diseñe esa fase, con un
    esqueleto fijo de 8 secciones en `_methodology/phases/NNN_<fase>.md` (esqueleto documentado en
    `PROJECT.md`). De ahi nacen **T-018** y **T-019** (`Origen: metodo`), aparcadas por esta misma
    decision.
  - **D-023** — se adopta `contract.md`, del repositorio del auditor, como contrato vigente
    (version 1, 2026-08-28), tras leerlo entero y contrastarlo sin encontrar contradicciones
    contra `CLAUDE.md` y `_audit/index.md`. El renombrado de `_review/CANAL.md` a `channel.md` no
    exigio ningun cambio operativo; las menciones historicas a `CANAL.md` se dejaron intactas a
    proposito (describen correctamente lo que paso ese dia).
  - **L-002** — leccion nueva: un metodo externo se contrasta contra el vocabulario propio antes
    de adoptarlo, porque el choque no se ve como error, se ve como dos cosas distintas llamadas
    igual.
- **Lo que quedo sin resolver, a proposito o no:**
  - `_methodology/phases/` mete contenido propio del proyecto dentro de una carpeta declarada
    agnostica en `PROJECT.md`. Es un parche local, anotado en la propia D-027; la regla general
    agnostico/propio sigue sin decidirse.
  - `contract.md` §1 y §8 duplican datos que ya viven en `PROJECT.md`. Anotado como "duplicidad
    conocida, no resuelta" en D-023: el archivo es del auditor y de solo lectura para nosotros
    (C-002).
  - El dictamen del Gate que exige D-024 no tiene forma definida en `contract.md` §4, que solo
    contempla `R-XXX.md` auditando informes de sesion.
  - `_product/` esta declarada por D-025 pero no se creo ninguna carpeta ni archivo: es
    deliberado, se crea al entrar en Descubrimiento.
- **Sin auditoria pendiente de responder:** el tablero del auditor sigue con su tabla vacia.
  `_audit/index.md` mantiene S-002, S-003 y S-004 en `Pendiente`; se anade S-005 en el mismo
  estado.
- **Siguiente paso concreto:** recibir del usuario el alcance y el objetivo del proyecto (T-004)
  para poder cerrar la etapa `000_preproject`, entrar en `Descubrimiento` y diseñar la fase
  Prototipo (D-027) antes de empezarla.

---

### S-006 - La guia transversal `_global/guide.md` se analiza y se ajustan sus primeros cuatro puntos
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — sexta jornada del repositorio, sobre el commit
  `e9216f6` (S-005).
- **Que quedo hecho:** la sesion se dedico integramente a `_global/guide.md` (recetario
  transversal, 834 lineas, llego sin trackear). Se analizo entero contra un listado de nueve
  puntos y se aplicaron los primeros cuatro:
  - **D-028** — copia por proyecto con sello de version (`VERSION 1`), `_global/changelog.md`
    nuevo, y la regla de que en la copia se borra y se añade, nunca se reescribe. Se retira la
    pareja `lessons-global.md` (no se crea).
  - **D-029** — la fuente se congela en `_global/sources/GUIDE.md` (snapshot de
    `Edu_TripleS/GUIDE.md`, con regla de precedencia), y las trece flechas `↳ GUIDE §N` se anclan
    tambien por titulo. Verificada contra secretos antes de subir (apto). Fuera de alcance, por
    decision del usuario: `Proyectos_TripleS/_global/guide.md` y
    `Proyectos_TripleS/RandomAI/_guide/GUIDE.md`, que el borra por su cuenta.
  - **D-030** — dos ejes independientes deciden que aplica (quien construye / si el producto
    llama a un modelo en produccion); el Anexo A se parte en A (construccion) y B (producto);
    Windows pasa a Anexo C; `RR-008` se queda en el cuerpo sin marca.
  - **C-005** — `_global/sources/GUIDE.md` es de solo lectura. **A-004** — el sello de version
    aun no se ha ejercitado (no existe ninguna copia todavia).
  - **L-003** — un indice a mano necesita defensa explicita contra los generadores de TOC.
    **L-004** — un archivo duplicado sin marca hace que se edite el equivocado (paso durante esta
    misma sesion: `_global/` existia dos veces).
  - Se propone **DT-003** (pendiente de confirmar): `_global/` no tiene `.gitignore` propio ni
    esta declarada en `PROJECT.md`.
- **Lo que quedo pendiente, a proposito:** los puntos 5 a 9 del analisis de nueve — nivel de
  concrecion de `RR-003`, regla de asignacion de codigos `RR-NNN`, huecos de cobertura del
  recetario, fechas huerfanas de cabecera, y la contradiccion menor del §1 — quedan registrados
  como **T-020** a **T-024** para la proxima sesion, con contexto completo.
- **Sin auditoria pendiente de responder:** el tablero del auditor sigue con su tabla vacia.
  `_audit/index.md` mantiene S-002 a S-005 en `Pendiente`; se anade S-006 en el mismo estado.
- **Siguiente paso concreto:** retomar T-020 a T-024, en ese orden.

---

### S-007 - `_global/` se declara en `PROJECT.md` y se cierra DT-003
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — septima jornada del repositorio, sobre el commit
  `eb17b6e` (S-006).
- **Que quedo hecho:** sesion corta, dedicada a preparar el arranque de la auditoria pendiente
  (informes `S-002` a `S-006`, todos `Pendiente`). Se confirmo que la infraestructura de auditoria
  esta completa por ambos lados. Al revisar los informes contra lo registrado se detecto que
  `PROJECT.md` no declaraba `_global/` en su tabla «Carpetas propias» pese a que `S-006` la
  incorporo al repositorio; era **DT-003**, propuesta y sin confirmar. El usuario confirmo
  cerrarla:
  - **D-031** — `_global/` entra en la tabla «Carpetas propias» de `PROJECT.md`, con tres notas:
    se copia por proyecto con sello de version y no se comparte (D-028), `sources/GUIDE.md` es de
    solo lectura (C-005), y se versiona entera sin exclusiones en `.gitignore`.
  - **DT-003** pasa a `Implementada`, pagada el 2026-08-30. Sus dos mitades se cerraron por vias
    distintas: la fila en `PROJECT.md`, por edicion; la pregunta de si hacia falta alguna exclusion
    en `.gitignore`, por verificacion — no hacia falta ninguna, y la comprobacion queda escrita en
    `PROJECT.md` para que no se repita la duda.
- **Sin construccion de producto:** no hubo cambios de codigo en esta sesion.
- **Sin auditoria pendiente de responder:** el tablero del auditor (`AIzar_Auditor/_review/index.md`)
  sigue con su tabla vacia. `_audit/index.md` mantiene S-002 a S-006 en `Pendiente`; se anade S-007
  en el mismo estado.
- **Discrepancia detectada, no del diff propio sino del repositorio del auditor:** su
  `_persistence/progress.md` (linea 16-17) ya registra el `HEAD` del ejecutor como `eb17b6e`
  (S-006) y su delta sin auditar como los cinco commits S-002 a S-006; su `tasks.md` (V-003) ya
  nombra los cinco informes. No se encontro el desfase a `31e2ff7` que se esperaba encontrar segun
  el traspaso recibido al abrir el cierre — se deja constancia porque el traspaso y la evidencia
  discreparon, y manda la evidencia.
- **Siguiente paso concreto:** retomar T-020 a T-024 (puntos 5 a 9 del analisis de
  `_global/guide.md`), y sigue bloqueada T-004 (alcance y objetivo del proyecto).

---

## 6. Mapa de persistencia

| Archivo | Registra | Codigo |
|---|---|---|
| `progress.md` | Vision general, avance, ultimo hecho, siguiente paso | `S-XXX` sesiones, `H-nn` hitos |
| `tasks.md` | Tareas realizadas y por realizar | `T-XXX` |
| `decisions.md` | Decisiones tomadas en el proyecto | `D-XXX` |
| `constraints.md` | Limitaciones y restricciones del proyecto | `C-XXX` |
| `assumptions.md` | Supuestos vigentes por validar | `A-XXX` |
| `lessons.md` | Lecciones aprendidas durante la ejecucion | `L-XXX` |
| `debt_tec.md` | Deuda tecnica del proyecto | `DT-XXX` |
