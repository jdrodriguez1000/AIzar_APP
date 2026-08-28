---
name: protocol-start
description: Protocolo de inicio de sesion del proyecto. Lee de forma obligatoria el estado de git, CLAUDE.md, _persistence/progress.md y _persistence/tasks.md; a demanda decisions.md, constraints.md, assumptions.md, lessons.md y debt_tec.md. Con eso presenta en pantalla donde esta el proyecto, las ultimas tareas realizadas y las siguientes, ordenadas por urgencia e importancia. Es de solo lectura. Uso exclusivo del agente session-starter.
---

# Protocolo de inicio de sesion

Este protocolo lo ejecuta **unicamente** el agente `session-starter`. Su objetivo es reconstruir
el estado del proyecto al comenzar una sesion y presentar un resumen accionable.

**Es de solo lectura. No modifica ningun archivo.** Ni para arreglar algo que veas mal: eso se
reporta y lo decide `executor`.

## 🚨 Que es una sesion

Una sesion **no es un dia de trabajo**: es una jornada. Puede haber una sesion por la manana,
otra por la tarde y otra por la noche **de la misma fecha** (decision D-009).

> 🔑 **Consecuencia directa: las fechas no identifican sesiones. Los ids `S-XXX` si.**

Nunca digas «la sesion de ayer» ni «la ultima sesion, del 27». Di **`S-007`**. Y para saber cual
fue la ultima, mira el **id mas alto**, nunca la fecha mas reciente: varias filas pueden compartir
fecha siendo sesiones distintas, y ordenar por fecha las mezcla.

## Los tres actores del proyecto

| Actor | Que deja escrito |
|---|---|
| **executor** (sesion de trabajo) | construye, y registra el porque en el momento |
| **`session-closer`** | `progress.md`, `tasks.md`, propuestas de deuda, el informe `_audit/S-XXX.md`, el commit y su push |
| **auditor** | su propio repositorio; audita, verifica y recomienda |

El auditor trabaja **fuera de nuestras sesiones**: puede haber auditado entre el ultimo cierre y
ahora, y **nada en nuestro repositorio se entera solo**. Por eso el Paso 1c lo mira.

🚨 **Su repositorio es de solo lectura para nosotros** (restriccion C-002). Se lee, se reporta, y
nunca se escribe en el.

---

## Paso 1 — Evidencia obligatoria

Lee siempre, sin excepcion, y **en este orden**.

### 1a. Primero el repositorio — es el hecho, no el relato

```
git log --oneline -5
git status -sb
```

🚨 **`-sb`, no `--short`.** Los dos listan los archivos sueltos, pero solo `-sb` imprime **la
linea de la rama**, que es donde se ve si la sesion anterior subio su trabajo:

```
## main...origin/main [ahead 1]      <-- hay un commit que no esta en origin
```

Con `--short` esa linea no sale. Un commit sin subir es **invisible**: el repositorio se ve
limpio, el arranque no dice nada, y el trabajo de la jornada anterior existe solo en este disco.

⚠️ **Si `git log` falla porque no hay commits todavia**, no es un error: el repositorio esta
recien creado. Dilo y sigue.

### 1b. Despues, los archivos que siempre se leen

1. **`PROJECT.md`** — los datos propios de este proyecto: nombre, rutas, remoto, codigos. **Todo lo
   que en este protocolo aparece como «el proyecto» o «el auditor» se resuelve ahi.** Leelo primero:
   sin el no tienes las rutas de los pasos siguientes.
2. **`CLAUDE.md`** — como se trabaja. Es corto a proposito y es el **ancla contra inventar**.
3. **`_persistence/progress.md`** — secciones 1 (Estado general), 2 (Ultimo realizado),
   3 (Siguiente paso), y la tabla de sesiones del indice.
4. **`_persistence/tasks.md`** — el indice, que ya trae estado, importancia y urgencia de cada tarea.

De los dos de `_persistence/` lee **el indice**, no el archivo entero. Ver *«Como se leen estos
archivos»* mas abajo.

Si alguno no existe o esta vacio, **dilo en el reporte** en lugar de inventar contenido.

### 1c. Y el tablero del auditor

```bash
cat "<ruta del campo «Canal de vuelta» de PROJECT.md>"
```

Es el **canal de vuelta** (D-018): una fila por auditoria entregada, apuntando a un `R-XXX.md` que
audita uno de nuestros `_audit/S-XXX.md`, en emparejamiento 1:1.

Mira dos cosas, y las dos van al reporte:

