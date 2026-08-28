# tasks.md

> Registro de las tareas **realizadas** y de las tareas **por realizar**.
> Cada tarea tiene codigo `T-XXX`, estado, importancia y urgencia.

---

## Indice

| Codigo | Tarea | Estado | Importancia | Urgencia |
|---|---|---|---|---|
| [T-001](#t-001---crear-los-archivos-base-de-_persistence) | Crear los archivos base de `_persistence/` | Implementada | Alta | Bloqueante |
| [T-002](#t-002---crear-claudemd-con-las-reglas-executorauditor) | Crear `CLAUDE.md` con las reglas executor/auditor | Implementada | Alta | Bloqueante |
| [T-003](#t-003---estructurar-los-archivos-de-persistencia-indice-codigos-y-estados) | Estructurar los archivos de persistencia (indice, codigos y estados) | Implementada | Alta | Bloqueante |
| [T-004](#t-004---recibir-el-alcance-y-objetivo-del-proyecto) | Recibir el alcance y objetivo del proyecto | No implementada | Alta | Bloqueante |
| [T-005](#t-005---definir-el-canal-de-entrega-de-la-auditoria) | Definir el canal de entrega de la auditoria | No implementada | Media | No bloqueante |
| [T-006](#t-006---inicializar-el-repositorio-git-y-enlazarlo-con-github) | Inicializar el repositorio git y enlazarlo con GitHub | Implementada | Alta | Bloqueante |
| [T-007](#t-007---crear-la-skill-protocol-close) | Crear la skill `protocol-close` | Implementada | Alta | No bloqueante |
| [T-008](#t-008---crear-el-agente-session-closer) | Crear el agente `session-closer` | Implementada | Alta | No bloqueante |
| [T-009](#t-009---crear-la-skill-protocol-start) | Crear la skill `protocol-start` | Implementada | Alta | No bloqueante |
| [T-010](#t-010---incorporar-al-arranque-la-lectura-del-tablero-del-auditor) | Incorporar al arranque la lectura del tablero del auditor | No implementada | Media | No bloqueante |
| [T-011](#t-011---crear-el-agente-session-starter) | Crear el agente `session-starter` | Implementada | Alta | No bloqueante |
| [T-012](#t-012---anadir-al-cierre-el-informe-para-la-auditoria) | Anadir al cierre el informe para la auditoria | Implementada | Alta | No bloqueante |

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Codigo | `T-XXX`, correlativo, no se reutiliza |
| Estado | `Implementada` / `No implementada` / `Cancelada` / `Suspendida` |
| Importancia | `Alta` / `Media` / `Baja` |
| Urgencia | `Bloqueante` / `No bloqueante` |
| Origen | `usuario` / `executor` / `auditor` |

Regla: una tarea con origen `auditor` solo pasa a ejecutarse despues de que `executor`
evalue la recomendacion y la considere correcta.

---

## Tareas

### T-001 - Crear los archivos base de `_persistence/`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | Bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Crear los siete archivos de persistencia del proyecto: `progress.md`, `tasks.md`,
`lessons.md`, `decisions.md`, `constraints.md`, `assumptions.md`, `debt_tec.md`.

---

### T-002 - Crear `CLAUDE.md` con las reglas executor/auditor
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | Bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Registrar la identidad de `executor`, el rol y la ruta de la terminal `auditor`, y la regla
de evaluacion previa de lo entregado por el auditor.

---

### T-003 - Estructurar los archivos de persistencia (indice, codigos y estados)
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | Bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Anadir indice de busqueda rapida a todos los archivos, definir el rol de cada uno y aplicar
codificacion `T/D/C/A/L/DT` con estado, importancia y urgencia en `tasks.md` y `debt_tec.md`.

---

### T-004 - Recibir el alcance y objetivo del proyecto
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Alta |
| Urgencia | Bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | - |

Sin el alcance no es posible cerrar `000_preproject` ni tomar decisiones tecnicas.
Relacionada con el supuesto A-003.

---

### T-005 - Definir el canal de entrega de la auditoria
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | - |

Establecer como llegan a `executor` los hallazgos de `auditor`: pegados por el usuario,
en un archivo acordado, o leyendo la carpeta del auditor. Relacionada con el supuesto A-001.

---

### T-006 - Inicializar el repositorio git y enlazarlo con GitHub
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | Bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Repositorio inicializado en la rama `main` y enlazado al remoto
`https://github.com/jdrodriguez1000/AIzar_APP.git`. Incluye `.gitignore` con las exclusiones de
secretos. Era bloqueante porque el protocolo de cierre toma su evidencia de `git`.

---

### T-007 - Crear la skill `protocol-close`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Skill de cierre de sesion en `.claude/skills/protocol-close/SKILL.md`, adaptada a la estructura
de `_persistence/` de este proyecto: sus codigos, sus cuatro estados, y sus campos de importancia
y urgencia. Sin dependencia de `tools/mkindex.py` (ver D-006). La skill quedo despues como de uso
exclusivo del agente `session-closer` (ver D-008 y T-008).

---

### T-008 - Crear el agente `session-closer`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Agente en `.claude/agents/session-closer.md`, modelo `sonnet`, unico autorizado a invocar la
skill `protocol-close`. Se lanza siempre en frio —nunca como `fork`— para que no herede la
conversacion de la jornada. Ver D-008 y D-009.

---

### T-009 - Crear la skill `protocol-start`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Protocolo de inicio en `.claude/skills/protocol-start/SKILL.md`, de solo lectura y adaptado a
nuestra estructura: indices por ancla, nuestros cuatro estados, y las siguientes tareas ordenadas
por urgencia e importancia. Sus `grep` se verificaron contra los archivos reales. Sin el paso del
auditor (ver D-011 y T-010).

---

### T-010 - Incorporar al arranque la lectura del tablero del auditor
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | - |

Cuando T-005 defina por que canal llegan los hallazgos de `auditor`, anadir a `protocol-start` el
paso que los lee y los compara con `_persistence/tasks.md`, reportando el desfase sin corregirlo.
Depende de T-005. Ver D-011.

---

### T-011 - Crear el agente `session-starter`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Agente en `.claude/agents/session-starter.md`, modelo `haiku`, unico autorizado a invocar la skill
`protocol-start`. De solo lectura, con lista blanca y negra explicita de comandos `Bash`. Ver
D-012. `CLAUDE.md` gana la seccion «Inicio de sesion».

---

### T-012 - Anadir al cierre el informe para la auditoria
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Nuevo Paso 6b en `protocol-close`: escribe `_audit/S-XXX.md` completo antes del `git add`, con la
seccion obligatoria «Que pedimos auditar». El reporte de pantalla gana un bloque con la version
corta. Propagado al agente `session-closer` y a las tablas de actores de ambos protocolos, y
anunciado en `CLAUDE.md`. Ver D-016.
