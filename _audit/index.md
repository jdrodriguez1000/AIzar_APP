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
| `S-002.md` | S-002 | 2026-08-28 | Pendiente | - | - |
| `S-003.md` | S-003 | 2026-08-28 | Pendiente | - | - |
| `S-004.md` | S-004 | 2026-08-28 | Pendiente | - | - |
| `S-005.md` | S-005 | 2026-08-28 | Pendiente | - | - |
| `S-006.md` | S-006 | 2026-08-28 | Pendiente | - | - |

> `S-001` cerro antes de que existiera este mecanismo (D-016), asi que no tiene informe.
