# PROJECT.md

> **Los datos propios de este proyecto, en un solo sitio.** Todo lo que en los protocolos, agentes
> y `CLAUDE.md` aparece como «el proyecto», «el repositorio del auditor» o «el canal de vuelta» se
> resuelve aqui.
>
> 🔑 **Es lo unico que cambia al llevar este metodo a otro proyecto.** Si un archivo necesita saber
> un nombre o una ruta, lo lee de aqui en vez de llevarlo escrito dentro.

---

## Identidad

| Campo | Valor |
|---|---|
| Nombre del proyecto | AIzar |
| Terminal ejecutora | `executor` |
| Terminal auditora | `auditor` |
| Idioma de trabajo | Espanol |

## Rutas

| Campo | Valor |
|---|---|
| Repositorio del proyecto | `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_App` |
| Repositorio del auditor | `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_Auditor` |
| Canal de vuelta (tablero de auditorias) | `../AIzar_Auditor/_review/index.md` |
| Auditorias en detalle | `../AIzar_Auditor/_review/R-XXX.md` |
| Estado de los hallazgos | `../AIzar_Auditor/_persistence/findings.md` |
| Contrato entre las dos terminales | `../AIzar_Auditor/contract.md` |

🔑 **Forma canonica: relativa y con `/`.** Las rutas relativas de esta tabla se escriben
**tal como se pegan en un comando**, con separador `/` y desde la raiz de este repositorio. Es la
unica forma valida, y por una razon concreta: funciona igual en Bash y en PowerShell, mientras que
`..\AIzar_Auditor\...` solo funciona en uno de los dos. Quien copie un valor de aqui a un bloque
`bash` obtiene una orden que corre; no una que hay que traducir antes (T-033, hallazgo `F-007`).

⚠️ **Las dos absolutas de arriba son la excepcion declarada**, no una segunda forma a
elegir: existen porque nombran la ubicacion de cada repositorio en esta maquina, no porque sirvan
para navegar entre ellos. **Para citar un archivo del auditor se usa la relativa.**

🚨 El repositorio del auditor es de **solo lectura** para nosotros (restriccion C-002).

## El contrato

`contract.md` reune lo que las dos terminales dan por supuesto la una de la otra: reparto de
autoridad, los dos canales, el acuse de recibo, los tres veredictos, el desacuerdo y los codigos
de ambos lados. Vive en el repositorio del auditor porque el lo escribio; **obliga a los dos**.

| Campo | Valor |
|---|---|
| Version leida y verificada | **1** (2026-08-28) |
| Estado | Contrastada contra `CLAUDE.md` y `_audit/index.md`: **sin contradicciones** (D-023) |

⚠️ **La version es el mecanismo de deteccion.** Si `contract.md` sube de version y esta fila
sigue diciendo `1`, es que nadie ha vuelto a leerlo. Se lee, se contrasta, y se actualiza aqui.

⚠️ **`_review/channel.md` esta superado por el contrato** (antes se llamaba `CANAL.md`). Se
conserva como registro fundacional; si los dos discrepan, manda `contract.md`.

## Etapas

Las etapas del proyecto son **las del metodo VERTICAL**, con su nombre:

    Descubrimiento → Prototipo → [Gate 1] → Product Baseline → WSLT
                   → GRTH-01… → MVP → [Gate 2] → EVOL-01…

**Con una sola excepcion, `000_preproject`**, que es la etapa actual y no existe en el metodo. Es
deliberado: en ella no se construye producto, se monta la forma de trabajar —protocolos,
persistencia, canal con la auditoria, el propio metodo—. Meterla en la nomenclatura de VERTICAL
seria fingir que el producto avanza cuando lo que avanza es el andamio.

📌 **Al cerrarse T-004** (alcance y objetivo del proyecto) **se entra en `Descubrimiento`** y
`000_preproject` no vuelve a usarse (D-026).

⚠️ **Aqui va el vocabulario, no la etapa actual.** Cual es hoy vive en
`_persistence/progress.md`, que es lo que cambia.

## Definicion de cada fase

