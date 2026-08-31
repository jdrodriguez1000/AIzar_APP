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
| [S-008](#s-008---se-cierran-los-cinco-puntos-restantes-del-analisis-de-_globalguidemd) | Se cierran los cinco puntos restantes del analisis de `_global/guide.md` | 2026-08-30 | 000_preproject |
| [S-009](#s-009---primera-auditoria-recibida-r-002-los-dos-hallazgos-se-aceptan-e-implementan) | Primera auditoria recibida (R-002): los dos hallazgos se aceptan e implementan | 2026-08-30 | 000_preproject |
| [S-010](#s-010---segunda-auditoria-recibida-r-003-los-tres-hallazgos-se-aceptan-para-la-proxima-sesion) | Segunda auditoria recibida (R-003): los tres hallazgos se aceptan para la proxima sesion | 2026-08-30 | 000_preproject |
| [S-011](#s-011---se-implementan-los-tres-hallazgos-de-r-003-t-029-t-030-t-031) | Se implementan los tres hallazgos de R-003 (T-029, T-030, T-031) | 2026-08-30 | 000_preproject |
| [S-012](#s-012---llega-r-004-y-se-implementan-sus-cinco-hallazgos-t-032-a-t-036-mas-t-037-de-iniciativa-propia) | Llega R-004 y se implementan sus cinco hallazgos (T-032 a T-036), mas T-037 de iniciativa propia | 2026-08-30 | 000_preproject |
| [S-013](#s-013---llega-r-005-y-se-aceptan-sus-cinco-hallazgos-cuatro-se-implementan-uno-se-acepta-como-regla) | Llega R-005 y se aceptan sus cinco hallazgos; cuatro se implementan, uno se acepta como regla | 2026-08-30 | 000_preproject |
| [S-014](#s-014---llega-r-006-y-se-aceptan-e-implementan-sus-tres-hallazgos-mas-dos-recomendaciones-de-su-seccion-5) | Llega R-006 y se aceptan e implementan sus tres hallazgos, mas dos recomendaciones de su seccion 5 | 2026-08-31 | 000_preproject |

---

## 1. Estado general

| Campo | Valor |
|---|---|
| Etapa actual | `000_preproject` |
| Ultima actualizacion | 2026-08-31 |
| Salud | En marcha |
| Avance de la etapa | Metodo de trabajo, persistencia, repositorio, ciclo completo inicio/cierre, canal de vuelta con la auditoria, datos propios del proyecto en `PROJECT.md`, el metodo VERTICAL incorporado y ajustado, y el analisis de nueve puntos de `_global/guide.md` completo (`guide.md` en `VERSION 6`). T-026 registra que falta disenar la fase `Descubrimiento` antes de entrar en ella (bloqueante). Llego la **quinta auditoria** (`R-006`, sobre `S-006`, commit `eb17b6e`): **Con hallazgos (3)** — F-016 (`Media`), F-017, F-018 (`Baja`). Los tres se verificaron contra `HEAD`, los tres persistian, los tres se aceptaron y se implementaron (`D-046`): T-044 (la marca de maquina 💻 no entra en el ritual de poda, `guide.md` sube a VERSION 6), T-045 (correccion de capitalizacion de `_global/changelog.md` en `D-028`; al cerrarla se descubrio que la propia nota de correccion rompia el criterio de cierre del hallazgo — `L-010`), T-046 (`C-005` ampliada a las dos carpetas `sources/` y retitulada, con disparador para revisar las flechas `↳ GUIDE §N` al retomar un snapshot). Se aceptaron ademas dos recomendaciones de la seccion 5 del informe, que no eran hallazgos: T-047 (§5.4 — el sello del paso 2 gana una tercera linea, `Comprobacion del desfase`, y `A-004` se reescribe en dos tiempos de validacion) y T-048 (§5.2 — la regla de comando y salida cruda se extiende a las comprobaciones de iniciativa propia, no solo a las de `Origen: auditor`; tocada en `CLAUDE.md` y en el propio `protocol-close`). §5.3 quedo cerrada sin accion porque `DT-003` ya estaba pagada. Las cinco auditorias previas (`R-002` a `R-005`) siguen implementadas e integras. Sigue pendiente el alcance del proyecto |
| Bloqueos activos | Alcance y objetivo del proyecto sin definir (T-004); bloquea a su vez T-025 y el diseño de la fase Descubrimiento. **T-026** (disenar la fase `Descubrimiento` antes de entrar en ella) sin resolver y bloqueante por si misma |

---

## 2. Ultimo realizado

**Llego `R-006`** (`../AIzar_Auditor/_review/R-006.md`), auditando `_audit/S-006.md` sobre el
commit `eb17b6e`. Veredicto: **Con hallazgos (3)** — `F-016` (`Media`), `F-017`, `F-018` (`Baja`).
Llego con `S-013` ya cerrada, asi que recogerla abrio jornada nueva.

**Verificacion antes de tratarlos:** los tres se comprobaron contra `HEAD` (`e1fb1eb`), no contra
el commit auditado. **Los tres persisten**; comando y salida cruda quedaron en cada `T-XXX`. Acuse
de recibo: la fila `S-006` de `_audit/index.md` paso de `Pendiente` a `Con hallazgos`, con la ruta
de `R-006.md` y los tres codigos.

**Los tres hallazgos se aceptaron (`D-046`), cero rechazos:**

- **F-016 -> T-044** (`Media`) — la tabla de marcas de `_global/guide.md` declaraba cuatro valores
  y solo daba regla de poda a tres; la marca de maquina 💻 quedaba sin fila en el paso 3. Se
  declara que 💻 **no se poda** — es propiedad de quien lee, no del proyecto (`D-047`) — y la
  columna de la tabla se corrige. `guide.md` sube a **VERSION 6**.
- **F-017 -> T-045** (`Baja`) — `D-028` citaba el archivo que ella misma crea (`_global/changelog.md`)
  en mayusculas, la unica cita discrepante entre cinco. Corregida, con nota fechada. **Al correr el
  criterio de cierre del propio hallazgo contra la correccion se descubrio que la nota deletreaba
  la cadena prohibida**, dejando el `grep` en rojo para siempre; se reescribio para describir el
  error sin reproducirlo (`L-010`).
- **F-018 -> T-046** (`Baja`) — `C-005` citaba un precedente («misma regla que
  `_methodology/sources/`») que no existia como `C-XXX`. Se amplia `C-005` a las dos carpetas
  `sources/` y se retitula, en vez de crear una `C-006` gemela (`D-048`); se le añade ademas el
  disparador de `R-006` §5.1 — revisar las flechas `↳ GUIDE §N` al retomar un snapshot.

**Dos recomendaciones de la seccion 5, aceptadas sin ser hallazgos:**

- **§5.4 -> T-047** — `A-004` se validaba en «la primera copia real», pero ese dia el mecanismo se
  estrena y se valida a la vez: un supuesto cuya refutacion es indistinguible de su funcionamiento
  no se detecta observando (`D-049`). El sello del paso 2 gana una tercera linea, `Comprobacion
  del desfase`, y `A-004` se valida en dos tiempos: cada copia (que la linea existe) y la segunda
  copia (que alguien comparo de verdad).
- **§5.2 -> T-048** — el auditor repitio por su cuenta el escaneo de secretos de `D-029` y senalo
  que la regla de comando y salida cruda (`T-031`) solo cubria las entradas con `Origen: auditor`,
  no las de iniciativa propia. Se extiende la regla en `CLAUDE.md` y en el propio `protocol-close`
  (`D-050`).

**§5.3 se cierra sin accion:** su `PROPUESTA` sobre `DT-003` ya estaba resuelta — `DT-003` esta
`Implementada` y `Confirmada` desde `S-007`.

`decisions.md` gana `D-046` a `D-050`. `assumptions.md` reescribe `A-004` (`T-047`), citando el
enunciado anterior antes de sustituirlo. `constraints.md` amplia y retitula `C-005` (`T-046`).
`lessons.md` gana `L-010`. No hubo construccion de producto ni cambios de codigo de aplicacion.

---

## 3. Siguiente paso

**Las cinco tareas de esta sesion (T-044 a T-048) quedan `Implementada`.** No hay ninguna abierta
que dispare el siguiente paso. El siguiente paso concreto sigue siendo retomar las dos tareas
bloqueantes en espera, sin cambios respecto a la sesion anterior:

1. **T-004** (`Alta`, bloqueante) — recibir del usuario el alcance y objetivo del proyecto. Bloquea
   a `T-025`, al diseno de la fase `Descubrimiento`, y a `T-043`.
2. **T-026** (`Alta`, bloqueante) — disenar la fase `Descubrimiento` antes de entrar en ella
   (D-027); depende de que `T-004` fije el alcance.

En el informe de esta sesion (`_audit/S-014.md`) se responde a `R-006` en su seccion 0 con los
tres veredictos: `Implementado` (F-016, F-017, F-018).

El ciclo de auditoria sigue abierto: `_audit/index.md` mantiene S-007 a S-013 en `Pendiente`
(S-002 a S-006 ya con hallazgos recogidos), mas la nueva `S-014.md` que este cierre añade.

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

### S-008 - Se cierran los cinco puntos restantes del analisis de `_global/guide.md`
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — el analisis de nueve puntos de `_global/guide.md`
  (abierto en S-006) queda completo: T-016 a T-024 resueltas. T-004 sigue siendo el unico bloqueo
  para salir de la etapa.
- **Que quedo hecho, segun el diff:** T-020 a T-024 pasan a `Implementada` en `tasks.md`, cada una
  con su resultado escrito. `decisions.md` gana D-032, D-033, D-034 y D-035, cada una con sus
  alternativas descartadas. `_global/guide.md` sube de `VERSION 1` a `VERSION 5` (una linea de
  changelog por version en `_global/changelog.md`), con: la subseccion de `RR-003` con los
  patrones anclados de los tres barridos (D-032); la subseccion de §1 sobre estabilidad de
  codigos `RR-NNN` y los tres destinos de algo nuevo que aparece en una copia (D-033); el criterio
  de admision de §1 y la receta nueva `RR-013` (D-034); y la cabecera sin fechas mas la excepcion
  de lectura completa de §1 (D-035). Se anadio **T-025** («Juzgar las cuatro candidatas aplazadas
  del recetario»), `No implementada`, dependiente de T-004. Tambien se corrigio una errata en la
  linea v1 de `changelog.md` (nombraba solo «Anexo B (Windows)»; ahora nombra los tres anexos que
  el archivo realmente tiene).
- **Los cuatro archivos del porque:** `decisions.md` ya venia escrito con D-032 a D-035 al llegar
  este cierre. No hubo entradas nuevas en `assumptions.md`, `constraints.md` ni `lessons.md`; el
  diff de esta sesion no muestra ningun supuesto sin confirmar, ningun limite nuevo ni ninguna
  leccion aprendida por error/acierto que exigiera una.
- **Sin construccion de producto:** no hubo cambios de codigo de aplicacion.
- **Siguiente paso concreto:** recibir del usuario el alcance y el objetivo del proyecto (T-004),
  que desbloquea a su vez T-025.

---

### S-009 - Primera auditoria recibida (R-002): los dos hallazgos se aceptan e implementan
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — sobre el commit `3228ca1` (registro suelto de T-026,
  posterior al cierre de S-008). T-004 sigue siendo el unico bloqueo de fondo de la etapa; T-026
  se suma como bloqueo propio, sin depender de T-004 para existir.
- **Desfase encontrado al abrir esta sesion, corregido aqui:** el commit `3228ca1` registro
  **T-026** («Disenar la fase `Descubrimiento` antes de entrar en ella», `No implementada` ·
  `Alta` · `Bloqueante`) en `tasks.md`, pero no traia actualizacion de `progress.md` — su propio
  mensaje de commit lo advierte («Registro posterior al cierre de S-008 ... quedara descrita en el
  informe de la sesion que la ejecute»). El archivo quedo con `Estado general` y bitacora
  congelados en `S-008`. Esta entrada pone `progress.md` al dia con T-026 y con el trabajo de esta
  sesion, junto.
- **Que quedo hecho, segun el diff:** llego `R-002`, la **primera auditoria entregada del
  proyecto** (`..\AIzar_Auditor\_review\R-002.md`), auditando `_audit/S-002.md` sobre el commit
  `dced7b5`. Verificada antes de tratarla: el hash coincide con
  `git log -1 -- _audit/S-002.md`, los 10 archivos auditados coinciden con
  `git show --stat dced7b5`, y `contract.md` sigue en version `1` en ambos lados. Acuse de recibo:
  la fila de `S-002` en `_audit/index.md` paso de `Pendiente` a `Con hallazgos`, con la ruta del
  informe. Veredicto: **Con hallazgos (2)**, ambos `Media` / `REVERSIBLE`. Los dos se evaluaron
  (D-036) — no en automatico— y se aceptaron e **implementaron** en esta misma sesion:
  - **F-001 -> T-027** — el Paso 6b de `protocol-close` no tenia comprobacion que pudiera salir
    roja sobre el anclaje del informe al commit. Se anadio el **Paso 7b** a
    `.claude/skills/protocol-close/SKILL.md` (despues del commit, antes del push), con
    `git show --stat --name-only HEAD -- _audit/S-XXX.md` y la misma consulta para
    `_audit/index.md`, tabla de tres resultados, y la linea fija del Paso 8 sustituida por una de
    tres salidas. Propagado a `.claude/agents/session-closer.md`.
  - **F-002 -> T-028** — `A-001` se habia reescrito en el sitio en S-002, reutilizando el codigo
    contra la convencion del propio archivo (`A-XXX` no se reutiliza). Se anadio a la entrada de
    `A-001` en `assumptions.md` un bloque `♻️ Reescrito en S-002` con el enunciado anterior
    literal, para que quede recuperable sin ir al `git log`.
- **Los cuatro archivos del porque:** `decisions.md` gana `D-036` (evaluacion completa de ambos
  hallazgos, con las tres alternativas descartadas de `F-002`); `lessons.md` gana `L-005` (un paso
  obligatorio sin comando que pueda fallar es una intencion, no una obligacion). Sin entradas
  nuevas en `constraints.md`. `assumptions.md` no gana codigo nuevo — `A-001` sigue `Confirmado`;
  solo recibio la nota de reescritura que pedia T-028.
- **Sin construccion de producto:** no hubo cambios de codigo de aplicacion.
- **Siguiente paso concreto:** **T-026** (disenar `_methodology/phases/001_descubrimiento.md`) y,
  en paralelo, recibir del usuario el alcance y el objetivo del proyecto (**T-004**).

---

### S-010 - Segunda auditoria recibida (R-003): los tres hallazgos se aceptan para la proxima sesion
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — sobre el commit `beb782a` (S-009). T-004 y T-026
  siguen siendo los dos bloqueos de fondo de la etapa; ninguno se toco en esta sesion.
- **Que quedo hecho, segun el diff:** llego `R-003`, la **segunda auditoria entregada del
  proyecto** (`..\AIzar_Auditor\_review\R-003.md`), auditando `_audit/S-003.md` sobre el commit
  `ec8e982`. Verificada antes de tratarla, con comando y salida literal dentro de `D-037`: el hash
  coincide con `git log -1 -- _audit/S-003.md`, y los tres hallazgos se comprobaron uno a uno sobre
  `HEAD` — los tres persisten. Acuse de recibo: la fila de `S-003` en `_audit/index.md` paso de
  `Pendiente` a `Con hallazgos`, con la ruta de `R-003.md`. Veredicto: **Con hallazgos (3)** —
  `F-003` `Media`, `F-004`/`F-005` `Baja`, los tres `REVERSIBLE` y de coherencia interna (ninguna
  afirmacion de `S-003` resulto falsa).
  - **F-003 -> T-029** (`Alta`, `No implementada`) — declarar en `CLAUDE.md` y en el Paso 6b de
    `protocol-close` que el eje reversible/irreversible se aplica a criterio, citando `D-020`.
  - **F-004 -> T-030** (`Baja`, `No implementada`) — corregir en `D-020` la referencia `T-015` ->
    `T-016`.
  - **F-005 -> T-031** (`Media`, `No implementada`) — exigir comando y salida cruda en las
    decisiones que verifican antes de aceptar; no se corrige reescribiendo `D-018`.
- **Decision del usuario:** los tres hallazgos se **aceptan**, pero **no se implementan en esta
  sesion**: quedan para la proxima, expresamente.
- **Los cuatro archivos del porque:** `decisions.md` gana `D-037` (evaluacion completa de los tres
  hallazgos, tres alternativas descartadas, y el bloque de verificacion con cuatro comandos y su
  salida literal); `lessons.md` gana `L-006` (una regla decidida y no llevada al archivo operativo
  no rige). Sin entradas nuevas en `constraints.md` ni `assumptions.md`.
- **Sin construccion de producto:** no hubo cambios de codigo de aplicacion.
- **Siguiente paso concreto:** implementar **T-029, T-030 y T-031** en la proxima sesion. T-004 y
  T-026 siguen abiertas y bloqueantes, pero no son el siguiente paso de esta transicion.

---

### S-011 - Se implementan los tres hallazgos de R-003 (T-029, T-030, T-031)
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — sobre el commit `3d87e03` (S-010). T-004 y T-026
  siguen siendo los dos bloqueos de fondo de la etapa; ninguno se toco en esta sesion.
- **Que quedo hecho, segun el diff:** se ejecuto lo que `D-037` ya habia decidido en S-010, sin
  reabrir el criterio:
  - **T-029** (`Alta`) — `CLAUDE.md`, seccion «Cuando no estemos de acuerdo», gana una vinieta que
    cita `D-020` y exige declarar la clasificacion reversible/irreversible en la propia respuesta
    mientras `T-016` no cierre, aclarando que los cuatro ejemplos entre parentesis (borrar datos,
    publicar, migrar, gastar) son ejemplos y no un inventario. La misma exigencia se anadio al
    Paso 6b de `.claude/skills/protocol-close/SKILL.md`, seccion nueva «Si el rechazo clasifica el
    asunto como reversible o irreversible, dilo como criterio».
  - **T-030** (`Baja`) — en `_persistence/decisions.md`, el cuerpo de `D-020` corrige «Se crea
    T-015» a «Se crea T-016». Se toco una sola linea (`git diff --stat`: 1 insercion, 1 borrado);
    la segunda aparicion de la cadena `T-015`, que es la salida cruda del bloque de verificacion de
    `D-037` (`git grep -n "Se crea T-015"`), se dejo intacta a proposito — es historia, no prosa.
  - **T-031** (`Media`) — `CLAUDE.md`, misma seccion, y el Paso 6 de `SKILL.md` exigen desde ahora
    que toda decision con `Origen: auditor` que verifique algo lleve la orden ejecutada literal y
    su salida cruda, no un veredicto («se comprobo», «verificado», «existe y es legible»). Se deja
    escrito que la regla rige hacia adelante y que `D-018` no se reescribe.
- **Los cuatro archivos del porque:** `lessons.md` gana **L-007** («al corregir un codigo mal
  escrito, la salida cruda que lo cita no se toca»), registrando el hallazgo hecho al
  aplicar T-030: la cadena `T-015` aparecia dos veces y un reemplazo global habria reescrito la
  evidencia de `D-037`. No se registro ninguna `D-XXX` nueva: la decision que gobierna esta sesion
  ya existia (`D-037`, de S-010) y aqui solo se ejecuto. Sin entradas nuevas en `constraints.md` ni
  `assumptions.md`.
- **Sin construccion de producto:** no hubo cambios de codigo de aplicacion; todo el diff es
  documental (`CLAUDE.md`, la skill `protocol-close`, y tres archivos de `_persistence/`).
- **`tasks.md`:** `T-029`, `T-030` y `T-031` pasan de `No implementada` a `Implementada`
  (2026-08-30).
- **Siguiente paso concreto:** retomar **T-004** (alcance y objetivo del proyecto) y, con eso
  resuelto, **T-026** (diseno de la fase `Descubrimiento`) — las dos bloqueantes de la etapa.

---

### S-012 - Llega R-004 y se implementan sus cinco hallazgos (T-032 a T-036), mas T-037 de iniciativa propia
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — sobre el commit `fc21369` (S-011). T-004 y T-026
  siguen siendo los dos bloqueos de fondo de la etapa; ninguno se toco en esta sesion.
- **Que quedo hecho, segun el diff:** llego `R-004`, la **tercera auditoria entregada del
  proyecto** (`../AIzar_Auditor/_review/R-004.md`), auditando `_audit/S-004.md` sobre el commit
  `31e2ff7`. Verificado antes de tratarla: cada uno de los cinco hallazgos se comprobo de nuevo
  contra `HEAD`, no solo contra `31e2ff7` — los cinco persisten, con comando y salida cruda en
  `D-038` y en cada tarea (`T-031`). Acuse de recibo: la fila `S-004` de `_audit/index.md` paso de
  `Pendiente` a `Con hallazgos`, con la ruta de `R-004.md` y los cinco codigos. Veredicto: **Con
  hallazgos (5)** — `F-006`, `F-007`, `F-008` `Media`, `F-009`, `F-010` `Baja`, los cinco
  `REVERSIBLE` a criterio.
  - **F-006 -> T-032** (`Media`) — `PROJECT.md` gana la fila «Estado de los hallazgos» con la ruta
    del `findings.md` del auditor.
  - **F-007 -> T-033** (`Media`) — el Paso 1c de `protocol-start` vuelve a ser una orden ejecutable
    literal; `PROJECT.md` declara la forma canonica POSIX de sus rutas relativas.
  - **F-008 -> T-034** (`Media`) — codigos vivos generalizados en `protocol-close/SKILL.md`;
    ampliado por iniciativa propia de una linea a cuatro.
  - **F-009 -> T-035** (`Baja`) — `D-021` corrige la enumeracion de archivos (cinco -> seis); el
    comando y su salida se anexan como nota fechada hoy, sin incrustarse en el cuerpo original.
  - **F-010 -> T-036** (`Baja`) — `C-002` queda sin rutas literales, remitido a `PROJECT.md`.
  - **T-037** (`Origen: executor`) — no es un hallazgo: nace de la seccion 5.3 de `R-004`. Se
    escribe el control de regresion de `D-021` (`git grep`, patron y ambito acotado) en el Paso 1b
    de `protocol-close`.
- **Decision del usuario:** ninguna intervencion directa; los cinco hallazgos se evaluaron,
  aceptaron e implementaron en la misma jornada por `executor`.
- **Los cuatro archivos del porque:** `decisions.md` gana `D-038` (evaluacion en bloque de los
  cinco hallazgos; `F-009` se acepta en el fondo pero no se corrige reescribiendo `D-021`, para no
  chocar con `D-037`/`T-031`), `D-039` (forma canonica POSIX de las rutas y por que el Paso 1c
  conserva la indireccion en vez de escribir la ruta dentro) y `D-040` (dos ampliaciones de alcance
  sobre `F-008`, incluida una tercera fuga — `| Rama | main |` — que ningun control existente
  detectaba). `lessons.md` gana `L-008`: al implementar `F-007` con la opcion (a) del hallazgo (ruta
  escrita en el bloque), el control de `D-021` dejo de dar cero — la correccion reintroducia el
  nombre del auditor dentro de `.claude/`, revirtiendo `D-021`. Se revirtio y se tomo la opcion (b).
  Sin entradas nuevas en `assumptions.md` esta sesion.
- **Sin construccion de producto:** no hubo cambios de codigo de aplicacion; todo el diff es
  documental (`PROJECT.md`, las dos skills, `_audit/index.md`, cuatro archivos de `_persistence/`).
- **`tasks.md`:** `T-032` a `T-037` pasan a `Implementada` (2026-08-30).
- **Siguiente paso concreto:** retomar **T-004** (alcance y objetivo del proyecto) y, con eso
  resuelto, **T-026** (diseno de la fase `Descubrimiento`) — las dos bloqueantes de la etapa.

---

### S-013 - Llega R-005 y se aceptan sus cinco hallazgos; cuatro se implementan, uno se acepta como regla
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — sobre el commit `57f3f2a` (S-012). T-004 y T-026
  siguen siendo los dos bloqueos de fondo de la etapa; ninguno se toco en esta sesion.
- **Que quedo hecho, segun el diff:** llego `R-005`, la **cuarta auditoria entregada del
  proyecto** (`../AIzar_Auditor/_review/R-005.md`), auditando `_audit/S-005.md` sobre el commit
  `e9216f6`. Verificado antes de tratarla: los cinco hallazgos se comprobaron contra `HEAD`
  (`57f3f2a`), no contra `e9216f6` — cuatro persisten, con comando y salida cruda en cada `T-XXX`
  (`T-031`); uno (`F-015`) ya no persiste. Acuse de recibo: la fila `S-005` de `_audit/index.md`
  paso de `Pendiente` a `Con hallazgos`, con la ruta de `R-005.md` y los cinco codigos. Veredicto:
  **Con hallazgos (5)** — `F-011`, `F-012`, `F-013` `Media`, `F-014`, `F-015` `Baja`, los cinco
  `REVERSIBLE` a criterio. **Los cinco se aceptaron, cero rechazos** (`D-041`).
  - **F-011 -> T-038** (`Media`) — la tabla de Convenciones de `Origen` en `tasks.md` admitia tres
    valores cuando ya se usaban cinco; ahora enumera los cinco con su criterio de admision.
  - **F-012 -> A-005 + T-039** (`Media`) — `D-024` da por hecho que el dictamen de un Gate tiene
    donde escribirse; `contract.md` §4 no lo cubre. Registrado por partida doble (`D-042`).
    **Bilateral, elevado al usuario y a la sesion principal del auditor.**
  - **F-013 -> T-040** (`Media`, subida a `Alta`) — la version de `contract.md` no se comparaba
    nunca. Paso 1d nuevo en `protocol-start`, primera ejecucion sin desfase.
  - **F-014 -> T-041** (`Baja`) — `Origen` en `debt_tec.md` cargaba texto de confirmacion en tres
    entradas (`DT-001`, `DT-002`, y `DT-003` que el auditor no vio); campo `Confirmacion` nuevo,
    separado de `Estado` (`D-045`).
  - **F-015** (`Baja`) — el numero de decisiones de `S-005` no coincidia entre tres sitios; la
    cifra viva ya no existe en el registro, las otras dos son inmutables por `D-018`. **No se
    reescribe nada**: se acepta como regla hacia adelante (`D-041`).
  - **T-042** (`Baja`, `Origen: executor`) — no es hallazgo: el control de `L-008`, corrido tras
    tocar `.claude/` por `T-040`, encontro un ultimo codigo vivo (`DT-003`) sin generalizar por
    `T-034`, y ademas falso; corregido a `DT-NNN`.
  - **T-043** (`Baja`, `Origen: auditor`, no-hallazgo) — recomendacion de `R-005` §5.1: marcar en
    `_methodology/` que `phases/` no se copia. Aceptada en el fondo, aplazada porque presupone la
    regla que `DT-002` no ha decidido (`D-044`).
  - **Segundo asunto bilateral:** el auditor rechazo que `contract.md` cite `PROJECT.md`; el
    rechazo se acepta (`D-043`) y `DT-001` queda con una sola via de pago: `F-013`/`T-040`.
- **Decision del usuario:** ninguna intervencion directa; los cinco hallazgos se evaluaron,
  aceptaron y (cuatro) implementaron en la misma jornada por `executor`.
- **Los cuatro archivos del porque:** `decisions.md` gana `D-041` a `D-045`. `assumptions.md` gana
  `A-005` (el dictamen de Gate como supuesto no confirmado, disparador «al diseñar la fase
  Prototipo»). `lessons.md` gana `L-009`: un `grep` estructural sobre `_persistence/` cuenta como
  entrada real una linea que es salida cruda citada dentro de un bloque cercado — asi llego el
  reporte del arranque de esta jornada sobre `C-002` en `tasks.md`, comprobado y descartado como
  desfase real. `constraints.md` sin cambios: ningun hallazgo de `R-005` introdujo una restriccion
  nueva.
- **Sin construccion de producto:** no hubo cambios de codigo de aplicacion; todo el diff es
  documental (una skill, `_audit/index.md`, cinco archivos de `_persistence/`).
- **`tasks.md`:** `T-038`, `T-040`, `T-041`, `T-042` pasan a `Implementada` (2026-08-30). `T-039` y
  `T-043` quedan `No implementada`, cada una con su disparador escrito.
- **Siguiente paso concreto:** retomar **T-004** (alcance y objetivo del proyecto) y, con eso
  resuelto, **T-026** (diseno de la fase `Descubrimiento`) — las dos bloqueantes de la etapa.
  `T-039` y `T-043` no son el siguiente paso: ninguna esta disparada todavia.

---

### S-014 - Llega R-006 y se aceptan e implementan sus tres hallazgos, mas dos recomendaciones de su seccion 5
| Campo | Valor |
|---|---|
| Fecha | 2026-08-31 |
| Etapa | 000_preproject |

- **Etapa del proyecto:** `000_preproject` — sobre el commit `e1fb1eb` (S-013), ya cerrado. T-004 y
  T-026 siguen siendo los dos bloqueos de fondo de la etapa; ninguno se toco en esta sesion.
- **Que quedo hecho, segun el diff:** llego `R-006`, la **quinta auditoria entregada del proyecto**
  (`../AIzar_Auditor/_review/R-006.md`), auditando `_audit/S-006.md` sobre el commit `eb17b6e`.
  Verificado antes de tratarlos: los tres hallazgos se comprobaron contra `HEAD` (`e1fb1eb`), no
  contra `eb17b6e` — **los tres persisten**, con comando y salida cruda en cada `T-XXX`. Acuse de
  recibo: la fila `S-006` de `_audit/index.md` paso de `Pendiente` a `Con hallazgos`, con la ruta
  de `R-006.md` y los tres codigos. Veredicto: **Con hallazgos (3)** — `F-016` `Media`, `F-017`,
  `F-018` `Baja`. **Los tres se aceptaron, cero rechazos** (`D-046`).
  - **F-016 -> T-044** (`Media`) — la marca de maquina 💻 en `_global/guide.md` no tenia regla de
    poda en el paso 3 pese a que el ritual se presenta como «mecanico». Se declara que 💻 no se
    poda —es propiedad de quien lee, no del proyecto— (`D-047`); `guide.md` sube a **VERSION 6**.
  - **F-017 -> T-045** (`Baja`) — `D-028` citaba `_global/changelog.md` en mayusculas. Corregida,
    con nota fechada. Al correr el criterio de cierre del hallazgo contra la propia correccion se
    descubrio que la nota deletreaba la cadena prohibida, dejando el `grep` en rojo para siempre;
    reescrita para describirlo sin reproducirlo (`L-010`).
  - **F-018 -> T-046** (`Baja`) — `C-005` citaba un precedente sin `C-XXX` propio
    (`_methodology/sources/`). Se amplia `C-005` a las dos carpetas y se retitula (`D-048`), con el
    disparador de `R-006` §5.1 (revisar las flechas `↳ GUIDE §N` al retomar un snapshot).
  - **T-047** (`Media`, `Origen: auditor`, no-hallazgo) — recomendacion de `R-006` §5.4: `A-004` se
    reescribe en dos tiempos de validacion, y el sello del paso 2 gana una tercera linea,
    `Comprobacion del desfase` (`D-049`).
  - **T-048** (`Media`, `Origen: auditor`, no-hallazgo) — recomendacion de `R-006` §5.2: la regla de
    comando y salida cruda (`T-031`) se extiende a las comprobaciones de iniciativa propia, no solo
    a las de `Origen: auditor` (`D-050`), en `CLAUDE.md` y en el propio `protocol-close`.
  - **§5.3 cerrada sin accion:** su `PROPUESTA` sobre `DT-003` ya estaba resuelta —`DT-003` esta
    `Implementada` y `Confirmada` desde `S-007`.
- **Decision del usuario:** ninguna intervencion directa; los tres hallazgos y las dos
  recomendaciones se evaluaron, aceptaron e implementaron en la misma jornada por `executor`.
- **Los cuatro archivos del porque:** `decisions.md` gana `D-046` a `D-050`. `assumptions.md`
  reescribe `A-004` (`T-047`), citando literalmente el enunciado anterior antes de sustituirlo.
  `constraints.md` amplia y retitula `C-005` (`T-046`), con su fila de indice cambiada. `lessons.md`
  gana `L-010`: la nota que explica una correccion puede romper el control que la cierra, si el
  criterio de cierre es una busqueda de texto sobre el mismo archivo.
- **Sin construccion de producto:** no hubo cambios de codigo de aplicacion; todo el diff es
  documental (`CLAUDE.md`, la skill `protocol-close`, `_audit/index.md`, `_global/guide.md` y
  `changelog.md`, cinco archivos de `_persistence/`).
- **`tasks.md`:** `T-044` a `T-048` pasan a `Implementada` (2026-08-31).
- **Siguiente paso concreto:** retomar **T-004** (alcance y objetivo del proyecto) y, con eso
  resuelto, **T-026** (diseno de la fase `Descubrimiento`) — las dos bloqueantes de la etapa.

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
