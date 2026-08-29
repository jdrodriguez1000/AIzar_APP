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
