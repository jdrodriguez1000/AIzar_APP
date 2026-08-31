---
name: protocol-close
description: Protocolo de cierre de sesion del proyecto. Recoge la evidencia real del trabajo (git status, git diff, git log), actualiza de forma obligatoria _persistence/progress.md y _persistence/tasks.md, propone entradas de debt_tec.md, y solo revisa —sin escribirlos— decisions.md, assumptions.md, constraints.md y lessons.md; despues deja la sesion cerrada con un commit y su push. Uso exclusivo del agente session-closer, que se lanza al terminar una jornada de trabajo o cuando el usuario pida "cerremos la sesion", "cierra la sesion", "finalicemos el trabajo", "guarda el avance", "terminamos por hoy" o algo similar.
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
| **El cierre** (este protocolo) | `progress.md`, `tasks.md`, propuestas a `debt_tec.md`, el informe `_audit/S-XXX.md` | los cuatro del porque |
| **auditor** | su propio repositorio | no construye |

🚨 **Nunca escribas en el repositorio del auditor** — su ruta esta en `PROJECT.md`.
No es nuestro (restriccion C-002). Lo que venga de la auditoria se refleja en
`_persistence/tasks.md` como tarea con `Origen: auditor`, y solo despues de que `executor` la
evalue y la considere correcta (decision D-003).

🚨 **No toques `temporal/`.** Es el area de trabajo del usuario, no parte del registro.

---

## Paso 1 — Recoger la evidencia (antes de escribir nada)

Empieza leyendo **`PROJECT.md`**: los datos propios de este proyecto —nombre, rutas, remoto,
codigos—. Todo lo que en este protocolo aparece como «el proyecto» o «el auditor» se resuelve ahi.

Despues, en este orden y sin saltarte ninguno:

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

### 1b. El control de fuga de datos del proyecto

Con la evidencia delante, corre **tal cual** este control y **pega su salida cruda en el informe**:

```bash
git grep -nE "<Nombre del proyecto>|<carpeta raiz de las rutas absolutas>|<host del remoto>" -- .claude CLAUDE.md
```

Los tres valores salen de `PROJECT.md`: **Identidad → Nombre del proyecto**, el segmento comun de
las dos rutas absolutas de **Rutas**, y el host del campo **Remoto** de *Control de versiones*.

🔑 **La respuesta correcta es CERO lineas** (`exit 1`). Si devuelve alguna, un dato propio del
proyecto se ha colado en un archivo que deberia ser reutilizable tal cual: es una regresion de
`D-021` y **se reporta como hallazgo propio en el informe**, no se arregla en silencio ni se omite.

🚨 **El ambito es parte del control, no un detalle de implementacion.** Se acota a `.claude/` y
`CLAUDE.md`, y a nada mas, porque es el **unico sitio donde «cero» es la respuesta correcta**. El
mismo patron sobre el arbol entero da siempre positivos **legitimos**:

| Donde | Por que es correcto que aparezca |
|---|---|
| `PROJECT.md` | es su sitio, por diseño: el archivo existe justamente para concentrarlos |
| `_audit/S-XXX.md` | informes ya entregados; no se reescriben |
| `_persistence/` | registro historico: describe lo que paso, y el pasado no se reescribe |

⚠️ **Un control que avisa de todo termina apagado.** Si se ensancha el ambito «por si acaso», el
control pasa a devolver decenas de lineas correctas cada sesion, alguien deja de mirarlas, y
entonces no detecta nada — que es peor que no tenerlo, porque ademas se cree que existe.

📌 **Por que este control existe:** `D-021` vacio de datos propios los protocolos, y la regresion
aparecio **dentro del mismo commit que la implemento** — tres veces (`F-006`, `F-007`, `F-008` de
`R-004`). No es un riesgo hipotetico. Y es detectable sin ejecutar nada, porque es una busqueda de
texto: cuesta un segundo. Va escrito con su patron **precisamente** porque el hallazgo `F-009`
nacio de que cada quien lo reinventara.

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

