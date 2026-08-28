# lessons.md

> Registro de las **lecciones aprendidas** durante la ejecucion del proyecto.
> Cada leccion tiene codigo `L-XXX`.

---

## Indice

| Codigo | Leccion | Fecha | Etapa |
|---|---|---|---|
| [L-001](#l-001---progressmd-y-tasksmd-son-del-cierre-no-los-escribas-a-mano) | `progress.md` y `tasks.md` son del cierre, no los escribas a mano | 2026-08-28 | 000_preproject |
| [L-002](#l-002---un-metodo-externo-se-contrasta-contra-el-vocabulario-propio-antes-de-adoptarlo) | Un metodo externo se contrasta contra el vocabulario propio antes de adoptarlo | 2026-08-28 | 000_preproject |

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
