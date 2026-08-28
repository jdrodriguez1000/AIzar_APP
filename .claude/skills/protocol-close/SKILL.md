---
name: protocol-close
description: Protocolo de cierre de sesion del proyecto AIzar. Recoge la evidencia real del trabajo (git status, git diff, git log), actualiza de forma obligatoria _persistence/progress.md y _persistence/tasks.md, propone entradas de debt_tec.md, y solo revisa —sin escribirlos— decisions.md, assumptions.md, constraints.md y lessons.md; despues deja la sesion cerrada con un commit y su push. Uso exclusivo del agente session-closer, que se lanza al terminar una jornada de trabajo o cuando el usuario pida "cerremos la sesion", "cierra la sesion", "finalicemos el trabajo", "guarda el avance", "terminamos por hoy" o algo similar.
---

# Protocolo de cierre de sesion

Este protocolo lo ejecuta **unicamente** el agente `session-closer`. Deja el proyecto en un estado
del que la proxima sesion pueda arrancar sola.

## Que es una sesion

🔑 **Una sesion es una jornada de trabajo, no un dia.** Puede ser una manana, una tarde, una
noche, o un dia completo. **Puede haber varias sesiones en la misma fecha**, y cada una tiene su
propio cierre y su propio `S-XXX`. Nunca asumas que una sesion equivale a un dia.

> 🔑 **La regla que gobierna todo el protocolo: se escribe desde la EVIDENCIA, no desde el
> relato.** No anotes «se hizo X» si X no aparece en el `git diff`.

Escribir desde lo que se recuerda de la conversacion es escribir rumores; escribir desde el
diff es escribir hechos. Si las dos cosas se contradicen, **manda el diff**.

## Los tres actores del proyecto

| Actor | Escribe | No escribe |
|---|---|---|
| **executor** (sesion de trabajo) | construye, y registra el porque en el momento | — |
| **El cierre** (este protocolo) | `progress.md`, `tasks.md`, propuestas a `debt_tec.md` | los cuatro del porque |
| **auditor** | su propio repositorio | no construye |

🚨 **Nunca escribas en `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_Auditor`.**
Ese repositorio no es nuestro (restriccion C-002). Lo que venga de la auditoria se refleja en
`_persistence/tasks.md` como tarea con `Origen: auditor`, y solo despues de que `executor` la
evalue y la considere correcta (decision D-003).

🚨 **No toques `temporal/`.** Es el area de trabajo del usuario, no parte del registro.

---

## Paso 1 — Recoger la evidencia (antes de escribir nada)

En este orden, sin saltarte ninguno:

```
git status
git diff
git diff --staged
git log --oneline -5
```

De ahi sale **que paso de verdad hoy**: que archivos nacieron, cuales cambiaron y desde que
punto se venia.

Si `git status` sale limpio y no hay nada sin commitear, **dilo y detente**: no hay sesion que
cerrar. No inventes avance para llenar el reporte.

⚠️ **Excepcion unica — el primer cierre del repositorio.** Si `git log` falla porque todavia no
existe ningun commit, no es un error: es el commit inicial. Sigue el protocolo normal; la
evidencia es entonces `git status`, que lista todo como sin seguimiento.

---

## Paso 2 — El traspaso, solo para el porque

La sesion puede dejar un traspaso corto: lo que se intento, lo que se descarto, con que se trabo
el usuario. Usalo **solo para explicar el porque** de lo que ya viste en el diff.

⚠️ **El traspaso nunca sustituye la evidencia.** Si el traspaso dice que se hizo algo y el diff
no lo muestra, manda el diff — y anotalo como discrepancia en el reporte.

Si no hay traspaso, el protocolo funciona igual, solo que con menos porque.

---

## Paso 2b — Coherencia indice ↔ detalle (antes del `git add`)

Cada archivo de `_persistence/` abre con un indice. **Los indices de este proyecto son tablas
con enlaces de ancla, no numeros de linea**: no se desfasan al editar el archivo, asi que no hay
nada que regenerar. Lo que si se rompe es otra cosa:

- una **entrada sin fila en el indice** es invisible: nadie la va a encontrar, porque nadie lee
  el archivo entero;
