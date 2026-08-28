# lessons.md

> Registro de las **lecciones aprendidas** durante la ejecucion del proyecto.
> Cada leccion tiene codigo `L-XXX`.

---

## Indice

| Codigo | Leccion | Fecha | Etapa |
|---|---|---|---|
| [L-001](#l-001---progressmd-y-tasksmd-son-del-cierre-no-los-escribas-a-mano) | `progress.md` y `tasks.md` son del cierre, no los escribas a mano | 2026-08-28 | 000_preproject |

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