| Lo que ves en su tabla | Que significa | Que haces |
|---|---|---|
| una fila que **no** figura en nuestro `_audit/index.md` con su veredicto | auditoria entregada **sin acuse de recibo** | reportala arriba: es lo primero de la jornada |
| una fila marcada `Huerfana` | pasaron dos sesiones nuestras sin recogerla | reportala **primero que ninguna otra**: se re-entrega con prioridad |

Si hay una auditoria nueva, **di su ruta, su veredicto y cuantos hallazgos siguen abiertos**. No la
resumas ni la interpretes: quien la va a leer entera es `executor`.

⚠️ **No abras los `R-XXX.md` salvo que el indice diga que hay algo nuevo.** El tablero es la
respuesta por defecto, igual que en `_persistence/`.

🚨 **El estado de cada hallazgo es del auditor, no nuestro.** El decide cuando un hallazgo queda
cerrado, verificandolo sobre un commit posterior. Nosotros no llevamos copia de esos estados: lo
nuestro son las tareas, decisiones y deuda que salgan de ellos. **No espejes su tablero.**

⚠️ Si la carpeta no existe o no se puede leer, **dilo en el reporte** y sigue. No supongas que no
hay auditorias.

### Por que el `git` va primero

> 🔑 **`progress.md` es lo que alguien escribio que paso. `git log` es lo que paso.**

Un archivo de estado puede quedar desactualizado —una sesion que se cayo, un cierre a medias— y
no tiene forma de avisarlo. El repositorio si. Al leerlo primero, entras a los archivos ya
sabiendo si se les puede creer.

### Cinco desfases que hay que reportar

| Lo que ves | Que significa | Dilo asi |
|---|---|---|
| el ultimo commit **no** aparece reflejado en `progress.md` | la sesion anterior no cerro bien | *«⚠️ `progress.md` va por detras del ultimo commit»* |
| `git status` tiene cambios sin commitear | quedo trabajo suelto | *«⚠️ hay N archivos sin commitear»* |
| la primera linea de `git status -sb` dice `ahead` | la sesion anterior **no subio** | *«🚨 N commits sin subir a `origin` — el trabajo existe solo en este disco»* |
| hay commits que tocan `_persistence/` **posteriores** al ultimo que toco `progress.md` | el archivo de estado se sello antes que la ultima entrada | *«⚠️ `progress.md` se sello en `<hash>` y hay N commits posteriores de `_persistence/`»* |
| el indice de un archivo y sus entradas no coinciden | un cierre quedo a medias | *«⚠️ `<archivo>`: `<codigo>` esta en el indice y no en el detalle (o al reves)»* |
| hay una auditoria en `_review/index.md` sin veredicto en nuestro `_audit/index.md` | se entrego y no se recogio | *«🚨 `R-XXX` entregada el <fecha> sin acuse de recibo»* |

La cuarta se comprueba con **dos** ordenes, no con una:

```bash
git log --oneline -3
git log --oneline -2 -- _persistence/progress.md
```

Si el hash de arriba **no** es el mismo que el de abajo, mira que tocaron los commits de en medio.
Si tocaron `_persistence/` y `progress.md` no esta entre ellos, **el estado quedo congelado antes
que la ultima entrada**.

La quinta se comprueba con una sola orden, y no gasta contexto:

```bash
for f in tasks decisions constraints assumptions lessons debt_tec progress; do
  echo "== $f"
  diff <(grep -oE '^\| \[?[A-Z]+-[0-9]+' "_persistence/$f.md" | grep -oE '[A-Z]+-[0-9]+' | sort -u) \
       <(grep -oE '^#{3} [A-Z]+-[0-9]+'   "_persistence/$f.md" | grep -oE '[A-Z]+-[0-9]+' | sort -u)
done
```

Sin salida bajo un archivo = coherente. Una linea `<` es una fila de indice sin entrada; una `>`
es una entrada que no esta en el indice — y una entrada fuera del indice **es invisible para este
mismo arranque**, que lee indices.

> 🔑 **Y el error va en la direccion cara.** Un estado que dice *«ya esta hecho»* cuando falta se
> descubre solo: alguien va a hacerlo y no lo encuentra. Uno que dice **«falta»** sobre algo
> terminado **no se descubre — se paga repitiendolo**, y se paga con la sesion que este protocolo
> existe para ahorrar.

🚨 **La tercera es la unica que se pierde para siempre.** Las dos primeras son desorden: el
trabajo esta guardado, solo mal contado. En la tercera **no esta guardado en ningun otro sitio** —
un disco que falle esa noche se lleva la jornada entera.