🚨 **El `awk` del principio de cada rama no es decoracion: descarta los bloques de codigo
cercados.** Desde que el registro guarda **salida cruda de comandos** como evidencia, esos bloques
contienen encabezados y codigos identicos a los reales — `### C-002`, `| [T-014]…` — que son citas de
como estaba el archivo, no entradas. Sin el filtro, el control senala como huerfano lo que en
realidad es una prueba bien puesta. Ocurrio cuatro veces en dos jornadas y las cuatro hubo que
descartarlo a mano; una alarma que siempre resulta falsa se aprende a ignorar, y entonces el dia que
sea verdadera tampoco se mirara.

```bash
for f in tasks decisions constraints assumptions lessons debt_tec progress; do
  echo "== $f"
  diff <(awk '/^```/{c=!c; next} !c' "_persistence/$f.md" | grep -oE '^\| \[?[A-Z]+-[0-9]+' | grep -oE '[A-Z]+-[0-9]+' | sort -u) \
       <(awk '/^```/{c=!c; next} !c' "_persistence/$f.md" | grep -oE '^#{3} [A-Z]+-[0-9]+'   | grep -oE '[A-Z]+-[0-9]+' | sort -u)
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

## Paso 2c — Las carpetas del arbol contra las declaradas (antes del `git add`)

El Paso 2b compara un archivo consigo mismo. Este compara **el repositorio contra su declaracion**:
los directorios de primer nivel que existen de verdad, frente a las filas de la tabla «Carpetas
propias» de `PROJECT.md`.

```bash
diff <(git ls-tree -d --name-only HEAD | sed 's|$|/|' | sort) \
     <(sed -n '/^## Carpetas propias/,/^## /p' PROJECT.md | grep -oE '^\| `[^`]+/`' | tr -d '|` ' | sort)
```

**Las dos direcciones importan, y dicen cosas distintas:**

| Lo que ves | Que significa | Que haces |
|---|---|---|
| `<` una carpeta que existe y **no** esta declarada | el repositorio crecio y el registro no se entero | 🚨 proponlo como `DT-XXX`, o declarala si es obvio. **Es lo que paso con una carpeta entera durante dos sesiones** |
| `>` una fila declarada cuya carpeta **no** existe | o se borro sin actualizar el registro, o esta declarada por adelantado a proposito | comprueba cual de las dos. Si es deliberado, **tiene que haber un `D-XXX` que lo diga** |

⚠️ **Una diferencia con motivo escrito no es un fallo; una sin el, si.** Este control no lleva lista
de excepciones dentro, y es deliberado: una lista de excepciones envejece sin que nadie la revise y
acaba tapando justo lo que el control existe para ver. Lo que se exige es que **cada diferencia que
sobreviva tenga su razon en `PROJECT.md` o en una `D-XXX`** — y si no la tiene, esa es la noticia.

📌 **Por que existe este paso:** el desfase que lo motivo se encontro **de casualidad**, mientras se
preparaba otra cosa. Un metodo cuyo disparador es «alguien lo nota» no falla ruidosamente: falla en
silencio, y no hay forma de saber cuantas veces no se activo. Esto puede **salir rojo** sin que nadie
sospeche nada, que es la unica diferencia entre un detector y una coartada (`R-007` §5.1, `T-053`).

⛔ **No sustituye a releer.** La relectura encuentra cosas que ninguna comparacion mecanica ve; lo
que no puede es ser el unico filtro para lo que si es mecanizable.

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

### 🚨 Una comprobacion concreta sobre `decisions.md`: las que verifican, con comando y salida

Al leer `decisions.md`, mira **las entradas de esta sesion que afirmen un resultado comprobado**.
Cada una debe llevar un bloque de verificacion con la **orden ejecutada literal** y **su salida
cruda**. Son dos grupos, y el segundo se olvida:

| Grupo | Ejemplos |
|---|---|
| las de `Origen: auditor` | «verificado que el hallazgo persiste en `HEAD`» |
| **las de iniciativa propia que afirman un resultado** | «no hay secretos en el archivo», «cero coincidencias», «los dos numeros cuadran» |

⚠️ **El segundo grupo no lo pidio nadie, y por eso se cuela sin evidencia.** Una comprobacion que
hacemos por nuestra cuenta se siente como parte del trabajo, no como una afirmacion auditable — pero
en el registro se lee igual que cualquier otra. Sin patron ni ambito escritos, el auditor tiene que
rehacer el barrido entero para contrastarlo.

| Que dice la entrada | Que es | Que haces |
|---|---|---|
| «corri `git log -1 …`», y debajo lo que salio | evidencia | nada, esta bien |
| «se comprobo», «verificado», «existe y es legible» | **un veredicto sin evidencia** | 🚨 senalalo en el reporte del Paso 8 |

⛔ **No lo arregles tu, y menos aun reconstruyendo el comando ahora.** Vale lo mismo que en el resto
del paso: los cuatro archivos no son tuyos. Y aqui hay una razon extra — un bloque de verificacion
que no se ejecuto cuando dice haberse ejecutado es **peor que su ausencia**: convierte «falta
evidencia» en «hay evidencia falsa». Senalar, no rellenar.

⚠️ **Rige hacia adelante.** Las entradas antiguas que solo dijeron «se comprobo» se quedan como
estan; no las reportes como pendientes. Ver `D-037` y `T-031`.

### 🚨 Un riesgo nombrado en el informe y en ningun otro sitio: senalalo

Al leer el borrador del informe, busca los riesgos que **el propio texto reconoce** —«si algun dia
X, hoy nada lo detectaria», «esto asume que Y», «queda por confirmar Z»— y comprueba si cada uno
tiene **codigo** en `_persistence/`: un `A-XXX`, una `T-XXX` o un `DT-XXX`. Si no lo tiene,
**senalalo en el reporte del Paso 8**.

🔑 **El informe es el canal, no el registro.** Un riesgo escrito solo ahi se lee mientras ese informe
sea el ultimo, y deja de leerse en cuanto llega el siguiente. Peor si el riesgo colgaba de una deuda
que se marca `Implementada` en la misma sesion: **desaparece del radar en el momento exacto en que se
cierra lo que lo contenia**, porque una entrada pagada ya no se relee.

⛔ **No lo registres tu** —los cuatro archivos del porque no son tuyos—: senalalo, con la frase del
informe que lo enuncia, para que `executor` le ponga codigo antes del commit.

⚠️ **Esto ya ha ocurrido tres veces con la misma forma** y las tres se arreglaron como caso
particular. Por eso esta escrito aqui: para que la cuarta la detecte el protocolo y no la siguiente
auditoria (`F-012`, `F-019`, `T-054`).

**La unica excepcion, y es mecanica:** si un supuesto `A-XXX` quedo comprobado por la evidencia
del diff, puedes moverlo a `decisions.md` o `lessons.md` y marcarlo `Confirmado` en
`assumptions.md`. Eso no es interpretar, es aplicar la regla del ascenso — y **dilo en el reporte**.
Al moverlo, toca **los dos indices**, con id nuevo en el destino.

### 🚨 Si citas el repositorio del auditor, cita tambien el commit

Su repositorio es de solo lectura para nosotros, pero **no es estatico**: su sesion puede estar a
mitad de escritura mientras nosotros leemos. Lo que se ve entonces es un **arbol de trabajo**, cierto
en ese instante y que puede no llegar nunca a ningun commit.

Por eso, toda afirmacion sobre el contenido de su repositorio que vaya a `progress.md` o al informe
—registro permanente— va **anclada**:

```bash
git -C <repositorio del auditor, segun PROJECT.md> log -1 --format=%h
```

Ese hash acompana al valor leido. Si no se ancla, se declara: *«lectura del arbol de trabajo, no
reproducible»*.

⛔ **Nunca cites su archivo por numero de linea sin ancla.** Un numero de linea afirma precision y
no la tiene: el archivo se reescribe, y quien intente reproducirlo mañana no encontrara nada — ni
sabra si el error es suyo, del archivo o de quien lo escribio.

📌 **Ya paso una vez, y no fue culpa de nadie:** se comparo su ultimo estado **commiteado** con lo
que habia en su **arbol de trabajo** dos minutos antes de que commitearan. Las dos lecturas eran
ciertas a la vez porque median arboles distintos. Es exactamente lo que el contrato nos exige a
nosotros —auditar contra el commit del informe, no contra `HEAD`— en el sentido contrario
(`F-021` de `R-007`, `T-051`).

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

## Paso 6b — El informe para la auditoria (obligatorio)

Escribe **`_audit/S-XXX.md`**, con el mismo id que la entrada que acabas de crear en
`progress.md`. Un archivo por sesion. Si `_audit/` no existe, creala.

🚨 **Va antes del `git add`, y no es un detalle de orden: es lo que hace auditable la auditoria.**
Al entrar en el mismo commit que el trabajo que describe, el auditor puede averiguar exactamente
que estado esta juzgando:

```bash
git log -1 -- _audit/S-XXX.md
```

Con ese hash puede ir al `git show` y **verificar cada afirmacion del informe contra el diff real**,
en vez de creersela. Un informe que no se puede anclar a un commit deja al auditor juzgando un
relato.

### Para quien escribes

El auditor **no vivio la sesion, no conoce nuestras convenciones y trabaja en otro repositorio**.
No escribas como si compartiera contexto:

- **Cita siempre codigo y ruta** —el codigo y la ruta tal como aparecen en tu registro, p. ej.
  `T-NNN`, `D-NNN`, `_persistence/tasks.md`. Son su unica via para ir a comprobar.
- **Explica lo que un externo no puede deducir**, pero no repitas los archivos enteros: el informe
  cuenta **esta sesion**, no el proyecto entero.
- 🚨 **Escribe el informe completo, sin resumir.** Lo que se ahorre aqui es exactamente lo que el
  auditor tendra que reconstruir, y lo reconstruira adivinando.

### Estructura del informe

```markdown
# Informe de auditoria — S-XXX

| Campo | Valor |
|---|---|
| Sesion | S-XXX |
| Fecha | AAAA-MM-DD |
| Etapa | |
| Rama | la rama principal, segun `PROJECT.md` |
| Commit auditado | el commit que contiene este archivo (`git log -1 -- _audit/S-XXX.md`) |

## 0. Respuesta a la auditoria anterior     <-- omitir solo si no hay ninguna sin responder

| Hallazgo | Veredicto | Evidencia / Razon |
|---|---|---|
| F-NNN — <resumen> | Implementado | `T-NNN`, en este commit |
| F-NNN — <resumen> | Aceptado — pendiente | `T-NNN`, `No implementada` |
| F-NNN — <resumen> | No se implementa | `D-NNN` |

Los tres veredictos son los unicos validos:

| Veredicto | Cuando |
|---|---|
| `Implementado` | hecho, y esta en este commit |
| `Aceptado — pendiente` | de acuerdo, pero aun no hecho — **con su `T-XXX`** |
| `No se implementa` | rechazado — **con su `D-XXX`** |

### 🚨 Las dos listas del informe se **generan**; escribirlas de memoria es como se quedan cortas

Las secciones 1 y 2 llevan cada una una enumeracion, y **una enumeracion sin salvedad se lee como
exhaustiva**. Es justo el tipo de frase que el auditor usa como atajo para no recorrer el diff
entero — asi que una lista corta no se queda en un descuido: **ensena a confiar en algo que no se
puede contrastar sin rehacerlo**.

Las dos son generables. Sacalas de aqui, no de lo que recuerdes haber tocado:

```bash
git show --stat --name-only --format= <commit>          # seccion 1: archivos tocados
sed -n '/^## Indice/,/^---/p' _persistence/tasks.md \
  | grep "No implementada"                              # seccion 2: tareas abiertas
```

⚠️ **El cierre anade archivos que no son «de contenido»** —la fila de `_audit/index.md`, el propio
informe— y son justo los que se olvidan al escribir de memoria. Si prefieres listar solo los de
contenido, **dilo**: «los archivos de contenido; el cierre anade ademas…». Una lista declarada
parcial es honesta; una lista corta presentada como completa, no.

🚨 **Y no filtres «las relevantes» sin decirlo.** Si la seccion 2 solo cubre algunas tareas abiertas,
la frase lo tiene que decir. El coste de la version correcta es cero; el de la incorrecta es que la
proxima omision, cuando importe, llegue con la misma cara de completa (`F-022` de `R-007`, `T-052`).

### 🚨 Esta tabla se audita fila a fila. Cada veredicto exige algo comprobable

| Veredicto | Lo que el auditor va a comprobar | Si no esta |
|---|---|---|
| `Implementado` | que la correccion **aparezca en el diff de este commit** | es un hallazgo, y el original **sigue abierto** |
| `Aceptado — pendiente` | que cite su `T-XXX`, y que esa tarea **exista y siga abierta** | el hallazgo no se da por recogido |
| `No se implementa` | que cite su `D-XXX` | un rechazo sin decision registrada **no es auditable** |

⚠️ **No marques `Implementado` lo que el diff no muestre.** Si estas de acuerdo pero no esta hecho,
su veredicto es `Aceptado — pendiente` con su tarea abierta. Marcarlo hecho no lo adelanta: lo
convierte en un hallazgo nuevo y deja el original abierto igual.

### 🚨 La tabla va completa: un hallazgo omitido NO cuenta como contestado

**Todos los hallazgos entregados y no cerrados entran en la tabla**, uno por fila, incluso los que
no tocaste esta sesion. Un `F-NNN` que no aparezca **sigue `Entregado` y el auditor lo reclama**:
no se interpreta como aceptado ni como rechazado por omision.

Si un hallazgo no se atendio y no sabes por que, **ponlo igual** y dilo en «Sin resolver» del
reporte. Una fila incomoda vale mas que una ausencia silenciosa.

🚨 **`Aceptado — pendiente` no es opcional ni un adorno.** Sin el, un hallazgo con el que estamos de
acuerdo pero que aun no hicimos no esta implementado ni rechazado: **no aparece en ningun sitio y
desaparece del radar.** Esa es la forma en que se pierden los hallazgos buenos.

⚠️ Un hallazgo rechazado **por coste o prioridad** —no por ser incorrecto— es deuda tecnica por
definicion y exige su `DT-XXX`. Un rechazo por coste sin entrada en `debt_tec.md` es, por si solo,
un hallazgo del auditor, y no requiere criterio: se comprueba mirando si la entrada existe.

### 🚨 Si el rechazo clasifica el asunto como reversible o irreversible, dilo como criterio

Un `No se implementa` que apoye su razon en ese eje **tiene que declarar que la clasificacion se
hizo a criterio** (`D-020`), en la propia fila o en el `D-XXX` que cita: «reversible a criterio,
porque…». **No existe ningun inventario de acciones irreversibles**: esta vacio hasta que `T-016`
lo pueble, y `T-016` no puede cerrarse sin alcance (`T-004`).

⚠️ Escribir «es reversible» a secas presenta una tabla que no existe, y el auditor no tiene como
distinguir un criterio de una consulta. **Tu no lees `decisions.md` entero**, asi que esta es la
unica vez que veras `D-020`: si el eje aparece en la tabla, la salvedad va con el.

## 1. Que se hizo
<lo que muestra el diff, con codigos y rutas. Archivos creados, modificados y por que>
<la lista de archivos sale de `git show --stat`, no de la memoria: ver el aviso de abajo>

## 2. Que NO se hizo, y por que
<lo que quedo pendiente o a medias, y en que punto quedo>
<las tareas abiertas salen del indice de `tasks.md` filtrando `No implementada`, no de la memoria>

## 3. Decisiones tomadas
<cada `D-XXX` de esta sesion: que se decidio, por que, y **las alternativas descartadas**>

## 4. Supuestos vigentes y riesgos
<`A-XXX` abiertos, que se apoya en ellos, y que pasa si resultan falsos>

## 5. Siguiente tarea propuesta
<la primera accion concreta de la proxima sesion, con su codigo, importancia y urgencia>

## 6. Que pedimos auditar
<nuestros propios puntos debiles: lo que quedo flojo, la decision de la que menos seguros
estamos, el supuesto en el que nos apoyamos sin confirmar>
```

### 🚨 La seccion 6 es obligatoria y no puede quedar vacia

Un informe que solo cuenta lo bien que fue todo produce auditorias flojas: el auditor gasta su
turno redescubriendo lo que nosotros ya sabiamos.

**Senalar nuestros propios puntos debiles lo manda directo a lo que importa.** Escribe al menos un
punto real. «Nada que senalar» **no es una respuesta valida**: si de verdad no encuentras ninguno,
di que no lo encontraste y que eso mismo conviene revisarlo.

⚠️ Sigue rigiendo la regla de siempre: **solo lo que la evidencia respalde**. Un punto debil
inventado desperdicia la auditoria igual que uno omitido.

### Y su fila en `_audit/index.md`

El informe no sirve de nada si el auditor no sabe que existe. **Anade su fila** al indice, con
estado **`Pendiente`** y `-` en observaciones:

```
| `S-XXX.md` | S-XXX | AAAA-MM-DD | Pendiente | - | - |
```

La ultima columna es **`Respondida en`**: se rellena cuando un informe posterior contesta a la
auditoria de esta fila. Tu la dejas en `-`.

🚨 **`Pendiente` es el unico estado que escribes tu.** `Sin hallazgos` y `Con hallazgos` los pone
`executor` cuando la auditoria vuelve — tu no puedes saber que encontro alguien que todavia no ha
mirado.

⚠️ **No pongas el hash del commit en la fila.** No puedes: la fila se escribe antes del commit que
la contiene. El auditor lo obtiene con `git log -1 -- _audit/S-XXX.md`, igual que el resultado del
push se mira con `git status -sb` en vez de anotarse (Paso 4). Es la misma imposibilidad, y la
misma solucion: preguntarle a git en vez de intentar escribirlo.

⚠️ **Este informe no reemplaza a `_persistence/`.** Es una vista de **esta sesion** para un lector
externo, no una copia del registro. Y **nunca escribas en el repositorio del auditor**: el informe
vive en el nuestro, y el es quien lo lee.

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

### 7b — Que el informe entro en el commit (obligatorio)

**Ya hay un hash. Preguntale a git si el informe esta dentro de el:**

```bash
git show --stat --name-only HEAD -- _audit/S-XXX.md
git show --stat --name-only HEAD -- _audit/index.md
```

Si el archivo aparece en la salida, entro. Si la salida esta vacia, **no entro**.

🚨 **Esta comprobacion es la que sostiene el Paso 6b entero.** El anclaje del informe al commit es
todo el valor de D-016: sin el, el auditor recibe un relato que no puede contrastar contra ningun
estado. Un paso obligatorio cuyo cumplimiento nadie mira **no es obligatorio, es una intencion**.

**Hay tres resultados, no dos** —los mismos que el Paso 2b, y por la misma razon:

| Que sale | Que significa | Que haces |
|---|---|---|
| los dos archivos aparecen | el informe quedo anclado | sigue al push |
| alguno falta | **el commit no lo lleva** | 🚨 **detente**: escribelo o anadelo y **haz un commit nuevo** que lo incluya, nunca un `--amend`. Dilo en el reporte |
| el comando falla | **no lo comprobaste** | push igual, y a **Sin resolver** con `🚨 SIN COMPROBAR` |

🚨 **La tercera fila otra vez.** «No pude comprobarlo» no es «esta bien». Y la segunda no se
arregla reescribiendo el commit: los comandos de abajo siguen prohibidos, tambien aqui.

⚠️ **Lo que salga de aqui es lo que se escribe en la linea del Paso 8**, con su resultado real. Esa
linea era antes una afirmacion fija que se imprimia igual hubiera entrado el archivo o no; ahora
tiene detras un comando que puede salir rojo. Sin el, un cierre que anclo y uno que no se leian
identicos — que es exactamente el defecto que el Paso 2b ya tenia resuelto para los indices.

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
- decisions.md — <al dia | falta anotar: ... | 🚨 D-XXX (`Origen: auditor`) verifica sin comando ni salida>
- assumptions.md — <al dia | falta anotar: ... | ascendido A-XXX → D-XXX>
- constraints.md — <al dia | falta anotar: ...>
- lessons.md — <al dia | falta anotar: ...>
- 🚨 Repositorio remoto — <nada sensible, diff mirado | 🚨 SACAR: ...>

### Commit
Indices de `_persistence/` — <al dia | corregidos | 🚨 SIN COMPROBAR — <que fallo>>
Informe de auditoria — <`_audit/S-XXX.md` y su fila en `_audit/index.md`, **comprobados en el commit** (Paso 7b) | 🚨 NO ENTRO — <que falto y en que commit nuevo entro> | 🚨 SIN COMPROBAR — <que fallo>>
<hash corto> — <primera linea del mensaje>
<"subido a origin, `git status -sb` sin ahead" | 🚨 "SIN SUBIR — <que fallo>">

### Informe para la auditoria
`_audit/S-XXX.md` — version corta:
- **Se hizo:** <una linea>
- **Quedo pendiente:** <una linea>
- **Siguiente tarea propuesta:** <codigo y accion>
- **Pedimos auditar:** <los puntos de la seccion 6, en una lista breve>

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
