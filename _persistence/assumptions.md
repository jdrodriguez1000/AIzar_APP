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
| [A-004](#a-004---la-comprobacion-del-desfase-de-la-guia-tendra-dueno-cuando-se-copie) | La comprobacion del desfase de la guia tendra dueno cuando se copie | 2026-08-28 | Abierto |
| [A-005](#a-005---el-dictamen-de-un-gate-cabe-en-la-forma-de-entrega-que-contractmd-4-ya-define) | El dictamen de un Gate cabe en la forma de entrega que `contract.md` §4 ya define | 2026-08-30 | Abierto |

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

♻️ **Reescrito en S-002.** El enunciado anterior de `A-001` era **«Sincronizacion via archivos de
persistencia»**, y cubria **la ida y la vuelta** del ciclo: se suponia que tanto los informes que
salen hacia el auditor como sus observaciones de vuelta viajarian por archivos en disco. D-016
resolvio la ida —el informe entra en el commit que describe—, y el codigo se reutilizo en el sitio
para lo unico que seguia abierto, la vuelta, contra la convencion de arriba (`A-XXX` **no se
reutiliza**). Queda escrito aqui porque `D-011` y `T-005` se redactaron citando `A-001` con el
significado **antiguo**: sin esta nota, quien las lea creeria estar leyendo el supuesto original.
Corrige el hallazgo `F-002` de `R-002` (ver `T-028` y `D-036`).

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

---

### A-004 - La comprobacion del desfase de la guia tendra dueno cuando se copie
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Estado | Abierto |
| Decision relacionada | D-028 |

- **Supuesto:** el sello de version de `_global/guide.md` sirve porque **alguien comparara los dos
  numeros** —el de la global y el de la copia— con alguna regularidad. La guia deja ese momento a
  cada proyecto, «el dia que se copia».
- **Por que se registra:** hoy **no existe ninguna copia**, asi que el mecanismo no se ha ejercitado
  ni una vez. Se esta construyendo sobre algo que todavia no ha demostrado ocurrir.
- **Riesgo si es falso:** el sello se convierte en decoracion. Las copias divergen igual que sin el,
  con el agravante de que la cabecera afirma una version que nadie comprueba — y un dato que se ve
  fiable y no lo es es peor que no tener dato. Es exactamente el fallo que `RR-002` describe: lo que
  «ya se hara» se cobra solo cuando ya hay algo que perder.
- **Como validarlo** — ♻️ **reescrito el 2026-08-31 (`T-047`, recomendacion de `R-006` §5.4).**

  El enunciado anterior decia: «en la **primera copia real** de la guia a un proyecto, comprobar que
  el paso 2 del ritual fija un momento concreto para la comparacion, y que ese momento se ejecuta al
  menos una vez». **No servia, y el auditor dio el motivo exacto:** el dia en que se valida y el dia
  en que el mecanismo se estrena eran el mismo, y ese dia no tiene red. Un supuesto **cuya refutacion
  es indistinguible de su funcionamiento** no se detecta observando — el sintoma de que el sello es
  decoracion es que **no pasa nada**, y «no pasa nada» es tambien lo que se ve cuando funciona.

  Ahora se valida en dos tiempos, y el primero ya no depende de que nadie se acuerde:

  | Cuando | Que se comprueba | Si falla |
  |---|---|---|
  | en **cada copia**, al hacerla | que la tercera linea del sello —`Comprobacion del desfase`— esta escrita y nombra un sitio concreto. Es un `grep`, no un juicio | la copia esta mal sellada: se corrige antes de seguir |
  | en la **segunda copia**, no en la primera | que alguien comparo de verdad los dos numeros al menos una vez desde la primera | supuesto **refutado**: la comprobacion se lleva al arranque de sesion, el unico sitio con dueno garantizado |

  🔑 **Por que la segunda y no la primera:** hasta que no existen dos copias no hay dos numeros que
  puedan discrepar, y sin discrepancia posible no hay nada que el mecanismo pueda dejar de detectar.
  La primera copia solo demuestra que se sabe rellenar una plantilla.

  Lo que cambio en el archivo para que esto sea comprobable: `_global/guide.md` v6 anade la tercera
  linea al sello del paso 2, con la prohibicion explicita de dejarla en blanco o rellenarla con
  «cuando haga falta».

---

### A-005 - El dictamen de un Gate cabe en la forma de entrega que `contract.md` §4 ya define
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Estado | Abierto |
| Tarea relacionada | T-039 |

- **Que se supone:** **D-024** reparte el veredicto de un Gate en tres actos —evidencia
  (`executor`), dictamen (`auditor`), veredicto (**el usuario**)— y da por hecho, sin haberlo
  comprobado ni acordado, que el acto 2 tendra donde escribirse cuando llegue el momento.
- **Por que no esta confirmado:** `contract.md` §4 define **una sola** forma de entrega del auditor:
  un `R-XXX.md` que audita un informe de sesion `S-XXX.md`, en emparejamiento 1:1. Un dictamen de
  Gate no es eso — no audita una sesion, verifica siete criterios contra evidencia acumulada de
  varias— y hoy **no tiene codigo, ni plantilla, ni sitio en el indice** del auditor.
- **Sobre que se ha construido encima:** D-024 esta escrita en `PROJECT.md` y en `CLAUDE.md`, y el
  reparto de los tres actos se da ya por vigente. Si el supuesto se refuta, el acto 2 se queda sin
  soporte y **el Gate 1 no se puede emitir tal como esta escrito**.
- **Quien lo puede refutar, y por que no lo decidimos nosotros:** el acto 2 **asigna una funcion al
  auditor que su contrato no le da**. Se decidio por un lado solo y el contrato es de dos: sin la
  otra mitad, el dia del Gate 1 `executor` esperara un dictamen que ninguna skill del auditor sabe
  producir. Lo confirma el propio auditor en `R-005` §5.3, y lo eleva como asunto bilateral.
- **Como validarlo:** `contract.md` §4 declara —en una version posterior a la 1— **una segunda
  forma de entrega para el dictamen, o que el dictamen usa la misma**. Cualquiera de las dos cierra
  el supuesto; el silencio no.
- **Disparador:** **al diseñar la fase Prototipo**, que es cuando el Gate 1 entra en el horizonte
  segun D-027. Antes seria la especulacion que D-027 prohibe. El trabajo concreto es **T-039**.
- **Origen:** hallazgo `F-012` de `R-005`. El riesgo estaba detectado desde S-005 y **declarado
  explicitamente como no registrado**: vivia solo en `_audit/S-005.md`, un informe de un dia.