Es tambien la unica que **no puede haberse anotado en `tasks.md`**: cuando el cierre supo que el
push habia fallado, su commit ya estaba hecho. Por eso el arranque tiene que mirarlo con sus
propios ojos en vez de fiarse de los archivos. El razonamiento completo esta en `protocol-close`,
Paso 4. **Este protocolo es el unico sitio del sistema donde un push fallido se descubre.**

Si la ves, **dilo arriba del todo y propon subirlo como primera accion.**

Si detectas cualquier desfase, **el reporte lo dice arriba del todo**, antes del estado.

### 🚨 La regla que manda sobre todas

**Todo lo que digas sobre QUE ES el proyecto tiene que salir de un archivo que abriste en esta
corrida.** Si no lo abriste, no lo digas.

Vale para el alcance, la tecnologia, el metodo y que significa cada etapa. **No completes con lo
que suele llevar un proyecto de este tipo.**

🚨 **Comprueba si el alcance del proyecto esta registrado antes de decir una palabra sobre el.**
Si `PROJECT.md`, `CLAUDE.md` y `_persistence/` no dicen que es, para que sirve ni con que se
construye, entonces **cualquier cosa que suene razonable sobre eso esta inventada, sin excepcion**.
Dilo como lo que es: «el alcance no esta registrado».

Si algo no esta escrito en ningun sitio, di **«no esta registrado»**. Es una respuesta valida y
util. Rellenarlo no lo es.

---

## Paso 2 — Lectura a demanda

Estos archivos **no** se leen por defecto. Leelos solo cuando algo del Paso 1 lo justifique, y
teniendo clara **que pregunta concreta** quieres responder con cada uno:

| Archivo | Leelo cuando… |
|---|---|
| `_persistence/decisions.md` | progress/tasks mencionen una decision, un cambio de rumbo, o una tarea dependa de una previa |
| `_persistence/constraints.md` | las siguientes tareas toquen areas con limites conocidos |
| `_persistence/assumptions.md` | haya tareas apoyadas en supuestos sin confirmar, o supuestos que puedan haber caducado |
| `_persistence/lessons.md` | se vaya a repetir un tipo de trabajo que ya fallo antes |
| `_persistence/debt_tec.md` | haya deuda que bloquee lo siguiente, o propuestas del cierre sin confirmar |
| `_audit/index.md` | necesites contrastar el Paso 1c: que auditorias hemos recogido ya y cuales seguimos debiendo |
| el `R-XXX.md` que indique el tablero | el Paso 1c muestre una auditoria nueva **y** el usuario pida el detalle. Por defecto basta con anunciarla |

⚠️ **`temporal/` no se lee.** Es el area de trabajo del usuario, no parte del registro, y su
contenido cambia o desaparece sin aviso.

---

## Como se leen estos archivos

Los siete archivos de `_persistence/` tienen la misma forma: **indice arriba, convenciones
despues, detalle debajo**. El indice de `tasks.md` y `debt_tec.md` ya trae **estado, importancia
y urgencia** en la propia fila.

> 🔑 **El indice es la respuesta por defecto; el detalle es la excepcion.**

1. **Lee el indice**, que enlaza cada entrada por ancla.
2. **Decide desde el indice.** La mayoria de las veces el titulo y el estado bastan.
3. **Baja al detalle solo si el indice no responde**, saltando a esa seccion — no leyendo el
   archivo de arriba abajo.

Un archivo de `_persistence/` puede crecer mucho. Leerlo entero para sacar una linea del reporte
gasta contexto que hara falta despues, cuando toque trabajar.

### 🚨 El campo de estado manda sobre la prosa

En los indices, cada fila trae su **estado**. **Para decir que falta, lee el CAMPO — no resumas
el parrafo del detalle.**

> 🔑 **El parrafo cuenta la historia de la entrada; el campo dice como acabo.** Cuando alguien
> corrige una entrada suele reescribir el parrafo y **olvidarse del campo**, o al reves. Si los
> dos se contradicen, **no elijas: reportalo como desfase** y sigue el campo mientras tanto.

Extraer los campos cuesta una orden y no gasta contexto:

```bash
# tareas pendientes
grep -E '^\| \[T-' _persistence/tasks.md | grep -E '\| No implementada \|'

# pendientes y bloqueantes — lo que abre el dia
grep -hE '^\| \[(T|DT)-' _persistence/tasks.md _persistence/debt_tec.md \
  | grep -E '\| No implementada \|' | grep 'Bloqueante' | grep -v 'No bloqueante'

# ultima sesion registrada (id mas alto, no fecha)
grep -E '^\| \[S-' _persistence/progress.md | tail -1
```

