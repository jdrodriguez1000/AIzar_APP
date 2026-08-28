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

---

## 1. Estado general

| Campo | Valor |
|---|---|
| Etapa actual | `000_preproject` |
| Ultima actualizacion | 2026-08-28 |
| Salud | En marcha |
| Avance de la etapa | Metodo de trabajo, persistencia, repositorio y protocolo de cierre listos; alcance del proyecto pendiente |
| Bloqueos activos | Alcance y objetivo del proyecto sin definir (T-004) |

---

## 2. Ultimo realizado

Se inicializo el repositorio git con remoto en GitHub, y quedo montado el ciclo de cierre de
sesion: la skill `protocol-close` adaptada a la estructura de `_persistence/`, y el agente
`session-closer` que es el unico que la ejecuta.

---

## 3. Siguiente paso

Recibir del usuario el alcance y el objetivo del proyecto para poder cerrar la etapa
`000_preproject` y pasar a la definicion tecnica.

---

## 4. Hitos

| Hito | Etapa | Estado |
|---|---|---|
| `H-01` Metodo de trabajo y persistencia definidos | 000_preproject | Completado |
| `H-02` Repositorio y protocolo de cierre operativos | 000_preproject | Completado |
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
