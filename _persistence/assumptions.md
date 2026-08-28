# assumptions.md

> Registro de los **supuestos vigentes**: lo que se da por cierto sin confirmacion explicita.
> Cada supuesto tiene codigo `A-XXX`. Al confirmarse pasa a `constraints.md` o `decisions.md`;
> al refutarse se marca como refutado.

---

## Indice

| Codigo | Supuesto | Fecha | Estado |
|---|---|---|---|
| [A-001](#a-001---sincronizacion-via-archivos-de-persistencia) | Sincronizacion via archivos de persistencia | 2026-08-28 | Abierto |
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

### A-001 - Sincronizacion via archivos de persistencia
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Estado | Abierto |
| Tarea relacionada | T-005 |

- **Supuesto:** `auditor` lee el contenido de este proyecto (incluido `_persistence/`) y entrega
  sus hallazgos por un medio que `executor` puede consultar o que el usuario transmite.
- **Riesgo si es falso:** los ciclos de auditoria no se cierran y las recomendaciones se pierden.
- **Como validarlo:** confirmar con el usuario el canal exacto de entrega de la auditoria.

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
