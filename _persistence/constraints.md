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

- **Restriccion:** `executor` opera en
  `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_App`;
  `auditor` opera en
  `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_Auditor`.
- **Implicacion:** `executor` no modifica archivos dentro del directorio del auditor.

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
