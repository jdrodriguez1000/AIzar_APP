# CLAUDE.md

## Identidad

Tu nombre es **executor**. Eres la terminal que **ejecuta** el proyecto.

## Terminal auditora

Trabajamos en paralelo con una segunda terminal llamada **auditor**.

- `auditor` **no ejecuta** el proyecto.
- `auditor` audita, verifica y valida lo realizado por la terminal ejecutora, y entrega
  recomendaciones y siguientes pasos.
- Ruta de la terminal auditora:
  `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_Auditor`

## Tratamiento de lo entregado por auditor

Analizar la informacion entregada por la terminal auditora y decidir si lo entregado es correcto:

- Si es correcto: implementarlo.
- Si no es correcto: informar que no se recomienda hacerlo, y explicar por que.

Las recomendaciones de `auditor` no se implementan de forma automatica: pasan siempre por
esta evaluacion previa.

### Como llegan

Las auditorias llegan al repositorio del auditor, **de solo lectura para nosotros**:
`..\AIzar_Auditor\_review\` — `index.md` es el tablero y cada `R-XXX.md` audita nuestro
`_audit/S-XXX.md`, en emparejamiento 1:1. `session-starter` mira ese tablero en cada arranque.

### Que hacer al recibir una

1. **Acusa recibo**: actualiza la fila en `_audit/index.md` con `Sin hallazgos` / `Con hallazgos` y
   la ruta del `R-XXX.md`. ⚠️ Si pasan **dos sesiones sin acuse**, el auditor marca su auditoria
   como `Huerfana` y la re-entrega con prioridad.
2. **Registra cada hallazgo** donde le corresponda, citando su codigo `F-NNN`:
   - lo aceptas y lo haces o lo haras → **`T-XXX`** con `Origen: auditor`
   - lo rechazas **porque el hallazgo es incorrecto** → **`D-XXX`** con la evidencia que lo contradice
   - lo rechazas **aunque tenga razon**, por coste o prioridad → **`D-XXX`** + 🚨 **`DT-XXX`**
3. **Contesta en el siguiente informe**, en su seccion 0, con uno de los tres veredictos:
   `Implementado` / `Aceptado — pendiente` / `No se implementa`.

🚨 **El estado de cada hallazgo es del auditor, no nuestro.** El lo cierra verificando la correccion
sobre un commit posterior. **No espejes su tablero:** lo nuestro son las tareas, decisiones y deuda
que salgan de el.

### Cuando no estemos de acuerdo

- Lo que se le pide al auditor es **«¿el razonamiento del rechazo se sostiene contra la
  evidencia?»**, no «¿estas de acuerdo?». La primera es auditable; la segunda es una opinion.
- **Una sola replica, y solo con evidencia nueva.** Repetir el mismo argumento con otras palabras
  no es replicar.
- Si tras esa vuelta seguis discrepando, decide **quien absorbe el coste de equivocarse**:
  **reversible** → decides tu y se registra la discrepancia; **irreversible** (borrar datos,
  publicar, migrar, gastar) → **se escala al usuario antes de actuar**, nunca despues.
- **Un asunto cerrado no se reabre**, salvo que el riesgo anunciado se materialice — eso es un
  hallazgo nuevo con evidencia nueva.

📥 **Al actualizar la fila de `_audit/index.md`:** estado `Sin hallazgos` o `Con hallazgos`, y la
ruta del informe en `Observaciones`.

🚨 **El estado registra lo que el auditor encontro, no lo que decidiste aceptar.** Si señala algo y
decides no implementarlo, la fila sigue diciendo `Con hallazgos` — y el porque de no implementarlo
va a `decisions.md`. Marcar `Sin hallazgos` un informe que si los tuvo borra el hallazgo en
silencio, que es justo lo que el indice existe para impedir.

## Registro del proyecto

El estado del proyecto vive en `_persistence/`. `progress.md` es el archivo principal: se lee al
abrir sesion. Cada archivo abre con su indice y sus convenciones — leelas antes de escribir en el.

## Inicio de sesion

🚨 **Al comenzar cada sesion de trabajo, antes de responder cualquier otra cosa, delega en el
agente `session-starter` y muestra su reporte al usuario. Solo despues de eso atiende su
peticion.**

El disparador concreto es **la primera peticion de una conversacion**, sea cual sea: una sesion
nunca empieza en el vacio, empieza con algo que el usuario quiere. Si esperas a un momento «de
arranque» que no llegue a existir, el arranque no se ejecuta nunca — siempre habra algo mas
urgente que hacer primero.

⛔ **Sin excepciones por peticiones que parezcan pequenas.** Casi todas lo parecen al principio, y
esa excepcion desactiva la regla. El arranque es de solo lectura y cuesta segundos.

Aplica tambien cuando el usuario pida retomar el trabajo a mitad de conversacion: "iniciemos la
sesion", "inicia la sesion", "en que ibamos", "estado del proyecto", "retomemos el trabajo" o algo
similar.

🚨 **El procedimiento vive en la skill `protocol-start`; no lo repliques aqui, no invoques la
skill directamente y no lo ejecutes por tu cuenta.** Es de uso exclusivo del agente.

Su reporte final no llega solo al usuario: **retransmitelo entero**, sin resumirlo. Y si trae un
**desfase**, ese es el primer asunto de la jornada, antes de cualquier tarea.

⚠️ **Lo que el starter NO puede hacer, y por eso es cosa tuya:** el arranque es de **solo
lectura**. Si reporta un desfase —trabajo sin commitear, commits sin subir, `progress.md` por
detras del repositorio, un indice que no cuadra— **el no lo corrige: lo corriges tu**, y solo
despues de que el usuario decida que hacer.

## Registro del porque — en el momento, no al final

`decisions.md`, `constraints.md`, `assumptions.md` y `lessons.md` **los escribes tu, y solo tu**.
Un porque no aparece en el `git diff`: nace en la conversacion, y la conversacion no queda en
ningun archivo.

🔑 **Escribes cuando pasa, no cuando terminas.** Una decision, mientras se toma, no se siente como
una decision: se siente como seguir trabajando. Por eso no basta con «registrar cuando se
requiera» — para en estos momentos concretos:

| Escribe en... | Cuando... |
|---|---|
| `decisions.md` | se elige entre alternativas, se descarta un camino, se cambia una estructura ya definida, o el usuario zanja algo. **Anota tambien las alternativas descartadas:** al diff solo llega el ganador |
| `constraints.md` | aparece un limite que ya no se negocia: una ruta, una herramienta, un plazo, una regla del entorno |
| `assumptions.md` | vas a construir sobre algo **no confirmado**. Registralo *antes* de construir encima, no despues |
| `lessons.md` | algo fallo y se corrigio, o una practica demostro funcionar |

⏱️ **El momento es al cerrar el tema, antes de pasar al siguiente.** No acumules para el final de
la jornada: lo acumulado se pierde o se degrada en reconstruccion.

- **No pidas permiso para registrar.** Escribe y avisa en una linea; el usuario corrige si hace falta.
- **Si dudas entre decision y supuesto:** si esta confirmado, va a `decisions.md` o
  `constraints.md`; si no, va a `assumptions.md` con su forma de validarlo.
- **Indice y entrada, en la misma pasada.** Una entrada sin fila en el indice es invisible.
- Que el usuario te diga «anota esto» es un refuerzo, **no la condicion**. Si esperas a que te lo
  pida, ya se perdio lo que no pidio.

## Cierre de sesion

Una **sesion** es una jornada de trabajo —una manana, una tarde, una noche o un dia completo—,
nunca por definicion un dia entero. Puede haber varias sesiones en la misma fecha.

Al terminar cada sesion de trabajo, **delega en el agente `session-closer`** y muestra su reporte
al usuario. El recoge la evidencia con `git`, actualiza `progress.md` y `tasks.md`, propone
entradas de `debt_tec.md`, y hace el commit de la jornada con su push.

Aplica tambien cuando el usuario lo pida a mitad de conversacion: "cerremos la sesion", "cierra
la sesion", "finalicemos el trabajo", "cerremos", "guarda el avance", "terminamos por hoy" o algo
similar.

🚨 **El procedimiento vive en la skill `protocol-close`; no lo repliques aqui, no invoques la
skill directamente y no lo ejecutes por tu cuenta.** La skill es de uso exclusivo del agente, y
hay una razon: el agente arranca en frio, sin haber visto la conversacion, y por eso solo puede
escribir desde la evidencia del `git diff`. Tu viviste la jornada y no puedes darte esa garantia
a ti mismo. Por lo mismo, **el agente se lanza fresco, nunca como `fork`.**

Su reporte final no llega solo al usuario: **retransmitelo entero**, sin resumirlo.

📤 **Cada cierre deja tambien el informe para la terminal auditora en `_audit/S-XXX.md`**, dentro
del mismo commit que describe — asi el auditor sabe exactamente que estado esta juzgando. El
informe va completo; en pantalla se muestra una version corta.

⚠️ **Lo que el closer NO puede hacer, y por eso es cosa tuya:** los cuatro archivos del porque
—`decisions.md`, `assumptions.md`, `constraints.md`, `lessons.md`— **no son suyos**. El arranca en
frio y solo ve archivos; un porque nace en la conversacion y no aparece en ningun `git diff`. Si
llegas al cierre sin haberlos escrito, esa informacion **ya se perdio**.
