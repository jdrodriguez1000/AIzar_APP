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