- una **fila de indice sin entrada** apunta al vacio.

Las dos formas de dejarlo a medias mienten igual. Esta comprobacion las detecta:

```bash
for f in tasks decisions constraints assumptions lessons debt_tec progress; do
  echo "== $f"
  diff <(grep -oE '^\| \[?[A-Z]+-[0-9]+' "_persistence/$f.md" | grep -oE '[A-Z]+-[0-9]+' | sort -u) \
       <(grep -oE '^#{3} [A-Z]+-[0-9]+'   "_persistence/$f.md" | grep -oE '[A-Z]+-[0-9]+' | sort -u)
done
```

Sin salida bajo un archivo = indice y detalle coinciden. Una linea `<` es una fila de indice sin
entrada; una linea `>` es una entrada que falta en el indice.

**Por que va aqui y no mas abajo, y son tres razones:**

- **Antes del `git add`**, porque el dano no es tener algo mal en el disco: es meterlo en el commit.
- 🔑 **Antes de escribir `tasks.md` (Paso 4)**, porque esta comprobacion **produce tareas**.
  Corriendola despues de escribir, su resultado llegaria tarde y no habria donde anotarlo.
- **Despues de la puerta del Paso 1**, porque si no hay nada que cerrar tampoco hay nada que comprobar.

**Hay tres resultados, no dos:**

| Que sale | Que significa | Que haces |
|---|---|---|
| sin diferencias en los 7 | los indices estan al dia | sigue al Paso 3 |
| diferencias | falta una fila o sobra una | **arreglalo ahora** y dilo en el reporte |
| el comando falla | **no lo comprobaste** | commit igual, y a **Sin resolver** |

🚨 **La tercera fila es la importante.** «No pude comprobarlo» no es «esta bien», y confundir las
dos cosas es como se cuela todo lo que se cuela.

⚠️ **Entre esta comprobacion y el `git add` no se edita ningun archivo de `_persistence/`
ya comprobado sin volver a correrla.** El control solo vale si en medio nadie toca lo que se comprobo.

🚨 **La linea del reporte sale siempre**, este al dia o no. Sin ella, un cierre que comprobo y uno
que no se leen identicos.

---

## Como se escriben estos archivos

Los siete archivos de `_persistence/` tienen la misma forma: **indice arriba, convenciones
despues, y el detalle debajo** en secciones con su codigo. Las convenciones de cada archivo estan
escritas dentro del propio archivo, en su seccion `## Convenciones`: leelas antes de escribir.

Los codigos de este proyecto:

| Codigo | Archivo | Que es |
|---|---|---|
| `S-XXX` | `progress.md` | sesion de trabajo |
| `H-nn` | `progress.md` | hito |
| `T-XXX` | `tasks.md` | tarea |
| `D-XXX` | `decisions.md` | decision |
| `C-XXX` | `constraints.md` | restriccion |
| `A-XXX` | `assumptions.md` | supuesto sin comprobar |
| `L-XXX` | `lessons.md` | leccion aprendida |
| `DT-XXX` | `debt_tec.md` | deuda tecnica |

> 🚨 **El indice y las entradas se actualizan juntos, en la misma pasada.** Ver Paso 2b.

Al anadir una entrada:

1. Dale el **siguiente id libre** (mira el ultimo del indice, no cuentes entradas). Los ids no se reutilizan.
2. Escribe la entrada en la seccion de detalle, con su tabla de campos.
3. Anade su fila al **indice**, con el enlace de ancla.
4. Vuelve a correr la comprobacion del Paso 2b sobre ese archivo.

Fechas absolutas (`2026-08-28`), nunca «ayer» ni «la semana pasada». En el indice, titulos cortos:
tienen que caber en una fila y decidirse sin abrir la entrada.

---

## Paso 3 — `_persistence/progress.md` (obligatorio)

Es el archivo principal: da la vision general, **no detalla tareas**. Actualizalo **siempre**, en
tres sitios:

**a) La seccion `## 1. Estado general`.** Es lo primero que se lee al abrir sesion, asi que se
sobrescribe entera: etapa, fecha, salud, avance y bloqueos activos.

