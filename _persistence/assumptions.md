# assumptions.md

> Registro de los **supuestos vigentes**: lo que se da por cierto sin confirmacion explicita.
> Cada supuesto tiene codigo `A-XXX`. Al confirmarse pasa a `constraints.md` o `decisions.md`;
> al refutarse se marca como refutado.

---

## Indice

| Codigo | Supuesto | Fecha | Estado |
|---|---|---|---|
| [A-001](#a-001---el-canal-de-vuelta-de-la-auditoria) | El canal de vuelta de la auditoria | 2026-08-28 | Confirmado |
| [A-002](#a-002---un-unico-proyecto-por-directorio) | Un unico proyecto por directorio | 2026-08-28 | Abierto |
| [A-003](#a-003---el-proyecto-arranca-desde-cero) | El proyecto arranca desde cero | 2026-08-28 | Abierto |

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Codigo | `A-XXX`, correlativo, no se reutiliza |
| Estado | `Abierto` / `Confirmado` / `Refutado` |

---

## Supuestos

### A-001 - El canal de vuelta de la auditoria
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Estado | Confirmado |
| Tarea relacionada | T-005 |

✅ **Cerrado el 2026-08-28.** El auditor definio el canal de vuelta y se verifico que existe y es
legible: `AIzar_Auditor/_review/`. Lo que era supuesto pasa a D-018. Se conserva la entrada para que
se entienda que se creia mientras estuvo abierto.

- **Alcance actual:** la **ida** ya no es un supuesto. D-016 la fija: cada cierre deja el informe
  en `_audit/S-XXX.md`, dentro del commit que describe, y el auditor lo lee de ahi.
- **Supuesto que queda abierto:** que `auditor` entrega sus hallazgos por un medio que `executor`
  puede consultar, o que el usuario transmite.
- **Riesgo si es falso:** los ciclos de auditoria no se cierran — mandamos informes y las
  observaciones no vuelven, o vuelven sin quedar registradas en ningun sitio.
- **Como validarlo:** ver una auditoria real y decidir entonces el canal de vuelta. Decidirlo
  antes de ver una seria adivinar.

---

### A-002 - Un unico proyecto por directorio
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Estado | Abierto |
| Tarea relacionada | T-004 |

- **Supuesto:** `AIzar_App` contiene un solo proyecto de software, no un monorepo de varios.
- **Riesgo si es falso:** la estructura de persistencia necesitaria segmentarse por sub-proyecto.
- **Como validarlo:** al recibir el alcance del proyecto.

---

### A-003 - El proyecto arranca desde cero
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Estado | Abierto |
| Tarea relacionada | T-004 |

- **Supuesto:** no hay codigo previo que integrar; el directorio estaba vacio salvo `_persistence/`.
- **Riesgo si es falso:** decisiones de arquitectura tomadas sin considerar lo existente.
- **Como validarlo:** preguntar al usuario si existe codigo o sistema previo.