Cada fase se define en **`_methodology/phases/NNN_<fase>.md`**, y siempre **antes de entrar en
ella**: la fase N se disena al cerrar la fase N-1 (D-027).

⚠️ **`_methodology/` contiene dos cosas distintas.** `000_method.md` y `sources/` son VERTICAL:
agnosticos, se copian tal cual a otro proyecto. `phases/` es **la aplicacion a este proyecto** —sus
agentes, sus rutas, su flujo— y no se copia.

### El esqueleto, igual para todas

| Seccion | Que contiene |
|---|---|
| 1. Pregunta | La que responde la fase, tomada de §4 del metodo |
| 2. Entradas | Que debe existir antes, y **de que salida de la fase anterior viene** |
| 3. Salidas | Que produce: codigo, forma y donde vive |
| 4. Proceso | Los pasos, en orden |
| 5. Agentes | Quien ejecuta cada paso, y **que no puede hacer** |
| 6. Flujo | El orden real y sus puntos de decision |
| 7. Criterio de cierre | **Cuando la fase esta terminada**, en terminos comprobables |
| 8. Definida el | Fecha y `S-XXX` — la prueba de que se escribio antes de entrar |

🔑 **Por que un esqueleto fijo:** ocho fases inventando cada una su estructura producen ocho
documentos que no se pueden comparar y ocho vocabularios para lo mismo. Es la misma razon por la que
los siete archivos de `_persistence/` abren todos con indice arriba y detalle debajo.

📌 **La seccion 7 no es opcional.** El metodo avisa de que GRTH puede degenerar en Waterfall
(§41.1) y de que el MVP tiende a estirarse (§48), pero no da criterio de terminacion para ninguna
fase. Exigirlo en cada definicion cubre ese hueco sin tener que parchear el canonico fase por fase.

## Los Gates del metodo

El metodo VERTICAL (`_methodology/000_method.md`) exige en su **§32** que el veredicto de un Gate
tenga **dueño declarado antes de emitirlo** y distinto de quien construyo, pero no prescribe quien
es: manda que cada proyecto lo asigne en su definicion operativa. **Esta es esa asignacion.**

| Acto | Quien | Que hace |
|---|---|---|
| 1 · Evidencia | `executor` | Construye y registra la evidencia del Gate. **Nunca emite el veredicto** |
| 2 · Dictamen | `auditor` | Verifica **criterio por criterio** si la evidencia los sostiene. **No decide** |
| 3 · Veredicto | **el usuario** | Decide `Aprobado` / `No aprobado` con el dictamen delante |

Aplica a los **dos** Gates: el **Gate 1** (§28–§32, criterios en §29) y el **Gate 2** (§51).

🔑 **Por que el usuario y no `auditor`:** un Gate decide una **inversion**, no una verdad.
`auditor` verifica si una afirmacion se sostiene contra la evidencia —eso es auditable—; si vale la
pena gastar lo que viene despues depende de quien absorbe el coste de equivocarse. Ademas
`contract.md` §2 le niega el veto explicitamente, y un Gate es un veto (D-024).

⚠️ **Esta fila se llena antes de llegar al Gate, nunca al llegar.** Es la exigencia de §32: un
veredicto cuyo dueño se decide en el momento se asigna sabiendo ya que resultado conviene.

📌 **Cada veredicto emitido se registra como una `D-XXX` en `decisions.md`**, con su campo
`Decidido por`, mas su fila en `progress.md`. No hay codigo propio para los Gates: un veredicto es
una decision, y `decisions.md` ya tiene la forma que necesita.

## Control de versiones

| Campo | Valor |
|---|---|
| Remoto | `https://github.com/jdrodriguez1000/AIzar_APP.git` |
| Rama principal | `main` |

## Carpetas propias