**b) Las secciones `## 2. Ultimo realizado` y `## 3. Siguiente paso`.** Tambien se sobrescriben.
El siguiente paso es concreto: no «seguir con el desarrollo», sino la primera accion de manana.

**c) Una entrada nueva `S-XXX`** en `## 5. Bitacora`, mas su fila en el indice de sesiones, con:

1. **En que etapa va el proyecto.**
2. **Que quedo hecho hoy** — solo lo que esta en el diff.
3. **Cual es el siguiente paso concreto.**

Y si algun hito de `## 4. Hitos` cambio de estado, actualizalo.

### 🚨 La pregunta NO es «esta el archivo al dia?»

Es: **«tiene ESTA sesion su propia fila, con un id nuevo?»**

```bash
grep -n '^| \[S-' _persistence/progress.md | tail -1
```

🚨 **El criterio es el ID, no la fecha.** Esa fila tiene que llevar un `S-XXX` **mas alto** que el
que habia al arrancar. Si sigue el mismo id con el que empezaste, **falta la entrada** — y hay que
escribirla, diga lo que diga `Estado general`.

⚠️ **Por que el criterio no puede ser la fecha.** Puede haber **varios cierres el mismo dia**.
Comparar fechas no distingue dos tramos de la misma jornada: la ultima fila ya llevaria la fecha
de hoy siendo de otra sesion, y el control daria verde con la sesion entera sin registrar.

🔑 **Dos senales van a enganarte, y las dos se repiten:**

- **`Estado general` puede estar ya escrita**, porque `executor` la actualiza durante el dia.
  **Un archivo medio actualizado es peor que uno sin tocar: el trozo bueno avala al malo.**
- **Un arbol limpio no prueba que la entrada este escrita.** Significa «no queda trabajo», pero
  tambien puede significar «el trabajo se commiteo antes de que llegara el cierre».

---

## Paso 4 — `_persistence/tasks.md` (obligatorio)

Aqui el indice **es** el tablero: el estado de cada tarea vive en su fila, y se repite en la tabla
de campos de su entrada. **Las dos se actualizan juntas.**

**Los estados de este proyecto** (no hay otros, no inventes ninguno):

`Implementada` · `No implementada` · `Cancelada` · `Suspendida`

Y cada tarea lleva ademas **Importancia** (`Alta` / `Media` / `Baja`) y **Urgencia**
(`Bloqueante` / `No bloqueante`).

- Mueve a `Implementada` solo lo que la evidencia respalde.
- Lo que quedo a medias **sigue en `No implementada`**, y su entrada de detalle dice **en que
  punto quedo**. No existe un estado intermedio: media tarea no es una tarea hecha.
- `Cancelada` y `Suspendida` **requieren razon registrada** en la entrada. Si no tienes la razon,
  no cambies el estado: preguntalo en el reporte.
- Anade las tareas nuevas que aparecieron hoy, con su id, su estado y su importancia/urgencia.
  🚨 **Importancia y urgencia no son tuyas para decidir a ojo:** si el diff o el traspaso no las
  dejan claras, ponles `Media` / `No bloqueante` y **marcalo en el reporte como pendiente de
  confirmar**.
- Si una tarea estaba marcada `Implementada` y el diff la contradice, **desmarcala** y dilo en el reporte.

**Aqui entra tambien lo que produjo el Paso 2b**: si los indices salieron al dia, no hay nada que
anotar; si fallo la comprobacion, la tarea nueva se anade con su id. Ese es el motivo de que
aquel control vaya arriba y no abajo.

Una tarea que se entiende en una linea **se queda en el indice** y su entrada de detalle es
minima. No infles el archivo.

### 🚨 Lo unico que NO puede entrar aqui: el resultado del push

**El push no se anota en `tasks.md`, y no es un olvido: es imposible.** Para saber si el push
funciono, el commit ya tiene que existir — y `tasks.md` va dentro de ese commit. Cualquier cosa
que quisieras escribir aqui sobre el push se escribiria antes de que el push ocurriera.

🔑 **Un segundo commit tampoco lo arregla:** tendria exactamente el mismo problema con su propio
push, y asi hasta el infinito. No hay orden de pasos que lo resuelva.

