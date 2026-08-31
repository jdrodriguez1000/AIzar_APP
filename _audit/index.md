# _audit/index.md

> Indice de los informes entregados a la terminal auditora, con su estado.
> **Es el punto de entrada del auditor:** aqui ve que le falta por auditar, sin tener que
> adivinar cual es el informe mas reciente.

---

## Para el auditor

Audita todos los informes en estado **`Pendiente`**, del mas antiguo al mas reciente. No te fijes
en cual es el ultimo: pueden acumularse varias sesiones sin auditar, y la mas reciente no es
necesariamente la unica que falta.

🔑 **Cada informe se audita contra el commit que lo contiene.** Para obtener su hash:

```bash
git log -1 -- _audit/S-XXX.md
```

Ese es el estado exacto que describe el informe. Contrasta lo que afirma con `git show <hash>`:
si algo que dice no aparece en el diff, eso es un hallazgo.

⚠️ El hash no figura en esta tabla, y no es un olvido: la fila se escribe **antes** del commit que
la contiene, asi que no puede conocer su propio hash. Se le pregunta a git.

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Estado | `Pendiente` / `Sin hallazgos` / `Con hallazgos` |
| Observaciones | ruta del `R-XXX.md` que audita este informe, o `-` |
| Respondida en | informe `S-XXX.md` donde se contesto a esa auditoria, o `-` |

- **`Pendiente`** — el informe se entrego y la auditoria no ha vuelto. Lo escribe `session-closer`
  al crear el informe.
- **`Sin hallazgos`** / **`Con hallazgos`** — lo escribe `executor` cuando recibe las observaciones.

🚨 **Actualizar esta fila ES el acuse de recibo.** Vive en nuestro repositorio, asi que el auditor
puede comprobarlo sin que nadie se lo cuente. Si pasan **dos sesiones sin acuse**, el marca su
auditoria como `Huerfana` y la re-entrega con prioridad (D-018).

🚨 **Aqui no se lleva el estado de cada hallazgo.** Un hallazgo lo cierra el auditor, verificando la
correccion sobre un commit posterior; su estado vive en el `findings.md` del repositorio del auditor (ruta en `PROJECT.md`).
Lo nuestro son las tareas, decisiones y deuda que salgan de el. **No espejamos su tablero**: dos
copias de la misma realidad se separan, y entonces hay que decidir cual miente.

🚨 **El estado registra lo que el auditor encontro, no lo que nosotros aceptamos.** Si la auditoria
señala algo y `executor` decide no implementarlo (decision D-003), la fila sigue diciendo
`Con hallazgos`. Lo contrario permitiria borrar en silencio un hallazgo incomodo, y el indice
dejaria de servir para lo unico que sirve.

---

## Informes

| Informe | Sesion | Fecha | Estado | Observaciones | Respondida en |
|---|---|---|---|---|---|
| `S-002.md` | S-002 | 2026-08-28 | Con hallazgos | [`..\AIzar_Auditor\_review\R-002.md`](../../AIzar_Auditor/_review/R-002.md) — 2 hallazgos (F-001, F-002) | S-009 |
| `S-003.md` | S-003 | 2026-08-28 | Con hallazgos | [`..\AIzar_Auditor\_review\R-003.md`](../../AIzar_Auditor/_review/R-003.md) - 3 hallazgos (F-003, F-004, F-005) | S-010 |
| `S-004.md` | S-004 | 2026-08-28 | Con hallazgos | [`..\AIzar_Auditor\_review\R-004.md`](../../AIzar_Auditor/_review/R-004.md) - 5 hallazgos (F-006, F-007, F-008, F-009, F-010) | S-012 |
| `S-005.md` | S-005 | 2026-08-28 | Con hallazgos | [`../AIzar_Auditor/_review/R-005.md`](../../AIzar_Auditor/_review/R-005.md) - 5 hallazgos (F-011, F-012, F-013, F-014, F-015) | S-013 |
| `S-006.md` | S-006 | 2026-08-28 | Con hallazgos | [`../AIzar_Auditor/_review/R-006.md`](../../AIzar_Auditor/_review/R-006.md) - 3 hallazgos (F-016, F-017, F-018) | S-014 |
| `S-007.md` | S-007 | 2026-08-30 | Con hallazgos | [`../AIzar_Auditor/_review/R-007.md`](../../AIzar_Auditor/_review/R-007.md) - 4 hallazgos (F-019, F-020, F-021, F-022) | S-015 |
| `S-008.md` | S-008 | 2026-08-30 | Pendiente | - | - |
| `S-009.md` | S-009 | 2026-08-30 | Pendiente | - | - |
| `S-010.md` | S-010 | 2026-08-30 | Pendiente | - | - |
| `S-011.md` | S-011 | 2026-08-30 | Pendiente | - | - |
| `S-012.md` | S-012 | 2026-08-30 | Pendiente | - | - |
| `S-013.md` | S-013 | 2026-08-30 | Pendiente | - | - |
| `S-014.md` | S-014 | 2026-08-31 | Pendiente | - | - |
| `S-015.md` | S-015 | 2026-08-31 | Pendiente | - | - |

> `S-001` cerro antes de que existiera este mecanismo (D-016), asi que no tiene informe.
