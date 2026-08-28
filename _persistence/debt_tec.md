# debt_tec.md

> Registro de la **deuda tecnica** del proyecto: atajos conscientes, soluciones provisionales
> y pendientes de calidad. Cada item tiene codigo `DT-XXX`, estado, importancia y urgencia.
> La deuda se registra en el momento en que se contrae.

---

## Indice

| Codigo | Deuda tecnica | Estado | Importancia | Urgencia |
|---|---|---|---|---|
| [DT-001](#dt-001---duplicidad-de-datos-entre-contractmd-y-projectmd) | Duplicidad de datos entre `contract.md` y `PROJECT.md` | No implementada | Media | No bloqueante |
| [DT-002](#dt-002---_methodology-mezcla-contenido-agnostico-y-propio-en-phases) | `_methodology/` mezcla contenido agnostico y propio en `phases/` | No implementada | Baja | No bloqueante |

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Codigo | `DT-XXX`, correlativo, no se reutiliza |
| Estado | `Implementada` / `No implementada` / `Cancelada` / `Suspendida` |
| Importancia | `Alta` / `Media` / `Baja` |
| Urgencia | `Bloqueante` / `No bloqueante` |
| Origen | `usuario` / `executor` / `auditor` |

`Implementada` = la deuda ya fue pagada (corregida). `No implementada` = sigue pendiente de pago.

---

## Deuda registrada

<!--
Plantilla:

### DT-XXX - Titulo
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | |
| Urgencia | |
| Etapa | |
| Origen | |
| Fecha | AAAA-MM-DD |

- **Que se hizo:** el atajo tomado.
- **Por que:** razon del atajo.
- **Costo de no pagarla:** consecuencia de dejarla.
- **Como pagarla:** accion concreta.
-->

### DT-001 - Duplicidad de datos entre `contract.md` y `PROJECT.md`
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor (PROPUESTA — pendiente de confirmar) |
| Fecha | 2026-08-28 |

- **Que se hizo:** al adoptar `contract.md` (D-023) se detecto que sus secciones 1 y 8 repiten
  datos que ya viven en `PROJECT.md` — nombre, rutas, rama, remoto, carpetas, codigos. Se registro
  la duplicidad y se dejo sin resolver.
- **Por que:** `contract.md` es del repositorio del auditor, de solo lectura para nosotros
  (C-002); resolverlo exige acuerdo entre las dos terminales, no una edicion unilateral.
- **Costo de no pagarla:** dos copias de la misma realidad en repositorios distintos pueden
  divergir sin que nada lo señale — el mismo riesgo que D-021 existia para evitar dentro de este
  repositorio.
- **Como pagarla:** acordar con el auditor que `contract.md` cite `PROJECT.md` en vez de repetir
  sus valores, o aceptar la duplicacion con un mecanismo de deteccion (version, como ya existe
  para el contrato completo).

---

### DT-002 - `_methodology/` mezcla contenido agnostico y propio en `phases/`
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor (PROPUESTA — pendiente de confirmar) |
| Fecha | 2026-08-28 |

- **Que se hizo:** D-027 ubica la definicion de cada fase en `_methodology/phases/NNN_<fase>.md`,
  dentro de una carpeta que `PROJECT.md` declara agnostica (`000_method.md` y `sources/` se copian
  tal cual a otro proyecto). `phases/` no se copia: es la aplicacion a este proyecto.
- **Por que:** fue un parche local para no crear una quinta carpeta de primer nivel mientras la
  regla general agnostico/propio seguia sin decidirse; el usuario aplazo esa conversacion al
  inicio de esta sesion, sin registro de la razon.
- **Costo de no pagarla:** quien copie `_methodology/` a otro proyecto tiene que saber, sin que
  ningun archivo se lo impida, que debe excluir `phases/`. Hoy solo lo dice una nota dentro de
  `PROJECT.md`.
- **Como pagarla:** decidir la regla general agnostico/propio (posiblemente separando `phases/` a
  otra carpeta de primer nivel) y aplicarla de una vez, en vez de resolverla carpeta por carpeta.