**Su sitio es el reporte de hoy**, en «Sin resolver» (Paso 8). Y el arranque de manana debe leer
`git status -sb` —no `--short`— porque `--short` no imprime la linea de la rama y un commit sin
subir le resulta **invisible**.

---

## Paso 5 — `_persistence/debt_tec.md`: aqui si propones

La deuda tecnica es el unico registro del porque que **si deja rastro en la evidencia**: algo a
medias, un `TODO`, una comprobacion que quedo sin hacer, un archivo que quedo inconsistente.

Por eso, a diferencia de los cuatro de abajo, **puedes proponer entradas** — con dos condiciones:

1. **Solo lo que el diff respalde.** Nada de deuda intuida.
2. **Marcada como propuesta en el reporte**, para que el usuario la confirme o la tumbe.

Estados (los mismos cuatro): `Implementada` · `No implementada` · `Cancelada` · `Suspendida`,
donde `Implementada` significa deuda **ya pagada**. Mas Importancia y Urgencia, igual que en tareas.

⚠️ **`Cancelada` y `Suspendida` no las escribes tu:** significan «esto dejo de ser deuda» y
«decidimos convivir con esto por ahora», y las dos son decisiones del usuario, no lecturas del diff.

---

## Paso 6 — Los otros cuatro: **revisalos, no los escribas**

`decisions.md`, `assumptions.md`, `constraints.md` y `lessons.md` **no son del cierre**. Los
escribe `executor` en el momento en que las cosas pasan, porque una decision no aparece en el
`git diff`: nace en la conversacion.

**Lo que si haces: comprobar que no se quedaron cortos.**

1. Leelos.
2. Comparalos con lo que muestra el diff.
3. Si el diff ensena algo que **claramente fue una decision** y no esta anotado —se eligio una
   alternativa, se cambio una estructura, se descarto un camino— **no lo escribas tu**: senalalo
   en el reporte, para que lo dicte el usuario.

🚨 **Los cuatro se reportan siempre, aunque no falte nada.** El Paso 8 tiene una seccion propia
para ellos: cada uno sale con «al dia» o con lo que falta por anotar. Sin esa linea, un cierre que
reviso y uno que no reviso se ven igual.

**La unica excepcion, y es mecanica:** si un supuesto `A-XXX` quedo comprobado por la evidencia
del diff, puedes moverlo a `decisions.md` o `lessons.md` y marcarlo `Confirmado` en
`assumptions.md`. Eso no es interpretar, es aplicar la regla del ascenso — y **dilo en el reporte**.
Al moverlo, toca **los dos indices**, con id nuevo en el destino.

### 🚨 Una casilla mas, obligatoria: que entra al repositorio remoto

**Este proyecto sube a GitHub, y `_persistence/` va a Git a proposito** — es la historia del
proyecto. Asi que pregunta, en voz alta, sobre el diff de hoy:

> **Entro algo que no deberia salir de esta maquina?** Credenciales, tokens, rutas personales,
> datos de terceros, contenido de fuentes externas copiado sin necesidad.

Si entro, **sale** — y se sustituye por un equivalente inventado, dicho como inventado.

⚠️ **Honestidad sobre su fuerza, y va escrito porque importa: esto pregunta, no detecta.** No es
un test y no muerde. `.gitignore` cubre `.env`, pero **no cubre una credencial pegada dentro de
una leccion**. Ese es el camino por el que algo se escapa sin que ninguna herramienta lo note.
**Marcarla sin haber mirado el diff es marcarla con una intencion.**

📌 Se reporta siempre, igual que los cuatro.

---

## Paso 7 — El commit y el push

**Primero la verificacion, despues el commit.** Nunca al reves.

```
git status
```

🚨 Comprueba que **no aparezca ningun archivo de secretos** (`.env` y variantes). Si aparece,
**detente**, no anadas nada y reportalo: falta una linea en `.gitignore`. Git no olvida — si una
credencial entra al historial, borrar el archivo despues no la borra.

Si esta limpio:

```
git add -A
git commit -m "..."
```

El mensaje dice **que avanzo y por que**, no que archivos cambiaron: eso ya lo sabe Git. Primera
linea corta, y debajo lo que valga la pena. Termina siempre con:

