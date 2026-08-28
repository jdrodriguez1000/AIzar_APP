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

---

## 1. Estado general

| Campo | Valor |
|---|---|
| Etapa actual | `000_preproject` |
| Ultima actualizacion | 2026-08-28 |
| Salud | En marcha |
| Avance de la etapa | Metodo de trabajo, persistencia, repositorio, ciclo completo inicio/cierre y canal de vuelta con la auditoria listos; alcance del proyecto pendiente |
| Bloqueos activos | Alcance y objetivo del proyecto sin definir (T-004); bloquea a su vez T-016 |

---

## 2. Ultimo realizado

Se creo `_audit/index.md`, indice de informes con estado por fila (`Pendiente` / `Sin hallazgos` /
`Con hallazgos`), para saber cuales sesiones quedan sin auditar en vez de asumir que la ultima es
la unica pendiente (D-017, T-013). El auditor entrego su propuesta de canal de vuelta en
`AIzar_Auditor/_review/CANAL.md`; se evaluo segun D-003 —verificando primero que la carpeta
existiera y fuera legible— y se acepto (D-018, T-014, primera tarea con `Origen: auditor`): Paso 1c
en `protocol-start`, seccion 0 con tres veredictos en el informe del Paso 6b de `protocol-close`,
y las reglas de recepcion/desacuerdo en `CLAUDE.md`. Con eso cerraron T-005, T-010 y A-001
(`Confirmado`); D-011 quedo `Revocada por D-018`. El auditor senalo ademas que audita la seccion 0
fila a fila con tres exigencias que no estaban escritas en `protocol-close`: se anadieron (D-019,
T-015). Y que su inventario de acciones irreversibles esta vacio hasta que exista alcance: se
acepto que el desempate se aplique a criterio mientras tanto (D-020, T-016, depende de T-004).

---

## 3. Siguiente paso

Recibir del usuario el alcance y el objetivo del proyecto para poder cerrar la etapa
`000_preproject` y pasar a la definicion tecnica.

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
