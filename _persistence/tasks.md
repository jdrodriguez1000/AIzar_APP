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
| [T-017](#t-017---extraer-los-datos-del-proyecto-a-projectmd) | Extraer los datos del proyecto a `PROJECT.md` | Implementada | Alta | No bloqueante |
| [T-018](#t-018---resolver-la-circularidad-del-criterio-6-del-gate-1) | Resolver la circularidad del criterio 6 del Gate 1 | No implementada | Media | No bloqueante |
| [T-019](#t-019---enunciar-una-sola-vez-el-principio-de-declarar-antes) | Enunciar una sola vez el principio de «declarar antes» | No implementada | Baja | No bloqueante |
| [T-020](#t-020---decidir-el-nivel-de-concrecion-de-rr-003-auditar-el-historial) | Decidir el nivel de concrecion de `RR-003` («Auditar el historial») | Implementada | Media | No bloqueante |
| [T-021](#t-021---fijar-la-regla-de-asignacion-de-los-codigos-rr-nnn) | Fijar la regla de asignacion de los codigos `RR-NNN` | Implementada | Media | No bloqueante |
| [T-022](#t-022---decidir-los-huecos-de-cobertura-del-recetario-que-entran-y-que-se-poda) | Decidir los huecos de cobertura del recetario (que entra y que se poda) | Implementada | Media | No bloqueante |
| [T-023](#t-023---revisar-rastros-de-fecha-huerfana-en-la-cabecera-de-guidemd) | Revisar rastros de fecha huerfana en la cabecera de `guide.md` | Implementada | Baja | No bloqueante |
| [T-024](#t-024---resolver-la-contradiccion-menor-del-1-de-guidemd) | Resolver la contradiccion menor del §1 de `guide.md` | Implementada | Baja | No bloqueante |
| [T-025](#t-025---juzgar-las-cuatro-candidatas-aplazadas-del-recetario) | Juzgar las cuatro candidatas aplazadas del recetario | No implementada | Media | No bloqueante |
| [T-026](#t-026---disenar-la-fase-descubrimiento-antes-de-entrar-en-ella) | Disenar la fase `Descubrimiento` antes de entrar en ella | No implementada | Alta | Bloqueante |
| [T-027](#t-027---dar-comprobacion-roja-al-anclaje-del-informe-de-auditoria-en-el-commit) | Dar comprobacion roja al anclaje del informe de auditoria en el commit | Implementada | Alta | No bloqueante |
| [T-028](#t-028---dejar-recuperable-el-enunciado-anterior-de-a-001-desde-el-propio-archivo) | Dejar recuperable el enunciado anterior de `A-001` desde el propio archivo | Implementada | Media | No bloqueante |
| [T-029](#t-029---declarar-en-claudemd-que-el-eje-reversibleirreversible-se-aplica-a-criterio) | Declarar en `CLAUDE.md` que el eje reversible/irreversible se aplica a criterio | Implementada | Alta | No bloqueante |
| [T-030](#t-030---corregir-la-referencia-de-d-020-es-t-016-no-t-015) | Corregir la referencia de D-020: es T-016, no T-015 | Implementada | Baja | No bloqueante |
| [T-031](#t-031---exigir-comando-y-salida-cruda-en-las-decisiones-que-verifican-antes-de-aceptar) | Exigir comando y salida cruda en las decisiones que verifican antes de aceptar | Implementada | Media | No bloqueante |
| [T-032](#t-032---anadir-a-projectmd-la-ruta-del-findingsmd-del-auditor) | Anadir a `PROJECT.md` la ruta del `findings.md` del auditor | Implementada | Media | No bloqueante |
| [T-033](#t-033---devolver-al-paso-1c-una-orden-ejecutable-y-declarar-una-forma-canonica-de-ruta) | Devolver al Paso 1c una orden ejecutable y declarar una forma canonica de ruta | Implementada | Alta | No bloqueante |
| [T-034](#t-034---generalizar-los-codigos-vivos-que-sobrevivieron-en-protocol-close) | Generalizar los codigos vivos que sobrevivieron en `protocol-close` | Implementada | Media | No bloqueante |
| [T-035](#t-035---corregir-en-d-021-la-enumeracion-de-archivos-y-anexar-el-control-fechado) | Corregir en `D-021` la enumeracion de archivos y anexar el control fechado | Implementada | Baja | No bloqueante |
| [T-036](#t-036---vaciar-c-002-de-rutas-literales-y-remitirlo-a-projectmd) | Vaciar `C-002` de rutas literales y remitirlo a `PROJECT.md` | Implementada | Baja | No bloqueante |
| [T-037](#t-037---escribir-el-control-de-regresion-de-d-021-con-su-patron-y-su-ambito) | Escribir el control de regresion de `D-021` con su patron y su ambito | Implementada | Media | No bloqueante |
| [T-038](#t-038---admitir-en-la-convencion-de-origen-los-valores-que-las-tareas-ya-usan) | Admitir en la convencion de `Origen` los valores que las tareas ya usan | Implementada | Media | No bloqueante |
| [T-039](#t-039---acordar-con-el-auditor-la-forma-de-entrega-del-dictamen-de-gate) | Acordar con el auditor la forma de entrega del dictamen de Gate | No implementada | Media | No bloqueante |
| [T-040](#t-040---dar-momento-y-dueno-a-la-comparacion-de-version-de-contractmd) | Dar momento y dueno a la comparacion de version de `contract.md` | Implementada | Alta | No bloqueante |
| [T-041](#t-041---separar-si-es-deuda-de-si-esta-pagada-en-debt_tecmd) | Separar «si es deuda» de «si esta pagada» en `debt_tec.md` | Implementada | Baja | No bloqueante |
| [T-042](#t-042---generalizar-el-ultimo-ejemplo-ilustrativo-con-codigo-vivo-de-protocol-start) | Generalizar el ultimo ejemplo ilustrativo con codigo vivo de `protocol-start` | Implementada | Baja | No bloqueante |
| [T-043](#t-043---poner-la-advertencia-de-no-copiar-phases-dentro-de-_methodology) | Poner la advertencia de no copiar `phases/` dentro de `_methodology/` | No implementada | Baja | No bloqueante |

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Codigo | `T-XXX`, correlativo, no se reutiliza |
| Estado | `Implementada` / `No implementada` / `Cancelada` / `Suspendida` |
| Importancia | `Alta` / `Media` / `Baja` |
| Urgencia | `Bloqueante` / `No bloqueante` |
| Origen | `VS-XXX` / `usuario` / `executor` / `auditor` / `metodo` |

**`Origen` es obligatorio y su valor sale de esta lista** (D-022). Que significa cada uno:

| Valor | La tarea nace de… |
|---|---|
| `VS-XXX` | un Vertical Slice del producto. Es el codigo concreto, no la palabra: `VS-004`, no `VS-XXX` |
| `usuario` | una peticion o una decision del usuario |
| `executor` | iniciativa propia al ejecutar |
| `auditor` | un hallazgo `F-NNN` de una auditoria |
| `metodo` | una inconsistencia del canonico `_methodology/000_method.md`, no del producto |

🔑 **`VS-XXX` es la unica forma de origen del producto.** Los otros cuatro son los origenes
**no-producto**: trabajo sobre el andamio —metodo, registro, canal, herramientas— que no cuelga de
ninguna necesidad. La distincion importa porque §47 del canonico exige que todo elemento del
producto declare a su padre; una tarea de andamio no tiene padre en el producto, y decirlo con un
valor propio es lo que impide que parezca huerfana.

🚨 **Anadir un valor nuevo es una decision, no una improvisacion.** El criterio es uno solo:
**nombra un origen de demanda que ninguno de los cinco ya cubre**. Un matiz de un origen existente
—«usuario, pero por escrito», «auditor, pero de otra terminal»— no es un valor nuevo: va en el
cuerpo de la tarea. Si el criterio se cumple, el valor entra **en esta tabla en la misma pasada** en
que se escribe la primera tarea que lo usa, con su `D-XXX`. Un valor que aparece en una tarea antes
que en esta tabla es exactamente el desfase que abrio el hallazgo `F-011` (T-038).

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

---

### T-017 - Extraer los datos del proyecto a `PROJECT.md`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | usuario |
| Fecha | 2026-08-28 |

`PROJECT.md` con identidad, rutas, remoto, carpetas y codigos. Las dos skills, los dos agentes,
`CLAUDE.md` y `_audit/index.md` dejan de llevar datos dentro y lo citan. De paso se generalizaron
las tres menciones coyunturales a T-004. Verificado: cero menciones especificas en `.claude/` y
`CLAUDE.md`. Ver D-021.

---

### T-018 - Resolver la circularidad del criterio 6 del Gate 1
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | metodo |
| Fecha | - |

El criterio **6** de §29 —«existe confianza suficiente para realizar la inversion del MVP»— es la
pregunta del Gate 1 (§28) puesta como requisito de si misma. Tiene consecuencia practica con la
**D-024**: si `auditor` dictaminara el criterio 6 estaria emitiendo el veredicto que esa decision le
prohibe. Propuesta a evaluar: declarar que los criterios **1–5 y 7 son materia del dictamen** y el
**6 es el veredicto**, propiedad de su dueño.

**No depende de ninguna fase ni del alcance:** es una inconsistencia interna del canonico. Aparcada
por D-027; se resuelve al definir la fase Prototipo, o antes si conviene.

---

### T-019 - Enunciar una sola vez el principio de «declarar antes»
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | metodo |
| Fecha | - |

El metodo repite el mismo argumento en cinco sitios sin nombrarlo: §23 (los usuarios representativos
se definen antes de la prueba), §32 (el dueño del Gate, antes de llegar), A.6 (la metrica, antes de
medir), A.11 (el alcance del prototipo, en Descubrimiento) y la regla de D-027 (la fase, antes de
entrar). Todos dicen: **lo que se define despues de ver el resultado no es una definicion.**

Enunciarlo una vez y citarlo desde los cinco, en lugar de reargumentarlo cada vez. Mejora de
redaccion del canonico, sin consecuencia sobre el diseño del producto. Aparcada por D-027.

---

### T-020 - Decidir el nivel de concrecion de `RR-003` («Auditar el historial»)
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-30 |

`_global/guide.md` se declara «procedimientos, ordenes concretas, formatos» y lo cumple en
`RR-005` (formato literal de salida), `RR-011` (plantillas pegables) y `RR-004` (forma del
comando). La subseccion «Auditar el historial» de `RR-003` rompe ese patron: describe tres
barridos sobre el historial de git **sin un solo comando**, justo donde mas falta hace uno —
nadie improvisa un barrido anclado al formato de un secreto sin ejemplo delante. La fuente
`_global/sources/GUIDE.md` §2.b tiene los comandos reales (ver D-029, que congelo esa fuente).

Decidir con el usuario si esos comandos bajan al recetario o si el agnosticismo de herramienta
justifica dejarlo en prosa — teniendo en cuenta que `RR-003` ya asume git en todo su cuerpo, asi
que el agnosticismo ya esta roto en la practica. Punto 5 del analisis de nueve de la sesion S-006.

**Resuelta el 2026-08-30 (D-032):** bajan a la receta los patrones ya anclados de los tres
barridos, el porque de cada anclaje y un aviso 💻 sobre la sensibilidad a mayusculas; **no bajan
los comandos de shell**. `_global/guide.md` sube a VERSION 2 con su linea en `changelog.md`.

---

### T-021 - Fijar la regla de asignacion de los codigos `RR-NNN`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-30 |

`_global/guide.md` no dice si los codigos `RR-NNN` son estables. Si un proyecto poda `RR-005` y
renumera lo que sigue, su `RR-007` deja de ser el `RR-007` de los demas proyectos, y la propia
instruccion del indice de la guia (`grep -n "RR-007" guide.md`) se vuelve una trampa: el mismo
codigo apunta a recetas distintas segun la copia.

Falta anadir una linea explicita en `guide.md`: los codigos son globales, nunca se reasignan,
nunca se renumeran, y un hueco (`RR-005` ausente) es informacion, no un error a corregir. Encaja
con la doctrina de trazabilidad de `CLAUDE.md` (cada codigo es estable una vez asignado). Punto 6
del analisis de nueve de la sesion S-006.

**Resuelta el 2026-08-30 (D-033):** §1 de `guide.md` gana la subseccion «Los codigos son
estables, y un hueco es informacion». Los `RR-NNN` los asigna solo la global, no se renumeran ni
se reutilizan, y un hueco es informacion. Se cerro ademas el hueco que la tarea no cubria —si una
copia puede **crear** un codigo nuevo: no puede, y se fijaron sus tres destinos. `guide.md` sube a
VERSION 3.

---

### T-022 - Decidir los huecos de cobertura del recetario (que entra y que se poda)
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-30 |

Para servir a «todo proyecto de desarrollo de software», `_global/guide.md` (834 lineas) tiene
huecos de cobertura del **como** transversal: convencion de commits y ramas, como se revierte
algo ya publicado, como entra una dependencia nueva, copias de seguridad antes de una migracion,
que corre en CI.

**La tarea NO es anadir esas recetas sin mas.** La propia guia avisa de que su enemigo es su
tamano — «si deja de leerse el indice de un vistazo, se poda antes de anadir» — y ya esta en 834
lineas. La tarea es **decidir con el usuario que entra y que se poda a cambio**, receta por
receta, no acumular. Punto 7 del analisis de nueve de la sesion S-006.

**Resuelta el 2026-08-30 (D-034):** entra **una sola receta** —`RR-013`, «Como se deshace algo ya
publicado»— y se escribe en §1 el criterio de admision que faltaba («Que merece ser una receta»:
transversal, falla en silencio, hay procedimiento, no esta ya dicho). **No se poda nada:** el
presupuesto es el indice, no el numero de recetas. Las otras cuatro candidatas se aplazan a
**T-025**, que depende de T-004. `guide.md` sube a VERSION 4.

---

### T-023 - Revisar rastros de fecha huerfana en la cabecera de `guide.md`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-30 |

La cabecera de `_global/guide.md` sustituyo «Ultima revision» por el sello `VERSION 1` mas
`_global/changelog.md` (D-028). Ese cambio de mecanismo puede haber dejado algun rastro suelto de
fecha de revision que ya no aplica bajo el esquema nuevo. Falta una revision especifica —no se
hizo en la sesion S-006, solo se aplico el cambio de fondo— para confirmar que no quedo ningun
resto huerfano. Punto 8 del analisis de nueve de la sesion S-006.

**Resuelta el 2026-08-30 (D-035):** se encontraron **dos** rastros. (1) La cabecera llevaba
`Creado: … · Actualizado: …` —introducido en esta misma sesion al subir a VERSION 2— duplicando lo
que ya dice la linea del `changelog.md`; queda en `**VERSION N**` a secas, con la razon escrita.
(2) La plantilla del sello de copia traia valores concretos (`versión 7` · `el 2026-08-28`) dentro
de algo que se copia verbatim; pasa a marcadores `<N>` y `<AAAA-MM-DD>`.

---

### T-024 - Resolver la contradiccion menor del §1 de `guide.md`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-30 |

El §1 de `_global/guide.md` («Cuando se usa, y como se mantiene») dice que la guia «nunca se lee
entera, y nunca de corrido». Pero el paso 3 del ritual de adaptacion —«borra lo que no aplica»—
exige exactamente una lectura completa para poder decidir que sobra. Es el unico momento en que
la guia si se lee entera, y hoy queda como una contradiccion sin resolver en vez de una excepcion
reconocida. Ajustar el §1 para que la nombre como la unica lectura completa prevista. Punto 9 del
analisis de nueve de la sesion S-006.

**Resuelta el 2026-08-30 (D-035):** §1 nombra la excepcion en vez de contradecirse — el dia que se
copia si se lee entera, es la unica lectura completa prevista y ocurre una vez por proyecto. Se
aprovecha para fijar **contra que se mide el tamano**: contra ese unico dia, no contra el uso
diario. No se ablando la frase original: diluir el principio habria quitado la contradiccion junto
con la regla.

---

### T-025 - Juzgar las cuatro candidatas aplazadas del recetario
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | - |

Cuatro huecos de cobertura de `_global/guide.md` quedaron aplazados en **D-034**, no descartados:
**convencion de commits y ramas**, **como entra una dependencia nueva**, **copias de seguridad
antes de una migracion**, y **que corre en CI**.

Se aplazaron porque son recetas sobre un stack que todavia no existe: escritas hoy describirian lo
imaginado, y habria que corregirlas cuando la guia ya se hubiera copiado. **Depende de T-004**
(alcance del proyecto): sin saber que se construye no hay con que juzgarlas.

Cuando llegue el alcance, cada una se pasa por los cuatro filtros del criterio de admision (§1 de
`guide.md`, «Que merece ser una receta»). Aviso ya anotado: la convencion de commits **suspende el
filtro 2** —falla a la vista de todos y se arregla al momento—, asi que su entrada tendria que
justificarse por otra via o descartarse.

---

### T-026 - Disenar la fase `Descubrimiento` antes de entrar en ella
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Alta |
| Urgencia | Bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | - |

**La carpeta `_methodology/phases/` no existe todavia**, y con ella no existe la definicion de
ninguna fase. `PROJECT.md` la declara como el sitio donde vive cada una, con su esqueleto fijo de
ocho secciones, y **D-027** exige que la fase N se disene al cerrar la fase N-1 — antes de entrar,
nunca desde dentro.

El problema de secuencia: **D-026 dice que al cerrarse T-004 se entra en `Descubrimiento`**. Si esa
transicion ocurre sin la definicion escrita, la fase quedaria disenada desde dentro, que es
exactamente lo que `CLAUDE.md` prohibe: «diseñada desde dentro, una fase no define lo que se exige:
describe lo que salio».

Falta escribir `_methodology/phases/001_descubrimiento.md` con las ocho secciones del esqueleto
(pregunta, entradas, salidas, proceso, agentes, flujo, criterio de cierre, y la fecha con su
`S-XXX` como prueba de que se escribio antes). Las **salidas** las fija el metodo en su §14 —
registro de necesidades `N-xxx`, actores, interesados, hipotesis a validar, y la decision de
alcance del prototipo con su justificacion escrita (A.11)—, asi que no se inventan: se aterrizan a
este proyecto.

**Depende de T-004** en el contenido, no en la forma: el esqueleto y las salidas del metodo se
pueden escribir sin alcance, pero aterrizarlas —quienes son los actores, que hipotesis— exige
saber que se construye. **Debe estar terminada antes de declarar la entrada en `Descubrimiento`.**

---

### T-027 - Dar comprobacion roja al anclaje del informe de auditoria en el commit
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-001` de `R-002`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**: el
hallazgo se sostiene, y se verifico que **persiste en `HEAD`**.

Lo observado: el Paso 6b de `protocol-close` obliga a que `_audit/S-XXX.md` entre en el mismo
commit que describe —es el ancla entera de D-016—, pero **ninguna comprobacion puede salir roja**:

- el bucle del **Paso 2b** recorre los siete archivos de `_persistence/` y **no incluye `_audit/`**
  (`.claude/skills/protocol-close/SKILL.md`, bloque del Paso 2b);
- el **Paso 7** solo mira secretos antes del `git add -A`;
- la plantilla del **Paso 8** lleva la linea **fija** `Informe de auditoria — _audit/S-XXX.md,
  incluido en el commit` (`SKILL.md:551`), que se escribe igual haya entrado el archivo o no —
  mientras su linea hermana justo encima, la de los indices, si tiene tres salidas
  (`al dia | corregidos | 🚨 SIN COMPROBAR`).

Por que importa: si el informe no entra, el reporte de pantalla **afirmara que entro**, y el
desfase solo se descubre cuando el auditor no lo encuentre, sesiones despues y sin poder
reconstruir que estado describia.

Que hacer: anclar esa linea a un comando que pueda fallar —`git diff --cached --name-only | grep -qx
"_audit/S-XXX.md"` antes del commit, o `git show --stat --name-only HEAD -- _audit/S-XXX.md`
despues— y darle las mismas tres salidas que la de los indices, con `🚨 SIN COMPROBAR` cuando el
comando no se pueda correr.

Evidencia que la cierra: un diff de `.claude/skills/protocol-close/SKILL.md` con el comando de
verificacion en el Paso 6b o el Paso 7, y la plantilla del Paso 8 con la linea de tres salidas.

**Como quedo (2026-08-30):** se anadio el **Paso 7b** a `protocol-close`, despues del `git commit` y
antes del `git push`, con `git show --stat --name-only HEAD -- _audit/S-XXX.md` y la misma consulta
para `_audit/index.md`. Se eligio comprobar **despues del commit** y no antes del `git add` porque
lo que la linea del reporte afirma es que el archivo *entro en el commit*, y eso solo el commit lo
prueba; hacerlo sobre el area de staging comprobaria una cosa distinta de la que se dice. Lleva la
tabla de tres resultados calcada del Paso 2b, con la salida rota explicita —si no entro, **commit
nuevo, nunca `--amend`**, que sigue prohibido tambien aqui— y `🚨 SIN COMPROBAR` cuando el comando
falle. La linea fija del Paso 8 se sustituyo por una de tres salidas. Propagado al agente en
`.claude/agents/session-closer.md`.

---

### T-028 - Dejar recuperable el enunciado anterior de `A-001` desde el propio archivo
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-002` de `R-002`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**: el
hallazgo se sostiene, y **persiste en `HEAD` en su parte de fondo**.

Lo observado: en S-002 `A-001` se reescribio en el sitio, de «Sincronizacion via archivos de
persistencia» a «El canal de vuelta de la auditoria», conservando codigo, fecha y estado, contra la
convencion que el propio archivo declara doce lineas mas arriba
(`_persistence/assumptions.md`: «`A-XXX`, correlativo, **no se reutiliza**»).

Que cambio desde el commit auditado (`dced7b5`): `A-001` ya esta `Confirmado` y con su nota de
cierre, asi que la mitad del problema se resolvio sola. **Lo que sigue faltando es lo esencial del
hallazgo**: el enunciado anterior no es recuperable desde `assumptions.md`. Solo consta en
`_persistence/progress.md:140` y en el `git log`. `D-011` (`decisions.md:262`) y `T-005`
(`tasks.md:129`) citan `A-001` con su significado **antiguo**, y quien las lea dentro de seis
sesiones creera estar leyendo el supuesto original.

Que hacer — de las dos vias que propone el auditor se elige la segunda, y por una razon: `A-001` ya
esta cerrado, y abrirle ahora un codigo nuevo reescribiria un historico ya asentado en vez de
documentarlo. Basta **anadir a la entrada de `A-001` una linea de reescritura**: «reescrito en
S-002; el enunciado anterior era *Sincronizacion via archivos de persistencia*, que cubria la ida y
la vuelta del ciclo».

Evidencia que la cierra: un diff de `_persistence/assumptions.md` donde el enunciado anterior de
`A-001` se lea **desde el propio archivo**, sin ir al `git log`.

**Como quedo (2026-08-30):** se anadio a la entrada de `A-001` un bloque `♻️ Reescrito en S-002`
delante del bloque de cierre, con el enunciado anterior literal —«Sincronizacion via archivos de
persistencia»—, que abarcaba **ida y vuelta**, por que se reutilizo el codigo, y el aviso de que
`D-011` y `T-005` lo citan con el significado antiguo. El estado y el codigo no se tocan: `A-001`
sigue `Confirmado`, segun D-036.

---

### T-029 - Declarar en `CLAUDE.md` que el eje reversible/irreversible se aplica a criterio
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-003` de `R-003`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**.

Lo observado: **D-020** decide que el eje reversible/irreversible se aplique «a criterio,
diciendolo explicitamente cada vez que se use, en vez de presentarlo como la lectura de una tabla
que no existe». El documento donde el eje se aplica de verdad —`CLAUDE.md:64`— lo presenta **sin esa
salvedad** y con una lista de ejemplos entre parentesis: «**irreversible** (borrar datos, publicar,
migrar, gastar) → se escala al usuario». Comprobado en `HEAD`: `git grep -l D-020` devuelve
`_audit/S-003.md`, `decisions.md`, `progress.md` y `tasks.md` — **ningun archivo operativo**.

Por que importa: el parentesis con cuatro ejemplos **se lee como la tabla que D-020 dice que no
existe**. Quien lea `CLAUDE.md` en la primera discrepancia real clasificara el asunto sin declarar
que lo hizo a criterio, que es la unica obligacion que D-020 impuso. El riesgo que el propio
informe S-003 declaro, materializable justo en el documento que se lee cuando llega el caso.

Que hacer: anadir junto a la vinieta del desempate de `CLAUDE.md` una linea que cite `D-020` y
exija que **la clasificacion se declare en la propia respuesta** mientras T-016 no cierre. Y la
misma linea en el Paso 6b de `protocol-close`, donde se redacta el rechazo, porque `session-closer`
no lee `decisions.md` entero.

Evidencia que la cierra: un diff donde `CLAUDE.md` (o el Paso 6b de `protocol-close`) cite `D-020`
y exija declarar la clasificacion al usar el eje.

---

### T-030 - Corregir la referencia de D-020: es T-016, no T-015
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-004` de `R-003`** (severidad `Baja`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**.

Lo observado: el cuerpo de `D-020` dice «Se crea **T-015** para poblar nuestro lado del inventario
cuando T-004 se cierre». `T-015` es «Escribir en `protocol-close` las reglas de la seccion 0», y
esta **`Implementada`**. La tarea del inventario es **`T-016`**, `No implementada`, que ademas cita
correctamente «Ver D-020». El error esta **solo en `decisions.md`**: el informe `_audit/S-003.md`
si dice «Consecuencia: T-016».

Por que importa: el enlace decision→tarea es lo que impide que un aplazamiento se pierda. Quien
llegue a D-020 dentro de seis sesiones para saber que queda pendiente abrira T-015, la vera
`Implementada`, y **concluira que el inventario ya se poblo**. La referencia equivocada no daña por
mentir: daña porque **resuelve la duda del lector en la direccion de no mirar**.

Que hacer: corregir la referencia a `T-016` en el cuerpo de D-020, sin tocar nada mas.

Evidencia que la cierra: `git show <hash>:_persistence/decisions.md` con `T-016` en esa linea.

---

### T-031 - Exigir comando y salida cruda en las decisiones que verifican antes de aceptar
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-005` de `R-003`** (severidad `Baja`, `REVERSIBLE`). Evaluado y **aceptado**.

Lo observado: `D-018` registra la aplicacion de D-003 asi: «**Verificado antes de aceptar:** la
carpeta `_review/` existe, es legible desde este repositorio, y su `index.md` esta creado y vacio
[…] No se acepto sobre el relato: **se comprobo**». No consta **el comando, ni su salida**, ni el
estado del repositorio ajeno sobre el que se miro. El resultado era correcto —el auditor lo
confirmo desde su lado con dos hashes y sus horas—, pero **esa comprobacion la hizo el auditor
ahora, no nuestro registro de entonces**.

Por que importa: «se comprobo» es un **veredicto**; lo que alimenta una auditoria es «**corri esto,
salio esto**». La evidencia existia, pero fuera de nuestro registro: verificarla obligo a alguien
externo a reconstruirla. Con dos lineas de salida cruda, la entrada habria sido autoverificable.

⚠️ **Esta no se corrige reescribiendo `D-018`**, y el auditor lo dice en su evidencia de cierre:
«una decision **futura** con `Origen: auditor` cuyo bloque de verificacion contenga la orden
ejecutada y su salida literal». Es una regla de forma hacia adelante, no un parche al historico —
editar `D-018` para que parezca que registro lo que no registro seria justo lo contrario de lo que
el hallazgo pide.

Que hacer: escribir la regla donde se lee —`CLAUDE.md`, junto al tratamiento de lo entregado por
`auditor`, y el Paso 6 de `protocol-close`— y **aplicarla ya** en la decision que evalua `R-003`.

Evidencia que la cierra: una decision con `Origen: auditor` cuyo bloque de verificacion contenga la
orden ejecutada y su salida literal.

---

### T-032 - Anadir a `PROJECT.md` la ruta del `findings.md` del auditor
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-006` de `R-004`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**.

Verificacion — orden ejecutada y salida cruda:

```
$ sed -n '20,35p' PROJECT.md
## Rutas

| Campo | Valor |
|---|---|
| Repositorio del proyecto | `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_App` |
| Repositorio del auditor | `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_Auditor` |
| Canal de vuelta (tablero de auditorias) | `..\AIzar_Auditor\_review\index.md` |
| Auditorias en detalle | `..\AIzar_Auditor\_review\R-XXX.md` |
| Contrato entre las dos terminales | `..\AIzar_Auditor\contract.md` |
```

Lo observado: `_audit/index.md:46` dejo de decir la ruta y pasa a decir «su estado vive en el
`findings.md` del repositorio del auditor (ruta en `PROJECT.md`)». La tabla **Rutas** de
`PROJECT.md` tiene cinco filas —proyecto, auditor, canal de vuelta, `R-XXX.md` y contrato— y
**ninguna es la del `findings.md`**. El auditor lo midio sobre `31e2ff7`, cuando eran cuatro filas;
se anadio una desde entonces (contrato) y el hueco sigue igual.

Por que importa: la indireccion cambio un dato exacto por un puntero que no resuelve, y falla en su
primer uso. Antes, quien leia esa linea sabia donde mirar; ahora abre `PROJECT.md`, no lo encuentra
y tiene que reconstruirlo. Una referencia equivocada resuelve la duda del lector en la direccion
contraria, y por eso cuesta mas que no tener referencia.

Que hacer: anadir a la tabla **Rutas** de `PROJECT.md` la fila «Estado de los hallazgos |
`..\AIzar_Auditor\_persistence\findings.md`» — en la forma canonica que fije `T-033`.

Evidencia que la cierra: un commit posterior donde, partiendo de `_audit/index.md:46`, la ruta
completa del `findings.md` sea deducible leyendo solo `PROJECT.md`.

---

### T-033 - Devolver al Paso 1c una orden ejecutable y declarar una forma canonica de ruta
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-007` de `R-004`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**. Es el mas grave de los cinco.

Verificacion — orden ejecutada y salida cruda:

```
$ sed -n '75,95p' .claude/skills/protocol-start/SKILL.md
### 1c. Y el tablero del auditor

(bloque marcado como bash)
cat "<ruta del campo «Canal de vuelta» de PROJECT.md>"
```

Lo observado: el bloque marcado como `bash` del Paso 1c paso de `cat
../AIzar_Auditor/_review/index.md` a `cat "<ruta del campo «Canal de vuelta» de PROJECT.md>"`. El
valor de ese campo es `..\AIzar_Auditor\_review\index.md`, con separadores de Windows: sustituido
literalmente en ese `cat`, **no resuelve la ruta en un shell POSIX**. `PROJECT.md` ademas ofrece dos
formas de la misma ubicacion —absoluta en «Repositorio del auditor», relativa con `\` en «Canal de
vuelta»— sin declarar cual se usa en un comando.

Por que importa: el Paso 1c es **obligatorio** en el arranque y es el unico punto donde nos
enteramos de que hay auditorias entregadas. Un paso obligatorio cuyo comando hay que interpretar
antes de correrlo se salta mas facil que uno que se copia y se pega, y el modo de fallo es
**silencioso**: el arranque no dice nada de la auditoria y nadie nota que falto.

Que hacer: dejar en el bloque una orden ejecutable tal cual y la indireccion como nota al lado; y
declarar en `PROJECT.md` **una sola forma canonica** de las rutas. Propuesta: la relativa POSIX
(`../AIzar_Auditor/_review/index.md`), porque funciona igual en Bash y en PowerShell, mientras que
`..\AIzar_Auditor\...` solo funciona en uno de los dos. **Decision pendiente de tomar** al
implementar. **Decidida asi en `D-039`**, junto con la eleccion de conservar la indireccion en el
Paso 1c en vez de escribir la ruta dentro (opcion (b) del hallazgo): la opcion (a) reintroducia el
nombre del auditor en `.claude/` y habria revertido `D-021`. El fallo silencioso que quedaba se
cubre con un bloque **obligatorio** «Tablero del auditor» en el reporte del Paso 3 — no hace el paso
mas facil, hace su omision visible. Ver tambien `L-008`.

Evidencia que la cierra: un commit posterior donde el bloque del Paso 1c contenga una orden
ejecutable tal cual, y `PROJECT.md` declare una sola forma canonica de las rutas.

---

### T-034 - Generalizar los codigos vivos que sobrevivieron en `protocol-close`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-008` de `R-004`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**, y con **mas alcance del que el hallazgo describe**.

Verificacion — orden ejecutada y salida cruda (recortada a las lineas ilustrativas):

```
$ git grep -nE "T-[0-9]{3}|D-[0-9]{3}" -- .claude
.claude/skills/protocol-close/SKILL.md:349:- **Cita siempre codigo y ruta** (`T-014`, `D-018`, `_persistence/tasks.md`). Son su unica via
.claude/skills/protocol-close/SKILL.md:373:| F-001 — <resumen> | Implementado | T-014, en este commit |
.claude/skills/protocol-close/SKILL.md:374:| F-002 — <resumen> | Aceptado — pendiente | T-015, `No implementada` |
.claude/skills/protocol-close/SKILL.md:375:| F-003 — <resumen> | No se implementa | D-018 |
--- exit: 0 ---
```

Lo observado: dos cosas, y las dos cuentan. (a) El informe `S-004` situo las tres menciones
coyunturales en `session-starter.md` y «dos veces en `protocol-start/SKILL.md`»; la tercera estaba
en **`protocol-close/SKILL.md`**, y no se generalizo: paso de citar `T-004`, `D-006` a citar
`T-014`, `D-018` — otro codigo vivo de este mismo proyecto. (b) **Ampliacion nuestra sobre el
hallazgo:** no es una linea, son **cuatro**. La plantilla de la seccion 0 (`:373-375`) usa `T-014`,
`T-015` y `D-018`, tambien codigos vivos.

Las demas apariciones del `grep` —`D-003`, `D-037`/`T-031`, `D-020`/`T-016`/`T-004`, `D-009`,
`D-018`, `D-007`/`D-008`, `DT-003`— son **citas de decisiones estructurales**, no ejemplos
ilustrativos; el propio criterio de cierre del auditor las admite y no se tocan.

Por que importa: el objetivo declarado de `D-021` —que los protocolos no lleven dentro datos
propios del proyecto— no se cumple en esas cuatro lineas. Al llevar el metodo a otro proyecto,
seguiran citando `T-014`, `T-015` y `D-018`, codigos que alli no existiran o significaran otra
cosa. Es el mismo fallo que la sesion buscaba eliminar, sobreviviendo dentro del propio cambio que
lo elimina. Y la localizacion equivocada obliga a barrer los seis archivos en vez de ir al sitio.

Que hacer: en las cuatro lineas, usar ejemplos que no dependan del proyecto (`T-NNN`, `D-NNN`, o
«el codigo y la ruta tal como aparecen en tu registro»). Y corregir la localizacion en el registro
permanente — **no editando `S-004.md`**, que ya esta entregado y por `D-018` no se reescribe, sino
en `progress.md` y en la seccion 0 del proximo informe.

Evidencia que la cierra: en un commit posterior, `git grep -nE "T-[0-9]{3}|D-[0-9]{3}" -- .claude`
devuelve solo codigos genericos o citas de decisiones estructurales, ningun ejemplo ilustrativo con
codigos vivos.

---

### T-035 - Corregir en `D-021` la enumeracion de archivos y anexar el control fechado
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-009` de `R-004`** (severidad `Baja`, `REVERSIBLE`). Evaluado y **aceptado en el
fondo, con divergencia declarada en la forma** (ver `D-038`); verificado que **persiste en `HEAD`**.

Verificacion — ordenes ejecutadas y salida cruda:

```
$ git grep -nE "AIzar|Company_TripleS|github\.com" -- .claude CLAUDE.md
--- exit: 1 ---
```

```
$ sed -n '495,530p' _persistence/decisions.md
- **Contexto:** al plantear como reutilizar este metodo en otros proyectos se midio cuanto habia
  atado a AIzar: 17 menciones —nombre, rutas absolutas, remoto— repartidas por las dos skills, los
  dos agentes y `CLAUDE.md`.
```

Lo observado: cuatro sitios del registro permanente afirman «cero menciones» y «17 menciones» sin
decir que se busco ni como se conto. Dos consecuencias comprobables: (a) el componente **remoto**
no estaba en ninguno de los archivos citados; (b) las 17 solo salen contando tambien
`_audit/index.md`, mientras `D-021` enumera **cinco** archivos («las dos skills, los dos agentes y
`CLAUDE.md`»), que suman 16 lineas.

Por que importa: «cero menciones» es una afirmacion de **ausencia**, y una afirmacion de ausencia
sin el instrumento registrado no distingue «no queda ninguna» de «no se busco bien». Esta vez se
sostiene —el auditor la reprodujo y nosotros tambien, arriba—, pero la proxima nadie podra repetir
el control sin reinventar el patron, y la descomposicion inexacta es lo que se citara dentro de
seis sesiones.

Que hacer, con la divergencia de `D-038`:
1. **Corregir la enumeracion** de cinco a seis archivos en el cuerpo de `D-021`. Es un error de
   hecho, misma clase que `T-030`, y se corrige en el sitio.
2. **NO** incrustar el comando en el cuerpo original de `D-021` como si se hubiera anotado el
   2026-08-28. Anexarlo como **nota fechada hoy**, con la orden ejecutada hoy y su salida cruda.
   `D-037` prohibe expresamente reescribir una entrada antigua para que exhiba un comando que en su
   dia no se anoto: eso convierte «falta evidencia» en «hay evidencia falsa».

Evidencia que la cierra: `D-021` con la enumeracion de seis archivos y una nota fechada que
contenga el patron exacto y su salida, de forma que un tercero pueda reproducir el conteo sin
preguntar — y sin que la nota se presente como parte del registro original.

---

### T-036 - Vaciar `C-002` de rutas literales y remitirlo a `PROJECT.md`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-010` de `R-004`** (severidad `Baja`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**.

Verificacion — ordenes ejecutadas y salida cruda:

```
$ sed -n '45,60p' _persistence/constraints.md
### C-002 - Rutas de trabajo fijas
- **Restriccion:** `executor` opera en
  `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_App`;
  `auditor` opera en
  `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_Auditor`.
- **Implicacion:** `executor` no modifica archivos dentro del directorio del auditor.
```

```
$ grep -n "C-002" _persistence/tasks.md _persistence/debt_tec.md
_persistence/debt_tec.md:68:  (C-002); resolverlo exige acuerdo entre las dos terminales, no una edicion unilateral.
--- exit: 0 ---
```

Lo observado: el informe `S-004` declaro —bien, y por iniciativa propia— que `constraints.md` quedo
fuera del barrido de `D-021`. No se creo ninguna `T-XXX` ni `DT-XXX` para eso: la unica mencion a
`C-002` fuera de `constraints.md` es una deuda **distinta** (`debt_tec.md:68`, sobre la duplicidad
de `contract.md`). La excepcion vivia solo en `_audit/S-004.md`, un documento ya entregado que por
`D-018` no se reescribe. **Esta tarea es, en si misma, el hallazgo corregido a medias**: registrarlo
donde se vuelve a leer.

Por que importa: `D-021` dice que los datos propios del proyecto viven en `PROJECT.md` y solo ahi.
Hay una excepcion conocida y ningun sitio del registro vivo la conocia: el proximo arranque lee
`progress.md` y `tasks.md`, no los informes de auditoria de hace cuatro sesiones. La lista de
pendientes no es la lista de trabajo disponible, y lo que no esta en ella no espera turno:
desaparece.

Que hacer: opcion (a) del hallazgo — `C-002` conserva **solo la restriccion** («`executor` no
modifica archivos dentro del directorio del auditor») y remite a `PROJECT.md` para las rutas. El
contenido normativo no cambia: `C-002` no necesita las rutas para cumplir su funcion. Se descarta
la opcion (b) —aceptar el duplicado como `DT-XXX`— porque el duplicado no aporta nada que
justifique mantenerlo.

Evidencia que la cierra: un `constraints.md` sin rutas literales en un commit posterior.

---

### T-037 - Escribir el control de regresion de `D-021` con su patron y su ambito
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-30 |

**Origen:** iniciativa propia a partir de la seccion 5.3 de `R-004`, donde el auditor responde a
nuestra pregunta «`D-021` no tiene ninguna prueba automatizada que impida la regresion». **No es un
hallazgo numerado**: el auditor no recomienda donde ponerlo, solo que el control exista escrito.

Lo observado: el riesgo de regresion de `D-021` **ya se materializo dentro del mismo commit que la
implemento**, en tres formas distintas — `F-006` (indireccion que apunta a nada), `F-007`
(indireccion que apunta a un formato inutilizable) y `F-008` (un dato propio que sobrevivio al
barrido). No es un riesgo futuro: es el estado actual.

Por que importa: la regresion de este tipo **es detectable sin ejecutar nada**, porque el control es
una busqueda de texto, no una prueba. Un `git grep` con el patron responde la pregunta entera en un
segundo. Lo que produjo `F-009` es justamente que cada quien reinventara el patron.

Que hacer: escribir el control con su patron y su **ambito acotado** —`.claude/`, `CLAUDE.md` y la
raiz **excluyendo `PROJECT.md`**—, y decidir donde vive (un paso de `protocol-close` junto a la
recogida de evidencia, o una comprobacion en el arranque). El ambito no es un detalle: un `grep` de
«AIzar» sobre el arbol entero dara siempre positivos legitimos —`PROJECT.md`, los informes
entregados, el registro historico— y **un control que avisa de todo termina apagado**. `PROJECT.md`
es el unico sitio donde las menciones son correctas por diseño, y el registro historico no se
reescribe.

Evidencia que la cierra: el control escrito en un archivo operativo, con su patron literal y su
ambito, y su primera ejecucion registrada con salida cruda.

---

### T-038 - Admitir en la convencion de `Origen` los valores que las tareas ya usan
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-011` de `R-005`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**.

Verificacion — ordenes ejecutadas y salida cruda:

```
$ awk '/^## Convenciones/,/^## Tareas/' _persistence/tasks.md | grep "Origen"
| Origen | `usuario` / `executor` / `auditor` |
--- exit: 0 ---
```

```
$ grep -h "^| Origen |" _persistence/tasks.md | sort | uniq -c
      1 | Origen | `usuario` / `executor` / `auditor` |
     12 | Origen | auditor |
     11 | Origen | executor |
      2 | Origen | metodo |
     12 | Origen | usuario |
--- exit: 0 ---
```

Lo observado: `D-022` declara `Origen` **obligatorio** y admite `VS-XXX` cuando la tarea nace del
producto; `PROJECT.md` lo recoge en la tabla de codigos. La tabla de Convenciones de `tasks.md` no
se toco: enumeraba tres valores, dos tareas usaban un cuarto (`metodo`) y `VS-XXX` no aparecia.

Por que importa: el argumento entero de `D-022` es que el origen convierte §47 de norma en «un campo
que esta o no esta», comprobable mirando. Esa comprobacion necesita saber **que valores son
validos**. Quien abriera `tasks.md` dentro de tres sesiones leeria la lista vieja en el sitio de mas
autoridad —la tabla de convenciones, arriba— y no la regla nueva, que vive en otro archivo.

Que se hizo: la tabla admite los cinco valores reales y cada uno se explica en una tabla propia. Se
anadio ademas lo que el hallazgo no pedia y hacia falta igual: **el criterio para admitir un valor
nuevo** —nombrar un origen de demanda que ninguno de los cinco cubra— y la regla de que el valor
entra en la tabla **en la misma pasada** que la primera tarea que lo usa. Sin criterio, la lista
vuelve a quedarse corta al siguiente caso, que es como llego este hallazgo.

Evidencia que la cierra: la tabla de Convenciones de `tasks.md` enumera `VS-XXX` y `metodo`, y
ninguna tarea usa un valor fuera de esa lista.

---

### T-039 - Acordar con el auditor la forma de entrega del dictamen de Gate
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-012` de `R-005`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**.

Verificacion — ordenes ejecutadas y salida cruda:

```
$ grep -rn "dictamen" _persistence/
_persistence/decisions.md:705:  parar; pedirle esa decision seria pedirle una opinion disfrazada de dictamen. En cambio un dictamen
_persistence/progress.md:244:    dictamen (`auditor`), veredicto (**el usuario**). Escrito en `PROJECT.md` y `CLAUDE.md`; el
_persistence/progress.md:270:  - El dictamen del Gate que exige D-024 no tiene forma definida en `contract.md` §4, que solo
_persistence/tasks.md:354:prohibe. Propuesta a evaluar: declarar que los criterios **1-5 y 7 son materia del dictamen** y el
--- exit: 0 ---
```

```
$ grep -rn "contract.md" _persistence/tasks.md _persistence/assumptions.md
_persistence/tasks.md:789:| Contrato entre las dos terminales | `..\AIzar_Auditor\contract.md` |
_persistence/tasks.md:1000:de `contract.md`). La excepcion vivia solo en `_audit/S-004.md`, un documento ya entregado que por
--- exit: 0 ---
```

Lo observado: ningun `A-XXX` ni `T-XXX` recogia el asunto. Las dos menciones de `progress.md` son
bloques historicos de sesion —el sitio que justamente deja de leerse—, y `tasks.md:354` es `T-018`,
que trata **otra cosa**: la circularidad del criterio 6 del Gate 1, no la ausencia de forma de
entrega en `contract.md` §4. Se comprobo expresamente porque era la unica candidata a cubrirlo.

Por que importa: el disparador de este riesgo —el primer Gate— esta a varias fases de distancia, que
es justo el horizonte en el que un asunto que solo vive en un informe deja de leerse. Es el argumento
de `D-027`: lo aplazado sin momento no se retoma, se olvida.

Que se hizo, y por que en dos sitios: el **supuesto** se registro como **`A-005`** —porque `D-024` se
construyo encima de algo no confirmado, y eso es literalmente lo que `assumptions.md` existe para
llevar— y **esta tarea** carga la accion y el disparador, porque la validacion **no depende de
nosotros**: el acto 2 asigna al auditor una funcion que su contrato no le da, y un contrato bilateral
no se cambia por un lado. Un supuesto sin tarea no se resuelve solo; una tarea sin supuesto pierde el
registro de que estamos construyendo sobre arena.

**Disparador:** al disenar la fase Prototipo, cuando el Gate 1 entra en el horizonte (`D-027`).
Adelantarlo seria la especulacion que `D-027` prohibe. Ver `A-005` y `D-042`.

Evidencia que la cierra: `contract.md`, en version posterior a la 1, declara una segunda forma de
entrega para el dictamen o dice explicitamente que usa la misma.

---

### T-040 - Dar momento y dueno a la comparacion de version de `contract.md`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Alta |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-013` de `R-005`** (severidad `Media`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**. Se le sube la importancia a `Alta` respecto de la severidad
del hallazgo, por lo que se dice mas abajo.

Verificacion — orden ejecutada y salida cruda:

```
$ git grep -in "contract" -- .claude
--- exit: 1 ---
```

Cero lineas: ninguna skill ni agente abria el contrato ni comparaba su version, en ningun momento
del ciclo — ni arranque, ni cierre, ni respuesta a la auditoria.

Por que importa, y por que sube a `Alta`: un detector que nadie corre no detecta. `PROJECT.md`
afirma que la version **es** el mecanismo de deteccion; si el contrato sube a 2, la fila seguira
diciendo `1` y la discrepancia solo sera visible para quien ya sospeche que existe. El desfase no
aparecera como desfase: aparecera como un reproche en un informe, con las dos partes citando reglas
distintas y ambas convencidas de tener la vigente. Es lo que `D-023` decia querer evitar. Sube a
`Alta` porque es la **unica** defensa contra la divergencia del unico documento que obliga a las dos
terminales, y porque cierra tambien el frente que abrio la respuesta del auditor a nuestra pregunta 2
(`D-043`).

Que se hizo: **Paso 1d de `protocol-start`**, con la misma indireccion que el Paso 1c —el valor se
toma del campo «Contrato entre las dos terminales» de `PROJECT.md`, no se escribe la ruta—, de forma
que `D-021` sigue cumpliendose. Dos salidas explicitas, y **las dos obligatorias en el reporte**:
callar cuando coincide dejaria el silencio ambiguo —¿coincidio, o no se miro?— y el paso no seria
auditable desde el reporte. Se declara ademas que **detectar no es resolver**: el arranque es de solo
lectura y no actualiza `PROJECT.md`, porque poner ahi un numero sin haber leido el contrato
convertiria el detector en un sello automatico y el campo dice «leida **y verificada**».

Comprobado que la orden corre y que hoy no hay desfase:

```
$ head -20 ../AIzar_Auditor/contract.md | grep -i "^> Version:"
> Version: 1 · 2026-08-28
--- exit: 0 ---
```

```
$ grep -n "Version leida y verificada" PROJECT.md
52:| Version leida y verificada | **1** (2026-08-28) |
--- exit: 0 ---
```

Control de regresion de `D-021` corrido **despues** de tocar `.claude/`, por `L-008`:

```
$ git grep -nE "AIzar|Company_TripleS|github\.com" -- .claude CLAUDE.md
--- exit: 1 ---
```

Evidencia que la cierra: un protocolo del ejecutor lee la version de `contract.md` y la contrasta
con la registrada, con dos salidas posibles.

---

### T-041 - Separar «si es deuda» de «si esta pagada» en `debt_tec.md`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**Hallazgo `F-014` de `R-005`** (severidad `Baja`, `REVERSIBLE`). Evaluado y **aceptado**;
verificado que **persiste en `HEAD`**.

Verificacion — orden ejecutada y salida cruda:

```
$ grep -n "PROPUESTA\|^| Origen |" _persistence/debt_tec.md
27:| Origen | `usuario` / `executor` / `auditor` |
61:| Origen | executor (PROPUESTA — pendiente de confirmar) |
85:| Origen | executor (PROPUESTA — pendiente de confirmar) |
109:| Origen | executor (confirmada por el usuario el 2026-08-30) |
--- exit: 0 ---
```

Lo observado: el hallazgo senala `DT-001` y `DT-002`, y la salida trae **un tercer caso que el
auditor no vio**: `DT-003` resolvio el mismo problema por la otra punta —«confirmada por el
usuario»— metiendo tambien en `Origen` un dato que ese campo no lleva. Tres entradas de tres
improvisando dentro del mismo campo es la prueba de que el eje faltaba, no de que hubiera dos
descuidos.

Por que importa: el caracter provisional estaba en el detalle y desaparecia en el indice, que es lo
que se lee. Una entrada `Propuesta` indistinguible de una confirmada es, en la practica, una
confirmada.

Que se hizo: **campo propio `Confirmacion`**, con columna en el indice, y `Origen` devuelto a sus
tres valores. Se declara que los dos ejes son distintos —`Estado` dice si **se pago**, `Confirmacion`
si **es deuda**— y que `Propuesta` **lleva dueno dentro del valor siempre**, porque una propuesta sin
dueno no espera: se queda propuesta para siempre. Las tres entradas quedan `Confirmada`: `DT-001` y
`DT-002` por el propio auditor en `R-005` §5.2 y §5.1, `DT-003` por el usuario.

Evidencia que la cierra: el `Origen` de `DT-001` y `DT-002` usa un valor de la convencion, y el
caracter provisional —cuando lo haya— es visible en el indice.

---

### T-042 - Generalizar el ultimo ejemplo ilustrativo con codigo vivo de `protocol-start`
| Campo | Valor |
|---|---|
| Estado | Implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-30 |

**No es un hallazgo del auditor.** Salio de correr el control de `T-034` despues de tocar `.claude/`
por `T-040`, que es lo que `L-008` manda hacer.

Verificacion — orden ejecutada y salida cruda (fragmento relevante):

```
$ git grep -nE "T-[0-9]{3}|D-[0-9]{3}" -- .claude
.claude/skills/protocol-start/SKILL.md:318:falta mencionarla, se dice *«`DT-003`, cancelada»* — nunca lo que decia cuando estaba abierta.
--- exit: 0 ---
```

Lo observado: `T-034` corrigio cuatro lineas con codigos vivos usados como ejemplo ilustrativo y
dejo esta. Su criterio de cierre admite «codigos genericos o citas de decisiones estructurales» y
excluye «ejemplos ilustrativos con codigos vivos» — y esto es exactamente lo segundo. Agravante: el
ejemplo era ademas **falso**, porque `DT-003` esta `Implementada`, no `Cancelada`. Al copiar el
metodo a otro proyecto, `DT-003` alli no existiria o seria otra cosa.

Que se hizo: `DT-003` pasa a `DT-NNN`. La linea del Paso 1d que cita su propio origen (`T-040`)
**no** se generaliza: es una cita de por que existe la regla, la misma forma que el Paso 1c ya usa
con «hallazgo `F-007`, T-033» y que el criterio de `T-034` admite expresamente.

Comprobado despues:

```
$ git grep -nE "DT-[0-9]{3}" -- .claude
--- exit: 1 ---
```

---

### T-043 - Poner la advertencia de no copiar `phases/` dentro de `_methodology/`
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | auditor |
| Fecha | 2026-08-30 |

**No es un hallazgo:** es la recomendacion de `R-005` §5.1, respondiendo a nuestra pregunta 1.
Evaluada y **aceptada en el fondo**, aplazada en el momento — y el motivo del aplazamiento se
explica abajo, porque no es el de siempre.

Lo observado: la exclusion de `phases/` al copiar `_methodology/` la sostiene hoy una advertencia en
prosa dentro de `PROJECT.md:73-75`. El argumento del auditor es correcto y es de los que no se
discuten: **quien copie la carpeta no leera `PROJECT.md`; leera la carpeta.** La advertencia no esta
donde ocurre la accion.

Por que **no** se implementa hoy, y no es por coste: escribir esa marca obliga a decidir donde va
—cabecera del canonico, archivo dentro de `phases/`, `README.md` en la raiz de `_methodology/`— y
cada una de las tres **presupone la regla agnostico/propio que `DT-002` declara sin decidir**. Poner
la marca ahora fijaria esa regla por la puerta de atras, que es justo lo que `DT-002` existe para
impedir y lo que `D-027` prohibe. Ademas `phases/` **no existe todavia** en el arbol, asi que la
mitad de las opciones ni siquiera son escribibles.

**Disparador:** el mismo que `DT-002` — al cerrar `T-004` y **antes** de escribir la primera fase.
En ese momento la regla ya estara decidida y la marca sera su consecuencia, no su sustituto.

Evidencia que la cierra: una marca dentro de `_methodology/` que diga que `phases/` no se copia,
puesta despues de decidir `DT-002` y coherente con esa decision.
