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
| [T-005](#t-005---definir-el-canal-de-entrega-de-la-auditoria) | Definir el canal de entrega de la auditoria | Implementada | Media | No bloqueante |
| [T-006](#t-006---inicializar-el-repositorio-git-y-enlazarlo-con-github) | Inicializar el repositorio git y enlazarlo con GitHub | Implementada | Alta | Bloqueante |
| [T-007](#t-007---crear-la-skill-protocol-close) | Crear la skill `protocol-close` | Implementada | Alta | No bloqueante |
| [T-008](#t-008---crear-el-agente-session-closer) | Crear el agente `session-closer` | Implementada | Alta | No bloqueante |
| [T-009](#t-009---crear-la-skill-protocol-start) | Crear la skill `protocol-start` | Implementada | Alta | No bloqueante |
| [T-010](#t-010---incorporar-al-arranque-la-lectura-del-tablero-del-auditor) | Incorporar al arranque la lectura del tablero del auditor | Implementada | Media | No bloqueante |
| [T-011](#t-011---crear-el-agente-session-starter) | Crear el agente `session-starter` | Implementada | Alta | No bloqueante |
| [T-012](#t-012---anadir-al-cierre-el-informe-para-la-auditoria) | Anadir al cierre el informe para la auditoria | Implementada | Alta | No bloqueante |
| [T-013](#t-013---crear-el-indice-de-auditorias-_auditindexmd) | Crear el indice de auditorias `_audit/index.md` | Implementada | Alta | No bloqueante |
| [T-014](#t-014---implementar-el-canal-de-vuelta-de-la-auditoria) | Implementar el canal de vuelta de la auditoria | Implementada | Alta | No bloqueante |
| [T-015](#t-015---escribir-en-protocol-close-las-reglas-de-la-seccion-0) | Escribir en `protocol-close` las reglas de la seccion 0 | Implementada | Alta | No bloqueante |
| [T-016](#t-016---poblar-el-inventario-de-acciones-irreversibles) | Poblar el inventario de acciones irreversibles | No implementada | Alta | No bloqueante |

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
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-28 |

Resuelta: el auditor definio el canal en `AIzar_Auditor/_review/` y `executor` lo evaluo y acepto
(D-018). A-001 queda `Confirmado`.

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
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-28 |

Implementada como **Paso 1c** de `protocol-start`: lee `../AIzar_Auditor/_review/index.md` y reporta
las auditorias nuevas y las entregadas sin acuse de recibo, sin corregir nada. Ver D-018.

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

---

### T-013 - Crear el indice de auditorias `_audit/index.md`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

Indice de informes con estado `Pendiente` / `Sin hallazgos` / `Con hallazgos`. `S-002` queda
registrado como `Pendiente`. El Paso 6b de `protocol-close` anade la fila; `protocol-start` reporta
las pendientes; `CLAUDE.md` recoge quien escribe el veredicto y por que no se puede suavizar.
Ver D-017.

---

### T-014 - Implementar el canal de vuelta de la auditoria
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-28 |

Primera tarea con `Origen: auditor`, evaluada y aceptada segun D-003. Paso 1c en `protocol-start`;
seccion 0 con tres veredictos en el informe del Paso 6b de `protocol-close`; columna `Respondida en`
y autoridad de estados en `_audit/index.md`; recepcion, registro de hallazgos y reglas de
desacuerdo en `CLAUDE.md`. Ver D-018.

---

### T-015 - Escribir en `protocol-close` las reglas de la seccion 0
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-28 |

Que exige cada veredicto para ser auditable, la prohibicion de marcar `Implementado` lo que el diff
no muestre, y que la tabla vaya completa porque un hallazgo omitido no cuenta como contestado.
Ver D-019.

---

### T-016 - Poblar el inventario de acciones irreversibles
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | - |

Listar que acciones son irreversibles en este proyecto (borrar datos, publicar, migrar, gastar, y
las propias del dominio), para que el desempate de D-018 deje de aplicarse a criterio. **Depende de
T-004:** sin alcance no se sabe que hace el proyecto ni que puede romper. Ver D-020.