| Carpeta | Que es |
|---|---|
| `.claude/` | **Con que** se construye: los agentes y las skills que ejecutan los protocolos. Agnostica por `D-021` — no lleva dentro ningun dato de este proyecto |
| `_methodology/` | **Como** se construye: el metodo VERTICAL (agnostico) mas `phases/`, su aplicacion aqui |
| `_global/` | **Como** se hace lo que se hace en cualquier proyecto: el recetario transversal `guide.md`, su `changelog.md` y su fuente. Agnostico: se copia a otros proyectos |
| `_product/` | **Que** se construye: necesidades, Baseline, slices. *Se crea al entrar en Descubrimiento* |
| `_persistence/` | **Como va** el trabajo: siete archivos, indice arriba y detalle debajo |
| `_audit/` | Informes que entregamos a la auditoria, mas su `index.md` |
| `temporal/` | Area de trabajo del usuario. **Fuera del repositorio** (D-015) y fuera del registro |

⚠️ **`_global/` se copia, no se comparte.** Cada proyecto tiene su copia con **sello de version**
(D-028); lo que cambia en una no llega a las demas hasta que se recopia. La version de la copia y
que trajo cada una estan en `_global/changelog.md`.

🚨 **`_global/sources/GUIDE.md` es de solo lectura** (restriccion C-005), igual que
`_methodology/sources/`: es la fuente de la que se destilo el recetario, se conserva intacta al
lado. Lo que se edita es `guide.md`.

📌 **Se versiona entera.** No lleva exclusiones en `.gitignore`: los tres archivos —recetario,
changelog y fuente— son registro del proyecto, no material en transito.

🚨 **Esta tabla se contrasta contra el arbol en cada cierre de sesion** (Paso 2c de `protocol-close`):
las carpetas de primer nivel que existen, frente a las filas de aqui, **en las dos direcciones**. Una
carpeta sin declarar y una fila sin carpeta son el mismo defecto por sus dos caras.

⚠️ **Dos filas de esta tabla no tienen carpeta en el arbol, y es a proposito:** `_product/` esta
declarada por adelantado y se crea al entrar en Descubrimiento (`D-025`), y `temporal/` vive **fuera
del repositorio** (`D-015`). El control de arriba las senala cada vez; esa es su razon escrita, y por
eso sobreviven a la comprobacion en vez de desaparecer en una lista de excepciones que nadie revisa.

## Codigos

| Codigo | Archivo | Que es |
|---|---|---|
| `S-XXX` | `_persistence/progress.md` | sesion de trabajo |
| `H-nn` | `_persistence/progress.md` | hito |
| `T-XXX` | `_persistence/tasks.md` | tarea |
| `D-XXX` | `_persistence/decisions.md` | decision |
| `C-XXX` | `_persistence/constraints.md` | restriccion |
| `A-XXX` | `_persistence/assumptions.md` | supuesto |
| `L-XXX` | `_persistence/lessons.md` | leccion aprendida |
| `DT-XXX` | `_persistence/debt_tec.md` | deuda tecnica |
| `F-NNN` | del auditor | hallazgo de auditoria |

### Del producto (metodo VERTICAL §46)

| Codigo | Que es | Declara como padre a |
|---|---|---|
| `N-XXX` | necesidad | — (es la raiz) |
| `FT-XXX` | Feature | `N-XXX` |
| `SC-XXX` | Scenario | `FT-XXX` |
| `VS-XXX` | Vertical Slice | `SC-XXX` |
| `T-XXX` | tarea | `VS-XXX`, u otro origen si no nace del producto (D-022) |
| `TC-XXX` | Test Case | `SC-XXX` |
| `ADR-XXX` | decision arquitectonica | — (cuelga de `ARCHIT`, no de la cadena) |

🔑 **La cadena se recorre, no se guarda.** Cada elemento declara **solo a su padre**; no hay
indice de trazabilidad y no debe crearse (D-025). Hacia atras se lee encadenado; hacia adelante se
busca quien declara a un codigo como padre.

---

## Que NO va en este archivo

⚠️ **Solo lo estable.** Si algo cambia de una sesion a otra —la etapa, el avance, las tareas
abiertas, los bloqueos— **no va aqui: va en `_persistence/progress.md`**.

Un archivo de identidad que hay que actualizar cada jornada deja de ser fiable, porque nadie
recuerda mantenerlo y todos lo siguen citando.
