# debt_tec.md

> Registro de la **deuda tecnica** del proyecto: atajos conscientes, soluciones provisionales
> y pendientes de calidad. Cada item tiene codigo `DT-XXX`, estado, importancia y urgencia.
> La deuda se registra en el momento en que se contrae.

---

## Indice

| Codigo | Deuda tecnica | Estado | Confirmacion | Importancia | Urgencia |
|---|---|---|---|---|---|
| [DT-001](#dt-001---duplicidad-de-datos-entre-contractmd-y-projectmd) | Duplicidad de datos entre `contract.md` y `PROJECT.md` | No implementada | Confirmada | Media | No bloqueante |
| [DT-002](#dt-002---_methodology-mezcla-contenido-agnostico-y-propio-en-phases) | `_methodology/` mezcla contenido agnostico y propio en `phases/` | No implementada | Confirmada | Baja | No bloqueante |
| [DT-003](#dt-003---_global-no-tiene-gitignore-propio-ni-esta-declarada-en-projectmd) | `_global/` no tiene `.gitignore` propio ni esta declarada en `PROJECT.md` | Implementada | Confirmada | Baja | No bloqueante |

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Codigo | `DT-XXX`, correlativo, no se reutiliza |
| Estado | `Implementada` / `No implementada` / `Cancelada` / `Suspendida` |
| Importancia | `Alta` / `Media` / `Baja` |
| Urgencia | `Bloqueante` / `No bloqueante` |
| Origen | `usuario` / `executor` / `auditor` |
| Confirmacion | `Confirmada` / `Propuesta (pendiente de <quien>)` |

`Implementada` = la deuda ya fue pagada (corregida). `No implementada` = sigue pendiente de pago.

🚨 **`Confirmacion` y `Estado` son ejes distintos, y por eso son dos campos.** `Estado` dice si la
deuda **se pago**; `Confirmacion` dice si **es deuda**. Una entrada puede estar confirmada y sin
pagar —lo normal— pero tambien propuesta y sin confirmar: alguien la detecto y nadie ha dicho
todavia que el atajo fuera un atajo.

🚨 **`Propuesta` lleva dueño dentro del valor, siempre.** No existe `Propuesta` a secas: quien
confirma va escrito (`Propuesta (pendiente del usuario)`), porque una propuesta sin dueño no espera
—se queda propuesta para siempre—. Si no sabes quien confirma, entonces lo que falta no es la
confirmacion: es saber de quien es la decision, y eso es una `T-XXX`.

⚠️ **El caracter provisional va en el indice, no solo en el detalle.** El ojo entra por la tabla de
arriba; una entrada `Propuesta` que en el indice se ve igual que una confirmada es, en la practica,
una confirmada (hallazgo `F-014`, T-041). Antes de este campo el matiz vivia metido dentro de
`Origen`, un campo cuya convencion no lo admitia.

---

## Deuda registrada

<!--
Plantilla:

### DT-XXX - Titulo
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Confirmacion | |
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
| Confirmacion | Confirmada (2026-08-30, por el propio auditor en `R-005` §5.2) |
| Importancia | Media |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-28 |

- **Que se hizo:** al adoptar `contract.md` (D-023) se detecto que sus secciones 1 y 8 repiten
  datos que ya viven en `PROJECT.md` — nombre, rutas, rama, remoto, carpetas, codigos. Se registro
  la duplicidad y se dejo sin resolver.
- **Por que:** `contract.md` es del repositorio del auditor, de solo lectura para nosotros
  (C-002); resolverlo exige acuerdo entre las dos terminales, no una edicion unilateral.
- **Costo de no pagarla:** dos copias de la misma realidad en repositorios distintos pueden
  divergir sin que nada lo señale — el mismo riesgo que D-021 existia para evitar dentro de este
  repositorio.
- **Como pagarla:** ⚠️ **reescrito el 2026-08-30 (D-043).** La primera de las dos vias que se
  proponian aqui —«acordar con el auditor que `contract.md` cite `PROJECT.md` en vez de repetir sus
  valores»— fue **evaluada y rechazada por el auditor** en `R-005` §5.2, y el rechazo se acepto: haria
  que un contrato bilateral colgase de un archivo que solo una de las dos partes controla y puede
  cambiar sin avisar, y obligaria a leer el repositorio del otro para resolverlo. Queda **solo la
  segunda via**: aceptar la duplicacion como deliberada —cada lado necesita las reglas comunes a
  mano— y construir la deteccion de divergencia. Esa deteccion es el hallazgo `F-013`, y su trabajo
  concreto es **T-040**.
- **Disparador:** ya disparada. Se paga cuando T-040 este implementada; lo que quede despues de
  T-040 no es esta deuda, sino la parte bilateral que decide el usuario con la sesion principal del
  auditor (D-042).

---

### DT-002 - `_methodology/` mezcla contenido agnostico y propio en `phases/`
| Campo | Valor |
|---|---|
| Estado | No implementada |
| Confirmacion | Confirmada (2026-08-30, por el propio auditor en `R-005` §5.1) |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
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
- **Disparador:** ⚠️ **anadido el 2026-08-30 (D-044).** Se paga **al cerrar T-004 y antes de
  escribir la primera fase en `_methodology/phases/`**. Antes de ese momento la decision seria la
  especulacion que D-027 prohibe, y despues seria tarde: la regla se habria fijado por el primer
  archivo escrito en vez de por una decision. El auditor lo confirma en `R-005` §5.1: el parche es
  aceptable mientras nada obligue a decidir, y hoy nada obliga.

---

### DT-003 - `_global/` no tiene `.gitignore` propio ni esta declarada en `PROJECT.md`
| Campo | Valor |
|---|---|
| Estado | **Implementada** |
| Confirmacion | Confirmada (2026-08-30, por el usuario) |
| Importancia | Baja |
| Urgencia | No bloqueante |
| Etapa | 000_preproject |
| Origen | executor |
| Fecha | 2026-08-28 |
| Pagada | 2026-08-30 (S-007) |

- **Que se hizo:** en esta sesion se incorporo `_global/` al repositorio (`guide.md`,
  `changelog.md`, `sources/GUIDE.md`), analizada entera y ajustada en cuatro decisiones (D-028,
  D-029, D-030 y la version 1 registrada). Se creo y edito la carpeta, pero **no se toco ni
  `PROJECT.md` ni `.gitignore`**: `PROJECT.md` §«Carpetas propias» sigue listando solo
  `_methodology/`, `_product/`, `_persistence/`, `_audit/` y `temporal/`, y `_global/` no aparece
  en ninguna linea del `.gitignore` actual.
- **Por que:** la sesion se dedico integramente al contenido de la guia (los nueve puntos del
  analisis); el registro de la carpeta en si misma no se abordo.
- **Costo de no pagarla:** `_global/` es una carpeta de primer nivel real en el repositorio, con
  reglas propias (D-029: `sources/` es de solo lectura, igual que `_methodology/sources/`) que hoy
  solo constan en `_persistence/constraints.md` y `decisions.md`, no en el registro estable de
  carpetas. Quien lea solo `PROJECT.md` no sabe que `_global/` existe ni que es.
- **Como pagarla:** anadir una fila a la tabla «Carpetas propias» de `PROJECT.md` describiendo
  `_global/` (recetario transversal, agnostico, se copia a otros proyectos) y confirmar si hace
  falta alguna exclusion especifica en `.gitignore` para esa carpeta (hoy ninguna receta lo exige,
  pero no se verifico explicitamente).
- **Como se pago (2026-08-30, S-007):** las dos mitades, por separado.
  1. **`PROJECT.md`** — `_global/` entra en la tabla «Carpetas propias» junto a `_methodology/`,
     con tres notas debajo: se copia y no se comparte (sello de version, D-028), `sources/GUIDE.md`
     es de solo lectura (C-005), y se versiona entera.
  2. **`.gitignore`** — se verifico y **no hace falta ninguna exclusion**: los tres archivos de la
     carpeta (`guide.md`, `changelog.md`, `sources/GUIDE.md`) estan versionados y deben estarlo,
     porque son registro del proyecto y no material en transito como `temporal/`. Esa mitad se
     cierra **por verificacion, no por edicion**: se comprobo que no habia nada que excluir, y
     queda escrito en `PROJECT.md` para que la proxima lectura no vuelva a abrir la duda.
