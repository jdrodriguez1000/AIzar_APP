# lessons.md

> Registro de las **lecciones aprendidas** durante la ejecucion del proyecto.
> Cada leccion tiene codigo `L-XXX`.

---

## Indice

| Codigo | Leccion | Fecha | Etapa |
|---|---|---|---|
| [L-001](#l-001---progressmd-y-tasksmd-son-del-cierre-no-los-escribas-a-mano) | `progress.md` y `tasks.md` son del cierre, no los escribas a mano | 2026-08-28 | 000_preproject |
| [L-002](#l-002---un-metodo-externo-se-contrasta-contra-el-vocabulario-propio-antes-de-adoptarlo) | Un metodo externo se contrasta contra el vocabulario propio antes de adoptarlo | 2026-08-28 | 000_preproject |
| [L-003](#l-003---un-indice-escrito-a-mano-necesita-defensa-explicita-contra-los-generadores) | Un indice escrito a mano necesita defensa explicita contra los generadores | 2026-08-28 | 000_preproject |
| [L-004](#l-004---un-archivo-duplicado-sin-marca-hace-que-se-edite-el-equivocado) | Un archivo duplicado sin marca hace que se edite el equivocado | 2026-08-28 | 000_preproject |
| [L-005](#l-005---un-paso-obligatorio-cuyo-resultado-no-se-mira-es-una-intencion-no-una-obligacion) | Un paso obligatorio cuyo resultado no se mira es una intencion, no una obligacion | 2026-08-30 | 000_preproject |
| [L-006](#l-006---una-regla-decidida-y-no-llevada-al-archivo-operativo-no-rige-descansa-donde-nadie-la-lee-al-aplicarla) | Una regla decidida y no llevada al archivo operativo no rige: descansa donde nadie la lee al aplicarla | 2026-08-30 | 000_preproject |
| [L-007](#l-007---al-corregir-un-codigo-mal-escrito-la-salida-cruda-que-lo-cita-no-se-toca) | Al corregir un codigo mal escrito, la salida cruda que lo cita no se toca | 2026-08-30 | 000_preproject |
| [L-008](#l-008---corregir-un-hallazgo-puede-romper-la-decision-que-lo-genero-corre-el-control-despues-de-arreglar-no-solo-antes) | Corregir un hallazgo puede romper la decision que lo genero: corre el control despues de arreglar, no solo antes | 2026-08-30 | 000_preproject |

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Codigo | `L-XXX`, correlativo, no se reutiliza |
| Origen | `usuario` / `executor` / `auditor` |

Cada leccion registra: contexto, que ocurrio, leccion y como aplicarla.

---

## Lecciones

<!--
Plantilla:

### L-XXX - Titulo
| Campo | Valor |
|---|---|
| Fecha | AAAA-MM-DD |
| Etapa | |
| Origen | |

- **Contexto:** que estaba pasando.
- **Que ocurrio:** hecho observado.
- **Leccion:** que se concluye.
- **Como aplicarla:** accion concreta a futuro.
-->

### L-001 - `progress.md` y `tasks.md` son del cierre, no los escribas a mano
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Origen | executor |

- **Contexto:** durante la definicion del metodo, `executor` fue escribiendo `progress.md` y
  `tasks.md` a medida que avanzaba, incluida una entrada de sesion `S-001` creada a mano.
- **Que ocurrio:** al redactar el protocolo de inicio se vio el choque. `protocol-close` exige que
  la entrada de la jornada lleve un id **mas alto que el que habia al arrancar**; con un `S-001`
  ya escrito por `executor`, el cierre habria creado `S-002` para **la misma jornada**. Dos
  entradas para una sola sesion, y el registro mintiendo en su primer dia.
- **Leccion:** que un archivo sea editable no lo hace tuyo. `progress.md` y `tasks.md` los cierra
  `session-closer` **desde la evidencia del diff**; escribirlos por adelantado no adelanta trabajo,
  crea conflictos de id y evidencia duplicada. La reparticion de D-002 y D-008 no es burocracia:
  es lo que evita esto.
- **Como aplicarla:** `executor` puede mantener al dia las secciones de cabecera de `progress.md`
  durante la jornada, pero **no crea entradas `S-XXX` ni cierra tareas**: eso es del cierre. Lo
  suyo son los cuatro archivos del porque (D-010).

---

### L-002 - Un metodo externo se contrasta contra el vocabulario propio antes de adoptarlo
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Origen | executor |

- **Contexto:** al incorporar el metodo VERTICAL, antes de usarlo se comparo su tabla de
  identificadores (§46) contra los codigos ya en uso en `PROJECT.md` y en el `contract.md` del
  auditor.
- **Que ocurrio:** aparecieron **tres colisiones** —`F-` (Feature vs hallazgo), `S-` (Scenario vs
  sesion) y `T-` (task de una Vertical Slice vs tarea del proyecto)—, dos de ellas sobre codigos
  comprometidos en un contrato bilateral. Resolverlas costo una edicion de documento porque **no
  existia todavia ni una sola instancia escrita**. La de `T-` era la peor y la mas invisible: mismo
  prefijo, misma palabra, distinta regla.
- **Leccion:** un metodo, una libreria o un estandar que se adopta trae **su propio vocabulario**, y
  el choque no se manifiesta como un error: se manifiesta como dos cosas distintas llamadas igual.
  El coste de detectarlo es minimo el dia antes de usarlo y crece con cada referencia escrita. Lo
  mismo aplico con `contract.md`: leerlo entero y contrastarlo antes de darlo por bueno confirmo que
  no contradecia lo nuestro — se adopto **porque coincidia**, no porque viniera del auditor.
- **Como aplicarla:** antes de adoptar cualquier cosa externa que traiga codigos, prefijos, estados
  o nombres de etapa, **cruzarlos contra `PROJECT.md` y contra el contrato**. Si algo choca, cambiar
  **lo que no tiene instancias escritas ni compromiso con la otra terminal**, nunca lo que ya se cita
  desde fuera. Ver D-022 y D-023.


---

### L-003 - Un indice escrito a mano necesita defensa explicita contra los generadores

| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Origen | executor |

- **Contexto:** `_global/guide.md` abre con un indice escrito a mano, y con una nota que explica por
  que es a mano: «no lleva numeros de linea a proposito, se desplazan con la primera edicion y
  mienten sin avisar».
- **Que ocurrio:** dentro de ese mismo indice habia **un bloque autogenerado por el editor**
  —presumiblemente la extension de TOC de VS Code— incrustado justo debajo de la etiqueta «El
  recetario», que habia **borrado la lista de recetas escrita a mano** y la habia sustituido por su
  propia version: con el titulo del documento como si fuera una seccion, con las secciones 0 y 1
  duplicadas, y con «Como se adapta a un proyecto nuevo» colgando de «Anexos».
- **Por que paso, y es la parte util:** el generador no invento nada. **Anido segun la jerarquia
  real de encabezados**, y esa jerarquia estaba mal: «Como se adapta» era `##` justo despues del `#`
  de «Anexos», asi que estructuralmente *era* un anexo. El generador dijo la verdad sobre un
  documento que estaba mal escrito. Arreglar el indice sin arreglar la jerarquia lo habria dejado
  volver a romperse en el siguiente guardado.
- **Y el modo de fallo que importa:** el destrozo **no se ve al leer el archivo de corrido**. Un
  indice que anida mal parece un indice. Solo se nota cuando alguien sigue un enlace, y para
  entonces ya lleva semanas ahi.
- **Leccion:** un indice a mano dentro de un `.md` que se edita en un editor con TOC automatico **no
  se mantiene solo: se defiende**. Y la defensa tiene dos mitades, porque una sola no basta: (1) la
  **jerarquia de encabezados tiene que ser correcta**, porque un generador refleja la estructura real
  y la estructura mal hecha se lo pone facil; (2) un **comentario visible** en el propio archivo que
  diga que el indice es a mano y que apaguen el automatismo.
- **Como aplicarla:** en cualquier `.md` con indice manual —los de `_persistence/`, `PROJECT.md`,
  `_methodology/000_method.md`, `_global/guide.md`— comprobar que **ningun encabezado cuelga de un
  padre al que no pertenece**, y dejar el comentario de aviso dentro del bloque del indice. Al
  anadir una seccion, tocar el indice en la misma pasada: una seccion que no esta en el indice no
  existe, porque estos archivos no se leen de corrido. Refuerza **D-006** (indices por ancla, sin
  generador): la decision ya estaba tomada, y lo que fallo fue que **nada la hacia cumplir dentro
  del archivo**.


---

### L-004 - Un archivo duplicado sin marca hace que se edite el equivocado

| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Origen | executor |

- **Contexto:** se trabajo durante toda la sesion sobre `AIzar_App/_global/guide.md`, editandolo a
  fondo: version, sello, regla de no reescribir, `changelog.md`.
- **Que ocurrio:** al buscar el `GUIDE.md` de las flechas aparecio que **`_global/` existia dos
  veces** —una al nivel de `Proyectos_TripleS/` y otra dentro de `AIzar_App/`— con el mismo archivo
  de 642 lineas. La de dentro era una copia de la de fuera. **Se habia editado la copia, no el
  original**, y nada lo advirtio: los dos archivos se llamaban igual, pesaban igual y decian lo
  mismo.
- **La ironia util:** paso mientras se disenaba el mecanismo para evitar exactamente eso. El
  problema no era teorico ni futuro — **ya estaba en el disco antes de empezar a hablar de el**.
- **Leccion:** dos archivos identicos en sitios distintos **no se distinguen por si mismos**, y la
  intencion de «no tener en cuenta uno de los dos» **no es un estado que el disco recuerde**. El
  siguiente que abra la carpeta —o la siguiente sesion, que arranca sin memoria— tiene un 50 % de
  acertar. Decir «ese ya no vale» en una conversacion no protege nada.
- **Como aplicarla:** cuando aparezca un duplicado, **resolverlo el mismo dia**: borrarlo, o dejar
  en el que no vale una linea en la primera pantalla diciendo cual es el bueno. Es lo mismo que
  `RR-003` hace con los commits —lo que no debe estar se decide **antes**, no despues— aplicado a
  carpetas. Y antes de editar un archivo que podria estar duplicado, un `find` por nombre cuesta un
  segundo. Ver D-029.

---

### L-005 - Un paso obligatorio cuyo resultado no se mira es una intencion, no una obligacion
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Origen | auditor |

- **Contexto:** primera auditoria entregada del proyecto, `R-002` sobre `_audit/S-002.md`. Su
  hallazgo `F-001` no señala nada falso en el informe: señala que el **Paso 6b** de
  `protocol-close` —obligatorio, y ancla de toda la auditabilidad segun D-016— no tenia detras
  ninguna comprobacion que pudiera salir roja.
- **Que ocurrio:** el reporte de pantalla llevaba la linea **fija** `Informe de auditoria —
  _audit/S-XXX.md, incluido en el commit`, que se imprimia igual hubiera entrado el archivo o no.
  Un cierre que anclo el informe y uno que no **se leian identicos**.
- **Lo que lo hace una leccion y no un despiste:** la linea de justo encima, la de los indices del
  Paso 2b, **ya tenia sus tres salidas** (`al dia | corregidos | 🚨 SIN COMPROBAR`), con su tabla y
  su aviso de que «no pude comprobarlo» no es «esta bien». La regla correcta estaba escrita, a una
  linea de distancia, y no se aplico al control nuevo. **No falto el criterio: falto extenderlo.**
- **Leccion:** al añadir un paso obligatorio hay que añadir a la vez **como se sabe que se
  cumplio**, y ese como tiene que poder **fallar**. Una afirmacion en el reporte no es evidencia de
  nada: es la misma frase pase lo que pase. Y el fallo silencioso es el peor de los tres estados,
  porque el desfase solo se descubre cuando alguien de fuera va a buscar lo que deberia estar —
  aqui, sesiones despues y sin poder reconstruir que estado describia el informe perdido.
- **Como aplicarla:** cuando el protocolo gane un paso obligatorio, preguntarse **que comando lo
  desmentiria** y escribirlo junto al paso, con sus **tres** resultados —cumplido, roto, y **no
  comprobado**, que nunca se colapsa con «cumplido»—. Si no existe tal comando, decirlo en el sitio
  en vez de afirmar el cumplimiento: es lo que ya hace la seccion «Que NO se pudo contrastar» del
  auditor. Aplicado en el **Paso 7b** (T-027).
- **Y una segunda, sobre el metodo:** la auditoria encontro esto **sin ejecutar nada**, leyendo dos
  lineas contiguas del mismo archivo. La revision externa no valio por saber mas, sino por leer sin
  dar por supuesto lo que quien lo escribio ya daba por hecho.

---

### L-006 - Una regla decidida y no llevada al archivo operativo no rige: descansa donde nadie la lee al aplicarla
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Origen | auditor |

- **Contexto:** hallazgo `F-003` de `R-003`. `D-020` habia decidido que el eje
  reversible/irreversible se aplicase «a criterio, **diciendolo explicitamente cada vez que se
  use**». La decision estaba bien tomada y bien escrita.
- **Que ocurrio:** `git grep -l "D-020"` devuelve `_audit/S-003.md`, `decisions.md`, `progress.md`
  y `tasks.md` — **ningun archivo operativo**. Y `CLAUDE.md:64`, que es donde el eje se usa de
  verdad, lo presenta con un parentesis de cuatro ejemplos: «(borrar datos, publicar, migrar,
  gastar)». Ese parentesis **es** la tabla que D-020 prohibio, escrita en prosa.
- **Leccion:** una regla vive donde se **aplica**, no donde se **acordo**. `decisions.md` guarda el
  **porque** de una regla; no la ejecuta nadie. Si la regla no llega al archivo que se lee en el
  momento de usarla —`CLAUDE.md`, la skill, el agente—, en la practica **no existe**: quien actua
  no la va a encontrar, porque no va a ir a buscarla. Y peor que su ausencia es lo que suele quedar
  en su lugar: la version simplificada y anterior, que se lee como si fuera la regla vigente.
- **Como aplicarla:** al cerrar una decision que **cambia como se actua** (no las que solo
  registran un porque), preguntarse **quien la va a leer en el momento de usarla** y escribirla ahi
  tambien, citando su `D-XXX`. Un `git grep D-XXX` que solo devuelva archivos de `_persistence/` es
  la señal de que la decision se quedo en el acta. Vale para los agentes con doble motivo:
  `session-closer` **no lee `decisions.md` entero**, asi que una regla que le afecte y no este en su
  skill no le llega nunca.
- **Parentesco:** es `L-005` en el otro eje. `L-005` dice que un paso obligatorio sin comprobacion
  que pueda fallar es una intencion; esta dice que una regla sin sitio donde se lea es un acta.
  Las dos son la misma familia de error — **confundir haberlo escrito con que ocurra**— y las dos
  las encontro la revision externa leyendo lo que nosotros ya dabamos por hecho.

---

### L-007 - Al corregir un codigo mal escrito, la salida cruda que lo cita no se toca
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Origen | executor |

- **Contexto:** `T-030` (hallazgo `F-004` de `R-003`) pedia corregir una referencia equivocada en
  el cuerpo de `D-020`: decia `T-015` donde debia decir `T-016`. La correccion mas natural es un
  reemplazo global de la cadena en `decisions.md`.
- **Que ocurrio:** la cadena aparecia **dos veces** en el archivo. La segunda no era prosa nuestra:
  era la salida literal de `git grep -n "Se crea T-015"` registrada dentro del bloque de
  verificacion de `D-037` —la propia evidencia con la que se acepto el hallazgo—, con su numero de
  linea de entonces. Un reemplazo global la habria reescrito, dejando un bloque que afirma haber
  ejecutado un comando cuya salida ya no coincide con lo que ese comando devolveria. Se corrigio
  solo la linea 505, y `git diff --stat` confirmo **1 insercion, 1 borrado**.
- **Leccion:** dentro de `_persistence/` conviven dos clases de texto que se editan con reglas
  opuestas. La **prosa** describe el estado actual y se corrige cuando esta mal. La **salida cruda
  registrada** describe un momento pasado y **no se corrige nunca**: si deja de coincidir con el
  presente, eso no es un error, es exactamente su funcion. Reescribirla no arregla nada — fabrica
  una evidencia que no se produjo.
- **Como aplicarla:** antes de reemplazar una cadena en `_persistence/`, **contar sus apariciones**
  y mirar cada una. Toda la que este dentro de un bloque de codigo de verificacion queda fuera del
  cambio. Nunca un reemplazo global a ciegas en estos archivos, por trivial que parezca la
  correccion. Y el `git diff --stat` posterior debe cuadrar con el numero de lineas que se pretendia
  tocar.
- **Parentesco:** es la cara defensiva de `T-031` y `D-037`. Ahi se decidio **no reescribir `D-018`**
  para que exhibiera un comando que no se ejecuto; aqui se evita reescribir un comando que **si** se
  ejecuto. La misma regla desde los dos lados: el bloque de verificacion es historia, no estado.

---

### L-008 - Corregir un hallazgo puede romper la decision que lo genero: corre el control despues de arreglar, no solo antes
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Origen | executor |

- **Contexto:** `T-033` (hallazgo `F-007` de `R-004`) pedia que el bloque `bash` del Paso 1c
  volviera a ser una orden ejecutable. El hallazgo ofrecia dos opciones y la primera era obvia:
  escribir la ruta en el bloque, `cat ../AIzar_Auditor/_review/index.md`.
- **Que ocurrio:** se escribio esa version. Al correr acto seguido el control de `D-021`
  —`git grep -nE "AIzar|..." -- .claude CLAUDE.md`— dejo de dar cero: la correccion acababa de
  reintroducir el nombre del auditor **dentro de `.claude/`**, que es justo lo que `D-021`, decidida
  por el usuario, habia vaciado. El arreglo de un hallazgo `Media` estaba deshaciendo en silencio
  una decision del usuario. Se revirtio y se tomo la segunda opcion del hallazgo (`D-039`).
- **Leccion:** un hallazgo llega **acotado a lo que el auditor miro**, y su remedio puede chocar con
  una decision que el no tenia delante. La colision no se ve razonando sobre el remedio: se ve
  **corriendo el control de la otra decision despues de aplicarlo**. En este caso pasaron menos de
  dos minutos entre escribir la regresion y detectarla, y solo porque el control existia escrito con
  su patron.
- **Como aplicarla:** al cerrar un hallazgo, **volver a correr los controles de las decisiones que
  tocan los mismos archivos**, no solo comprobar el criterio de cierre del hallazgo. Y cuando el
  propio hallazgo ofrece varias opciones, tratarlas como lo que son: alternativas de igual validez
  para el auditor, entre las que elige quien si conoce las decisiones vigentes de este lado.
- **Parentesco:** es la justificacion practica de `T-037`. El control se escribio para detectar la
  regresion de `D-021` en sesiones futuras; su primera captura real fue **una correccion nuestra, el
  mismo dia, hecha para cerrar un hallazgo**. Tambien explica por que `D-039` documenta la ventaja
  de la opcion descartada en vez de ocultarla: la opcion (a) fallaba ruidosamente al copiar el
  metodo a otro proyecto, y eso es una perdida real que se acepto a cambio de no revertir `D-021`.