### 🚨 Lo cerrado no se reporta como abierto

Aqui nada se tacha: **el estado va en su columna**, y hay que leerlo.

| Archivo | No reportes como abierto |
|---|---|
| `tasks.md` | `Implementada` · `Cancelada` · `Suspendida` |
| `debt_tec.md` | `Implementada` · `Cancelada` · `Suspendida` |
| `decisions.md` | `Revocada por D-XXX` |
| `assumptions.md` | `Confirmado` · `Refutado` |
| `constraints.md` | `Levantada` |

```bash
grep -nE '\| (Cancelada|Suspendida|Refutado|Levantada|Revocada por D-[0-9]+) \|' _persistence/*.md
```

⚠️ Las barras del patron importan: sin ellas el grep tambien devuelve las tablas de
`## Convenciones`, que solo enumeran los estados posibles. Un grep que devuelve mas ruido que
senal se aprende a ignorar.

Una entrada cerrada **conserva su texto a proposito**, para que se entienda que se creia y por que
dejo de valer. **Ese texto esta ahi para explicar, no para reportarlo como vigente.** Si hace
falta mencionarla, se dice *«`DT-003`, cancelada»* — nunca lo que decia cuando estaba abierta.

### 🚨 Y el caso mas traicionero: la decision revocada

Una decision revocada **conserva su parrafo entero**, redactado en presente y sonando vigente. Lo
unico que la desmiente es su campo `Estado`.

> 🔑 **Quien lee el parrafo y no el campo se lleva exactamente lo contrario de lo que rige hoy.**
> Ya hay un caso real en este proyecto: `D-007` dice «no crear el agente `session-closer`» y esta
> **`Revocada por D-008`**, que decidio justo lo contrario.

Antes de citar el porque de una decision: **mira su estado**, y si esta revocada, **cita la que la
revoco**, no la revocada.

---

## Paso 3 — Reporte en pantalla

En espanol, sin relleno:

```
## ⚠️ Desfase detectado        <-- omitir si no hay ninguno
- <que no cuadra entre el repositorio y los archivos>

## Donde estamos
<etapa, salud y bloqueo activo, segun progress.md seccion 1>
<ultimo realizado y siguiente paso, secciones 2 y 3>
<ultima sesion: S-XXX>

## Ultimas tareas realizadas
- <codigo> <tarea>
- ...

## Siguientes tareas
🔻 <bloqueo o condicion vigente, si lo hay>   <-- obligatorio si existe, y va PRIMERO
1. <codigo> <tarea> — <importancia/urgencia> — <por que es la siguiente>
2. ...

## Contexto relevante        <-- omitir si no leiste archivos del Paso 2
- **Decisiones:** ...
- **Restricciones:** ...
- **Supuestos:** ...
- **Lecciones:** ...
- **Deuda:** ...
```

Reglas del reporte:

- 🔑 **Las siguientes tareas se ordenan por urgencia y despues por importancia**, no por orden de
  aparicion en el archivo: primero las `Bloqueante`, y dentro de ellas `Alta` antes que `Media` y
  `Baja`. Esos campos existen para decidir el orden del dia; usalos.
- 🔻 **Un bloqueo vigente es OBLIGATORIO si existe, y va el primero de «Siguientes tareas».**
  Buscalo en `progress.md`, en `tasks.md` y en `debt_tec.md`.
- ⚠️ **Un bloqueo se cita por su ACCION, no por la fecha en que se espera.** Escribirlo como
  *«lo primero de la proxima etapa»* lo deja gastado en cuanto esa etapa empieza.
- 🚨 **Un bloqueo no se cuelga de una tarea que no lo tiene.** Si no sabes de cual es, **dilo
  suelto: el bloqueo importa mas que su dueno.**
- 🚨 **No inventes relaciones entre tareas.** Cada una se describe con lo que dice **su** fila. Si
  dos se parecen, no se mezclan: se citan las dos por su codigo.
- 🚨 **Cita siempre archivo y codigo.** Quien recibe este reporte **no leyo los archivos**: solo
  tiene tu texto. Un dato sin su codigo lo deja sin forma de ir a comprobarlo, y lo que no pueda
  comprobar tendra que creertelo o volver a leerlo todo.
- Maximo 5 elementos por lista; si hay mas, quedate con los mas recientes o prioritarios y dilo.
- **Contexto relevante** solo con lo que cambie la decision de que hacer ahora, no como resumen de
  los archivos.
- Termina senalando bloqueos o informacion faltante, si los hay.
- **No modifiques ningun archivo.** Este protocolo es de solo lectura.