```
Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>
```

⛔ **Comandos prohibidos, sin excepcion:** `git commit --amend`, `git reset`, `git checkout --`,
`git restore`, `git rebase`, `git clean`, `git push --force` y cualquier otra cosa con `--force`.
El trabajo del cierre es **anadir** historia, nunca reescribir ni borrar la que hay. Si crees que
hace falta uno de esos, **detente y dilo**: esa decision es del usuario.

### El cierre no acaba en el commit

```
git push
```

⚠️ **Si es el primer push del repositorio**, la rama todavia no existe en el remoto:

```
git push -u origin main
```

🔑 **Un `git push` a secas solo anade, y por eso si entra en el protocolo** — encaja con la regla
de arriba, no la rompe. Lo que reescribe historia es `--force`, y ese sigue prohibido.

Despues, siempre:

```
git status -sb
```

🚨 **Si la primera linea todavia dice `ahead`, el push no ocurrio** —remoto sin configurar,
credenciales, red— y el trabajo existe solo en este disco. **No lo tapes:** va en el reporte, en
«Sin resolver», con lo que salio mal. Un disco roto esa noche se lleva la sesion entera.

⚠️ **Y ahi se queda: en el reporte.** No vuelvas atras a anotarlo en `tasks.md` —ya esta
commiteado— ni abras un commit nuevo para arreglarlo. El porque esta en el Paso 4.

> 🔑 La regla no es «si no hay hash, no hubo cierre»: eso se cumple entero y el trabajo se queda
> sin subir igual, porque **un commit es local**. La regla es **«si el hash no esta en `origin`,
> no hubo cierre»**, y se comprueba con `git status -sb`, no con el hash.

---

## Paso 8 — Reporte en pantalla

En espanol, sin relleno. **Entregalo completo**, no un resumen diciendo que «ya actualice los
archivos».

🚨 El mensaje final del agente no llega al usuario por si solo: lo recibe `executor`, que lo
retransmite. Un reporte recortado se recorta dos veces.

```
## Cierre de sesion — <fecha>

### Lo que dice la evidencia
- <N> archivos tocados: <los principales>
- <que quedo hecho, segun el diff>

### _persistence/ actualizado
- progress.md — <S-XXX nueva> · <en una linea, que cambio en «Estado general»>
- tasks.md — <N implementadas, N pendientes, N nuevas>
- debt_tec.md — <sin novedad | PROPUESTA: DT-XXX ... (pendiente de confirmar)>

### Los cuatro del porque — revisados, no escritos
- decisions.md — <al dia | falta anotar: ...>
- assumptions.md — <al dia | falta anotar: ... | ascendido A-XXX → D-XXX>
- constraints.md — <al dia | falta anotar: ...>
- lessons.md — <al dia | falta anotar: ...>
- 🚨 Repositorio remoto — <nada sensible, diff mirado | 🚨 SACAR: ...>

### Commit
Indices de `_persistence/` — <al dia | corregidos | 🚨 SIN COMPROBAR — <que fallo>>
<hash corto> — <primera linea del mensaje>
<"subido a origin, `git status -sb` sin ahead" | 🚨 "SIN SUBIR — <que fallo>">

### Para manana
<el siguiente paso concreto, tal como quedo en progress.md>

### Sin resolver        <-- omitir si no hay nada
- <discrepancias entre el traspaso y el diff>
- <lo que quedo a medias y en que punto>
- <lo que hay que preguntarle al usuario>
```

---

## Reglas del protocolo

- **No inventes** avances, fechas, decisiones ni tareas. Si un archivo esta vacio o falta
  informacion, **dilo en el reporte** en lugar de rellenarlo.
- **No escribas codigo** ni arregles nada, aunque veas algo roto. Anotalo en `tasks.md` y sigue.
  Cerrar la sesion no es el momento de abrirla otra vez.
- **No toques `temporal/`** ni el repositorio de `auditor`.
- **No dupliques.** Cada archivo tiene un trabajo: `progress.md` da la vision general y no detalla
  tareas; el detalle de tareas vive solo en `tasks.md`.
- **Escribe corto.** Un `progress.md` que nadie lee no orienta a nadie.
