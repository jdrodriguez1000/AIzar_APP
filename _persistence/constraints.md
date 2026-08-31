# constraints.md

> Registro de las **limitaciones y restricciones** del proyecto: lo que obliga o impide,
> y no es negociable. Cada restriccion tiene codigo `C-XXX`.
> Lo que aun no esta confirmado no va aqui, va en `assumptions.md`.

---

## Indice

| Codigo | Restriccion | Tipo | Estado |
|---|---|---|---|
| [C-001](#c-001---separacion-de-roles-entre-terminales) | Separacion de roles entre terminales | Proceso | Vigente |
| [C-002](#c-002---rutas-de-trabajo-fijas) | Rutas de trabajo fijas | Entorno | Vigente |
| [C-003](#c-003---etapa-actual-000_preproject) | Etapa actual 000_preproject | Proceso | Vigente |
| [C-004](#c-004---entorno-de-ejecucion-windows) | Entorno de ejecucion Windows | Entorno | Vigente |
| [C-005](#c-005---las-carpetas-sources-son-registro-congelado) | Las carpetas `sources/` son registro congelado | Proceso | Vigente |

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Codigo | `C-XXX`, correlativo, no se reutiliza |
| Tipo | `Proceso` / `Tecnica` / `Negocio` / `Entorno` |
| Estado | `Vigente` / `Levantada` |

---

## Restricciones

### C-001 - Separacion de roles entre terminales
| Campo | Valor |
|---|---|
| Tipo | Proceso |
| Origen | usuario |
| Estado | Vigente |

- **Restriccion:** `auditor` no ejecuta el proyecto; unicamente audita, verifica, valida y recomienda.
- **Implicacion:** todo cambio efectivo sobre el proyecto lo realiza `executor`.

---

### C-002 - Rutas de trabajo fijas
| Campo | Valor |
|---|---|
| Tipo | Entorno |
| Origen | usuario |
| Estado | Vigente |

- **Restriccion:** cada terminal opera en **su propio repositorio, y solo en el**. Cual es cada uno
  esta en la tabla **Rutas** de `PROJECT.md` (campos «Repositorio del proyecto» y «Repositorio del
  auditor»); aqui no se repiten.
- **Implicacion:** `executor` no modifica archivos dentro del directorio del auditor.
- **Por que sin las rutas escritas** (2026-08-30, `T-036`, hallazgo `F-010` de `R-004`): las llevaba
  literales, duplicando lo que `D-021` acababa de centralizar en `PROJECT.md`. La restriccion **no
  las necesita para cumplir su funcion** —lo que obliga es «no escribes en el repositorio del otro»,
  y esa frase no cambia si las rutas se leen de otro sitio—. Con el duplicado, cambiar una ruta
  obligaba a acordarse de este archivo; si no se acordaba, dos sitios decian cosas distintas y habia
  que decidir cual mentia.

---

### C-003 - Etapa actual 000_preproject
| Campo | Valor |
|---|---|
| Tipo | Proceso |
| Origen | usuario |
| Estado | Vigente |

- **Restriccion:** aun no se ha comunicado el alcance ni la naturaleza del proyecto.
- **Implicacion:** no se toman decisiones tecnicas de arquitectura, stack ni producto todavia.

---

### C-004 - Entorno de ejecucion Windows
| Campo | Valor |
|---|---|
| Tipo | Entorno |
| Origen | verificado en sesion |
| Estado | Vigente |

- **Restriccion:** sistema Windows 11; shell primario PowerShell.
- **Implicacion:** scripts, rutas y herramientas deben ser compatibles con Windows.

---

### C-005 - Las carpetas `sources/` son registro congelado
| Campo | Valor |
|---|---|
| Tipo | Proceso |
| Origen | D-029 |
| Estado | Vigente |

- **Restriccion:** las carpetas `sources/` del repositorio contienen **fuentes congeladas** y
  **no se editan**. Son dos, y la regla es la misma para las dos:

  | Carpeta | Que guarda | Su destilado |
  |---|---|---|
  | `_global/sources/` | copia intacta de la fuente del recetario, tomada el 2026-08-28 | `_global/guide.md` |
  | `_methodology/sources/` | las fuentes de las que se destilo el canonico del metodo | `_methodology/000_method.md` |

  Si un original cambia y merece la pena, se retoma el snapshot **entero** — nunca por partes — y se
  anota la linea en el changelog que corresponda.

- **Implicacion:** una correccion que nazca leyendo una de estas fuentes **no se escribe ahi**: va a
  su destilado, que es el que manda. Editar un snapshot lo convierte en una tercera version que no es
  ni la fuente ni el destilado, y a partir de ese momento las flechas `↳ GUIDE §N` de `guide.md`
  apuntan a un texto que ya no es el que las origino.

- 🚨 **Disparador de la regla de precedencia:** `D-029` decide **quien gana** si el snapshot y el
  destilado discrepan —gana el destilado—, pero no decia **quien mira**. Como el snapshot solo se
  retoma entero, una discrepancia no se descubre por accidente: habria que comparar el manual entero
  contra el destilado. Por eso el momento de ejercerla es **este**: al retomar un snapshot se revisan
  ademas **las flechas de las recetas afectadas**, que es el unico instante en que puede haber
  discrepancia y hay alguien mirandola. (Recomendacion de `R-006` §5.1, `T-046`.)

- 📌 **Ampliada el 2026-08-31 (`T-046`, hallazgo `F-018` de `R-006`).** Antes esta restriccion
  cubria solo `_global/sources/GUIDE.md` y cerraba diciendo «misma regla que `_methodology/sources/`,
  que ya era intocable por la misma razon» — un precedente que **no existia como `C-XXX`**: vivia en
  una linea de cabecera de `_methodology/000_method.md`. El indice de restricciones, que es donde se
  mira antes de tocar algo, registraba una de las dos carpetas y no la otra. Se **descarta** crear una
  `C-006` gemela: es una sola regla, y dos filas para un mismo hecho son dos afirmaciones que un dia
  divergen.
