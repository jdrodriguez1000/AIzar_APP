# decisions.md

> Registro de las **decisiones tomadas** en el proyecto.
> Cada decision tiene codigo `D-XXX` y se considera vigente hasta que otra la revoque.

---

## Indice

| Codigo | Decision | Fecha | Estado |
|---|---|---|---|
| [D-001](#d-001---modelo-de-trabajo-de-dos-terminales) | Modelo de trabajo de dos terminales | 2026-08-28 | Vigente |
| [D-002](#d-002---estado-del-proyecto-persistido-en-archivos) | Estado del proyecto persistido en archivos | 2026-08-28 | Vigente |
| [D-003](#d-003---las-recomendaciones-del-auditor-requieren-evaluacion-previa) | Las recomendaciones del auditor requieren evaluacion previa | 2026-08-28 | Vigente |
| [D-004](#d-004---indice-y-codificacion-en-todos-los-archivos-de-persistencia) | Indice y codificacion en todos los archivos de persistencia | 2026-08-28 | Vigente |
| [D-005](#d-005---control-de-versiones-con-git-y-remoto-en-github) | Control de versiones con git y remoto en GitHub | 2026-08-28 | Vigente |
| [D-006](#d-006---indices-por-ancla-sin-generador-mkindexpy) | Indices por ancla, sin generador `mkindex.py` | 2026-08-28 | Vigente |
| [D-007](#d-007---el-cierre-de-sesion-es-una-skill-sin-agente-propio) | El cierre de sesion es una skill, sin agente propio | 2026-08-28 | Revocada por D-008 |
| [D-008](#d-008---el-cierre-lo-ejecuta-el-agente-session-closer) | El cierre lo ejecuta el agente `session-closer` | 2026-08-28 | Vigente |
| [D-009](#d-009---una-sesion-es-una-jornada-no-un-dia) | Una sesion es una jornada, no un dia | 2026-08-28 | Vigente |
| [D-010](#d-010---el-porque-se-registra-en-el-momento-con-disparadores-explicitos) | El porque se registra en el momento, con disparadores explicitos | 2026-08-28 | Vigente |
| [D-011](#d-011---el-arranque-no-lee-al-auditor-hasta-que-t-005-defina-el-canal) | El arranque no lee al auditor hasta que T-005 defina el canal | 2026-08-28 | Revocada por D-018 |
| [D-012](#d-012---el-arranque-lo-ejecuta-el-agente-session-starter-con-haiku) | El arranque lo ejecuta el agente `session-starter`, con haiku | 2026-08-28 | Vigente |
| [D-013](#d-013---el-arranque-es-de-solo-lectura-y-bash-es-su-unica-frontera) | El arranque es de solo lectura, y `Bash` es su unica frontera | 2026-08-28 | Vigente |
| [D-014](#d-014---el-arranque-precede-a-la-primera-peticion-de-la-conversacion) | El arranque precede a la primera peticion de la conversacion | 2026-08-28 | Vigente |
| [D-015](#d-015---temporal-queda-fuera-del-repositorio) | `temporal/` queda fuera del repositorio | 2026-08-28 | Vigente |
| [D-016](#d-016---el-cierre-produce-un-informe-para-la-auditoria-anclado-al-commit) | El cierre produce un informe para la auditoria, anclado al commit | 2026-08-28 | Vigente |
| [D-017](#d-017---el-estado-de-cada-auditoria-vive-en-_auditindexmd) | El estado de cada auditoria vive en `_audit/index.md` | 2026-08-28 | Vigente |
| [D-018](#d-018---se-acepta-el-canal-de-vuelta-propuesto-por-el-auditor) | Se acepta el canal de vuelta propuesto por el auditor | 2026-08-28 | Vigente |
| [D-019](#d-019---la-seccion-0-es-un-contrato-auditable-fila-a-fila) | La seccion 0 es un contrato auditable fila a fila | 2026-08-28 | Vigente |
| [D-020](#d-020---el-eje-reversibleirreversible-funciona-a-criterio-hasta-que-exista-alcance) | El eje reversible/irreversible funciona a criterio hasta que exista alcance | 2026-08-28 | Vigente |
| [D-021](#d-021---los-datos-propios-del-proyecto-viven-solo-en-projectmd) | Los datos propios del proyecto viven solo en `PROJECT.md` | 2026-08-28 | Vigente |
| [D-022](#d-022---los-codigos-de-vertical-se-renombran-para-no-chocar-con-los-nuestros) | Los codigos de VERTICAL se renombran para no chocar con los nuestros | 2026-08-28 | Vigente |
| [D-023](#d-023---contractmd-del-auditor-se-adopta-como-contrato-vigente) | `contract.md` del auditor se adopta como contrato vigente | 2026-08-28 | Vigente |
| [D-024](#d-024---el-veredicto-de-los-gates-es-del-usuario) | El veredicto de los Gates es del usuario | 2026-08-28 | Vigente |
| [D-025](#d-025---la-trazabilidad-se-registra-por-declaracion-hacia-arriba-sin-indice-central) | La trazabilidad se registra por declaracion hacia arriba, sin indice central | 2026-08-28 | Vigente |
| [D-026](#d-026---las-etapas-son-las-de-vertical-y-000_preproject-es-su-unica-excepcion) | Las etapas son las de VERTICAL, y `000_preproject` es su unica excepcion | 2026-08-28 | Vigente |
| [D-027](#d-027---cada-fase-se-disena-antes-de-entrar-en-ella-con-esqueleto-fijo) | Cada fase se disena antes de entrar en ella, con esqueleto fijo | 2026-08-28 | Vigente |
| [D-028](#d-028---la-guia-transversal-se-copia-por-proyecto-con-sello-de-version) | La guia transversal se copia por proyecto, con sello de version | 2026-08-28 | Vigente |
| [D-029](#d-029---la-fuente-de-la-guia-se-congela-en-_globalsources-y-las-flechas-se-anclan-por-titulo) | La fuente de la guia se congela en `_global/sources/`, y las flechas se anclan por titulo | 2026-08-28 | Vigente |
| [D-030](#d-030---lo-que-aplica-de-la-guia-se-decide-con-dos-ejes-quien-construye-y-si-el-producto-llama-a-un-modelo) | Lo que aplica de la guia se decide con dos ejes: quien construye, y si el producto llama a un modelo | 2026-08-28 | Vigente |

---

## Convenciones

| Campo | Valores posibles |
|---|---|
| Codigo | `D-XXX`, correlativo, no se reutiliza |
| Estado | `Vigente` / `Revocada por D-XXX` |
| Decidido por | `usuario` / `executor` / `auditor` |

---

## Decisiones

### D-001 - Modelo de trabajo de dos terminales
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** definir el metodo de trabajo antes de iniciar el desarrollo.
- **Decision:** trabajar con dos terminales en paralelo — `executor` (ejecuta el proyecto) y
  `auditor` (audita, verifica, valida y entrega recomendaciones y siguientes pasos).
  `auditor` no ejecuta el proyecto.
- **Razon:** separar la ejecucion de la verificacion para tener control de calidad independiente.
- **Alternativas descartadas:** una sola terminal que ejecuta y se autoverifica.

---

### D-002 - Estado del proyecto persistido en archivos
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** la memoria de una sesion no sobrevive entre sesiones ni entre terminales.
- **Decision:** mantener el estado del proyecto en `_persistence/` con siete archivos:
  `progress.md`, `tasks.md`, `lessons.md`, `decisions.md`, `constraints.md`,
  `assumptions.md`, `debt_tec.md`.
- **Razon:** dar continuidad entre sesiones y una base comun auditable por `auditor`.
- **Alternativas descartadas:** un unico archivo de notas.

---

### D-003 - Las recomendaciones del auditor requieren evaluacion previa
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** `auditor` entrega recomendaciones y siguientes pasos.
- **Decision:** `executor` analiza cada entrega de `auditor` y decide si es correcta. Si lo es,
  la implementa; si no, informa que no se recomienda hacerlo y explica por que.
- **Razon:** `auditor` es una fuente de recomendaciones, no una autoridad de ejecucion.
- **Alternativas descartadas:** implementar automaticamente todo lo que indique `auditor`.

---

### D-004 - Indice y codificacion en todos los archivos de persistencia
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** leer un archivo completo para encontrar un dato es costoso y lento.
- **Decision:** cada archivo de `_persistence/` abre con un indice de busqueda rapida, y cada
  registro lleva codigo propio: `T-XXX` tareas, `D-XXX` decisiones, `C-XXX` restricciones,
  `A-XXX` supuestos, `L-XXX` lecciones, `DT-XXX` deuda tecnica.
  `tasks.md` y `debt_tec.md` llevan ademas estado, importancia y urgencia.
- **Razon:** permitir localizar informacion puntual sin recorrer el archivo entero.
- **Alternativas descartadas:** listas planas sin indice ni codigos.

---

### D-005 - Control de versiones con git y remoto en GitHub
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** el protocolo de cierre necesita una fuente de evidencia verificable de lo que
  cambio en cada sesion, y el trabajo necesita respaldo fuera de este disco.
- **Decision:** inicializar git en la rama `main` y enlazarlo al remoto
  `https://github.com/jdrodriguez1000/AIzar_APP.git`. `_persistence/` entra al repositorio a
  proposito: es la historia del proyecto.
- **Razon:** sin `git diff` el protocolo de cierre no tiene como distinguir un hecho de un relato.
- **Alternativas descartadas:** trabajar sin control de versiones y reconstruir el avance desde
  la memoria de la sesion.

---

### D-006 - Indices por ancla, sin generador `mkindex.py`
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** el protocolo de referencia exigia un script `tools/mkindex.py` para regenerar los
  indices de `_persistence/`.
- **Decision:** no crear ese script. Los indices de este proyecto son tablas con enlaces de ancla
  markdown; el protocolo de cierre incorpora en su lugar una comprobacion con `grep` que compara
  los codigos del indice con los de las entradas de detalle.
- **Razon:** aquel script existia porque en el proyecto de origen los indices llevaban **numeros
  de linea**, que se desfasan con cualquier edicion. Nuestras anclas no dependen de la posicion en
  el archivo, asi que no hay nada que regenerar. El riesgo real que queda es otro —una entrada sin
  fila en el indice, o al reves— y eso se detecta comparando codigos, sin necesidad de un script
  ni de una dependencia de Python.
- **Alternativas descartadas:** migrar los indices a numeros de linea y crear el generador.

---

### D-007 - El cierre de sesion es una skill, sin agente propio
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Revocada por D-008 |

- **Contexto:** el material de referencia traia un agente `session-closer` cuya unica funcion era
  invocar la skill del protocolo.
- **Decision:** no crear el agente. La skill `protocol-close` se invoca directamente.
- **Razon:** el procedimiento vive en la skill; el agente solo anadia una capa de indireccion.
- **Alternativas descartadas:** crear el agente `session-closer` en `.claude/agents/`.

---

### D-008 - El cierre lo ejecuta el agente `session-closer`
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** revision de D-007, que habia descartado crear el agente.
- **Decision:** crear el agente `session-closer` (`.claude/agents/session-closer.md`, modelo
  `sonnet`). La skill `protocol-close` pasa a ser **de uso exclusivo de ese agente**: ninguna otra
  sesion la invoca directamente. El agente responde a "cerremos la sesion", "cierra la sesion",
  "finalicemos el trabajo" y frases similares.
- **Razon:** el agente arranca **en frio**, sin haber visto la conversacion de la jornada. Eso no
  es una limitacion sino el mecanismo que hace cumplir la regla central del protocolo: quien no
  vio el relato solo puede escribir desde la evidencia. `executor`, que si vivio la conversacion,
  no puede darse esa garantia a si mismo.
- **Alternativas descartadas:** que `executor` invoque la skill directamente (D-007); lanzar el
  cierre como `fork`, que heredaria la conversacion y anularia la premisa anterior.
- **Revoca:** D-007.

---

### D-009 - Una sesion es una jornada, no un dia
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** el registro `S-XXX` de `progress.md` necesita una definicion precisa de que
  delimita una sesion.
- **Decision:** una sesion es una **jornada de trabajo** — una manana, una tarde, una noche o un
  dia completo. Puede haber **varias sesiones en la misma fecha**, cada una con su propio cierre
  y su propio `S-XXX`.
- **Razon:** asumir que una sesion es un dia haria que el control del protocolo se pudiera hacer
  por fecha, y entonces un segundo cierre del mismo dia daria verde con la jornada entera sin
  registrar. Por eso el criterio es el **id**, nunca la fecha.
- **Alternativas descartadas:** una sesion = un dia calendario.

---

### D-010 - El porque se registra en el momento, con disparadores explicitos
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** `decisions.md`, `constraints.md`, `assumptions.md` y `lessons.md` solo puede
  escribirlos `executor`, pero `CLAUDE.md` lo decia en negativo y dentro de la seccion de cierre.
- **Decision:** anadir a `CLAUDE.md` la seccion «Registro del porque», con la instruccion en
  positivo y una tabla de **disparadores concretos** por archivo, mas la regla de escribir al
  cerrar cada tema y sin pedir permiso.
- **Razon:** el fallo no es de voluntad sino de reconocimiento del instante — una decision,
  mientras se toma, se siente como seguir trabajando. Y leida dentro de la seccion de cierre, la
  instruccion solo llega cuando ya es tarde: la decision ocurrio horas antes.
- **Alternativas descartadas:** dejar que el agente de cierre escriba esos cuatro archivos, lo que
  convertiria el registro en reconstrucciones verosimiles indistinguibles de hechos; y depender de
  que el usuario pida «anota esto», que solo cubre lo que el usuario alcanza a notar.

---

### D-011 - El arranque no lee al auditor hasta que T-005 defina el canal
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Revocada por D-018 |

- **Contexto:** el protocolo de inicio de referencia traia un paso obligatorio que leia el tablero
  de la terminal auditora. Se comprobo en esta sesion que `AIzar_Auditor/` **esta vacia**: no hay
  tablero que leer, ni esta definido el canal por el que llegan sus hallazgos (A-001 / T-005).
- **Decision:** omitir ese paso en `protocol-start`, dejando escrito en la skill que hoy no se lee
  nada del auditor y que **no se debe inventar ese paso**. Se incorporara cuando T-005 defina el
  canal (tarea T-010).
- **Razon:** un paso obligatorio que apunta a un archivo inexistente tiene dos finales, los dos
  malos: el protocolo falla en cada arranque, o el agente rellena el hueco con lo que le parece.
  Y este protocolo existe justamente para no inventar.
- **Alternativas descartadas:** dejar el paso apuntando a una ruta que no existe; crear un tablero
  de auditoria vacio para que el paso no falle, que seria fabricar evidencia.

---

### D-012 - El arranque lo ejecuta el agente `session-starter`, con haiku
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** simetria con el cierre — un agente propio que ejecuta el protocolo de inicio.
- **Decision:** crear `session-starter` (`.claude/agents/session-starter.md`) con modelo `haiku`,
  unico autorizado a invocar `protocol-start`, y anadir a `CLAUDE.md` la seccion «Inicio de sesion».
- **Razon:** la tarea del arranque es leer, extraer campos y formatear — trabajo mecanico y
  barato, que no necesita el modelo grande.
- **Riesgo asumido y como se mitiga:** el reporte es lo unico que sobrevive de esa lectura, y con
  haiku sube el riesgo de que rellene huecos o suavice los estados. Se mitiga con tres reglas
  escritas en el agente: prohibicion de inventar repetida ahi (unica duplicacion deliberada
  respecto al skill), **transcribir los estados literalmente** sin parafrasear, y **citar archivo
  y codigo** en cada dato.
- **Alternativas descartadas:** `sonnet` para el arranque, mas caro sin ganancia clara en una
  tarea de extraccion; y que `executor` lea los archivos por su cuenta, que gasta el contexto que
  hara falta despues para trabajar.

---

### D-013 - El arranque es de solo lectura, y `Bash` es su unica frontera
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** `session-starter` no tiene `Write` ni `Edit`, pero si tiene `Bash`.
- **Decision:** declarar en el agente una **lista blanca** de comandos de lectura permitidos y una
  **lista negra** explicita (redirecciones, `rm`, `mv`, `cp`, `mkdir`, `touch`, y todo `git` que
  modifique). Los desfases que detecte los corrige `executor`, nunca el.
- **Razon:** quitar `Write` y `Edit` **no hace de solo lectura a un agente que tiene `Bash`**: una
  redireccion o un `git commit` bastan para escribir. La unica barrera real es la regla escrita,
  asi que tiene que ser explicita y enumerada, no una frase general.
- **Alternativas descartadas:** quitarle `Bash`, que le impediria leer `git` — y `git` es
  precisamente la fuente que distingue el hecho del relato.

---

### D-014 - El arranque precede a la primera peticion de la conversacion
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** `CLAUDE.md` decia «al comenzar cada jornada, delega en `session-starter`», sin
  fijar que va **antes** de atender lo que el usuario pida.
- **Decision:** el arranque se ejecuta **antes de responder cualquier otra cosa**, y el disparador
  concreto es **la primera peticion de una conversacion**. Sin excepciones por peticiones que
  parezcan pequenas.
- **Razon:** una sesion nunca empieza en el vacio, empieza con una peticion. Sin la precedencia,
  el arranque no se ejecuta nunca, porque siempre hay algo mas urgente. Y «al comenzar la jornada»
  no es un disparador detectable por `executor`, que no tiene reloj; «la primera peticion de la
  conversacion» si lo es.
- **Coste asumido:** el arranque puede dispararse sobre una peticion trivial. Es aceptable porque
  corre en `haiku`, es de solo lectura y cuesta segundos.
- **Alternativas descartadas:** atender primero y arrancar despues; y admitir excepciones para
  peticiones sencillas, que desactivarian la regla en la practica.

---

### D-015 - `temporal/` queda fuera del repositorio
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** `temporal/` es el area donde el usuario deja material en transito —hasta ahora, las
  skills y agentes de otros proyectos que sirvieron de guia—. Su contenido cambia o se borra sin aviso.
- **Decision:** anadir `temporal/` a `.gitignore`. No entra al repositorio.
- **Razon:** el repositorio es la historia del proyecto, y material de otros proyectos en transito
  no es parte de esa historia. Ademas evita arrastrar contenido ajeno a un repositorio que sube a
  GitHub. Lo que de ahi valga se traslada al proyecto adaptado, que es lo que se registra.
- **Alternativas descartadas:** versionar `temporal/` como archivo historico de lo que se uso de guia.

---

### D-016 - El cierre produce un informe para la auditoria, anclado al commit
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** la terminal auditora necesita saber que se hizo y que se propone como siguiente
  tarea para poder auditar. Se evaluaron dos vias: mostrar el informe en pantalla para copiarlo y
  pegarlo, o guardarlo en un archivo que el auditor lea.
- **Decision:** el cierre escribe **`_audit/S-XXX.md`** con el informe **completo**, un archivo por
  sesion, **antes del `git add`** para que entre en el mismo commit que describe. En pantalla se
  muestra ademas una **version corta**. Nuevo Paso 6b de `protocol-close`.
- **Razon:** el copiar-pegar deja la auditoria **sin ancla**: si lo informado solo existio en
  pantalla, al volver las observaciones no hay contra que contrastarlas — no se puede comprobar si
  se audito lo que se mando ni sobre que version. Con el informe dentro del commit, el auditor
  ejecuta `git log -1 -- _audit/S-XXX.md`, obtiene el hash y **verifica cada afirmacion contra el
  diff real** en vez de creersela. La auditoria pasa de opinable a verificable, y no cuesta un paso
  extra: aprovecha el commit que el cierre ya hace.
- **Detalle que hace util el informe:** lleva una seccion obligatoria **«Que pedimos auditar»** con
  nuestros propios puntos debiles. Un informe que solo cuenta lo bien que fue todo produce
  auditorias flojas, porque el auditor gasta su turno redescubriendo lo que ya sabiamos.
- **Alcance:** esto define el **canal de ida**. El de vuelta —como llegan sus observaciones— sigue
  abierto (A-001 / T-005), y se decidira despues de ver una auditoria real. Sigue rigiendo D-003:
  lo que venga del auditor lo evalua `executor` antes de implementarlo.
- **Alternativas descartadas:** mostrar el informe solo en pantalla para copiar y pegar; y
  escribirlo en un segundo commit posterior, que separaria el informe del estado que describe.

---

### D-017 - El estado de cada auditoria vive en `_audit/index.md`
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** con D-016 el cierre empezo a producir un informe por sesion, pero no habia forma de
  saber cual tocaba auditar. Decirle al auditor «lee el ultimo» falla en cuanto se acumulan varias
  sesiones sin auditar: auditaria uno e ignoraria el resto.
- **Decision:** crear `_audit/index.md`, indice de informes con estado por fila:
  `Pendiente` / `Sin hallazgos` / `Con hallazgos`, mas la ruta de las observaciones recibidas.
  `session-closer` anade la fila como `Pendiente` en el Paso 6b; `executor` escribe el veredicto
  cuando la auditoria vuelve. `protocol-start` reporta las filas `Pendiente` al arrancar.
- **Razon:** la pregunta util no es «cual es el ultimo informe» sino «cuales no se han auditado»,
  y esa se responde con un estado en su columna — el mismo patron de los siete archivos de
  `_persistence/`. Ademas deja registro de que se auditó y que no, que hasta ahora no existia en
  ningun sitio.
- **Regla que lo sostiene:** 🚨 **el estado registra lo que el auditor encontro, no lo que
  aceptamos.** Si señala algo y `executor` decide no implementarlo (D-003), la fila sigue diciendo
  `Con hallazgos`, y el porque del rechazo va a `decisions.md`. Lo contrario permitiria borrar en
  silencio un hallazgo incomodo.
- **Detalle heredado:** la fila no lleva el hash del commit, por la misma imposibilidad del Paso 4
  —se escribe antes del commit que la contiene—. Se obtiene con `git log -1 -- _audit/S-XXX.md`.
- **Alternativas descartadas:** un puntero `LATEST.md`, que se desfasa y solo apunta a uno; y que
  el auditor deduzca el id mas alto, que ignora las sesiones acumuladas sin auditar.

---

### D-018 - Se acepta el canal de vuelta propuesto por el auditor
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | executor, sobre propuesta de auditor |
| Estado | Vigente |

- **Contexto:** el auditor entrego en `AIzar_Auditor/_review/CANAL.md` una propuesta completa del
  canal de vuelta, que era lo unico que faltaba de A-001 y T-005. **Primera entrega del auditor**,
  asi que se evaluo segun D-003 antes de implementar nada.
- **Verificado antes de aceptar:** la carpeta `_review/` existe, es legible desde este repositorio,
  y su `index.md` esta creado y vacio — ninguna auditoria entregada todavia. No se acepto sobre el
  relato: se comprobo.
- **Decision: aceptado e implementado.** `_review/index.md` como tablero, `R-XXX.md` en
  emparejamiento 1:1 con nuestros `_audit/S-XXX.md`, anclados a nuestro commit y no a `HEAD`.
  Nuestro lado: Paso 1c en `protocol-start`, seccion 0 con tres veredictos en el informe, columna
  `Respondida en`, y las reglas de recepcion y desacuerdo en `CLAUDE.md`.
- **Razon:** el diseño es el espejo del nuestro y no introduce convenciones nuevas. Tres puntos
  suyos mejoran lo que nosotros habiamos propuesto:
  1. **`Aceptado — pendiente`** como tercer veredicto. Sin el, un hallazgo aceptado y aplazado no
     esta implementado ni rechazado: desaparece del radar. Nuestra tabla de dos veredictos tenia ese
     hueco.
  2. **El desempate por reversibilidad**, en vez de escalar siempre al usuario: si es reversible
     decide `executor`; si es irreversible se escala **antes** de actuar. Decide quien absorbe el
     coste de equivocarse, no quien argumenta mejor.
  3. **Un rechazo por coste sin su `DT-XXX` es, por si solo, un hallazgo.** Convierte nuestra regla
     de la deuda oculta en algo comprobable sin criterio: se mira si la entrada existe.
- **Reparto de autoridad, que es lo que evita el problema del espejo:** el estado de cada hallazgo
  `F-NNN` lo lleva el auditor en su `findings.md`, y solo el lo cierra, verificando sobre un commit
  posterior. Nosotros no copiamos esos estados: lo nuestro son las tareas, decisiones y deuda que
  salgan de ellos. Dos copias de la misma realidad se separan, y entonces hay que decidir cual miente.
- **Acuse de recibo:** actualizar nuestra fila en `_audit/index.md`. Vive en nuestro repositorio, asi
  que el auditor lo comprueba sin que nadie se lo cuente. Dos sesiones sin acuse y la auditoria se
  marca `Huerfana` y se re-entrega con prioridad.
- **Revoca D-011**, cuya condicion («hasta que T-005 defina el canal») ya se cumplio.
- **Alternativas descartadas:** que el usuario transporte las observaciones pegandolas, que no
  sobrevive a una sesion cerrada ni se puede releer despues; y espejar su tablero de hallazgos en
  nuestro `tasks.md`, que duplica estado y garantiza divergencia.

---

### D-019 - La seccion 0 es un contrato auditable fila a fila
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | executor, sobre notificacion de auditor |
| Estado | Vigente |

- **Contexto:** el auditor implemento en su lado las reglas del bucle que ya estaban acordadas
  (lectura de nuestra seccion 0, tabla de discrepancias que alguien escriba, y contador de replicas).
  Anuncia que no nos pide implementar nada nuevo.
- **Evaluacion (D-003):** correcto, y **sin embargo si cambiaba algo en nuestro lado**. La seccion 0
  pasa a auditarse fila a fila con tres exigencias —`Implementado` visible en el diff,
  `Aceptado — pendiente` con su `T-XXX` abierta, `No se implementa` con su `D-XXX`— mas la regla de
  que un hallazgo omitido no cuenta como contestado. Ninguna estaba escrita en `protocol-close`.
- **Decision:** escribirlas en el Paso 6b, donde las lee quien redacta la seccion 0.
- **Razon:** `session-closer` **no lee las conversaciones**: arranca en frio y solo tiene su skill.
  Una regla acordada en un mensaje y no escrita en el protocolo no existe para quien debe cumplirla.
  Es el mismo hueco que el auditor acaba de cerrar en su lado —acordado pero no implementado— y
  aparece aqui por la misma razon.
- **Regla que se anade y no teniamos:** la tabla va **completa**, con todos los hallazgos abiertos
  aunque no se tocaran esta sesion. La omision no significa nada, y por eso no puede usarse.
- **Alternativas descartadas:** confiar en que `executor` se lo recuerde al closer en el traspaso,
  que depende de que se acuerde justo esa jornada.

---

### D-020 - El eje reversible/irreversible funciona a criterio hasta que exista alcance
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** el desempate de una discrepancia depende de si el asunto es reversible o
  irreversible (D-018). El auditor señala que su inventario de acciones irreversibles esta **vacio**,
  porque poblarlo exige saber que hace el proyecto — y el alcance sigue sin definirse (T-004).
- **Decision:** aceptar que hasta entonces ese eje **se aplica a criterio**, diciendolo
  explicitamente cada vez que se use, en vez de presentarlo como la lectura de una tabla que no
  existe. Se crea T-015 para poblar nuestro lado del inventario cuando T-004 se cierre.
- **Razon:** la alternativa seria inventar ahora una lista de acciones irreversibles para un
  proyecto cuyo alcance no conocemos — es decir, adivinar. Un criterio declarado como criterio se
  puede discutir; un criterio disfrazado de tabla, no.
- **Consecuencia:** una razon mas, pequeña y real, para cerrar T-004.

---

### D-021 - Los datos propios del proyecto viven solo en `PROJECT.md`
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** al plantear como reutilizar este metodo en otros proyectos se midio cuanto habia
  atado a AIzar: 17 menciones —nombre, rutas absolutas, remoto— repartidas por las dos skills, los
  dos agentes y `CLAUDE.md`. Cambiar de proyecto obligaba a editarlas una a una, y olvidar cualquiera
  deja un protocolo apuntando al proyecto anterior.
- **Decision:** crear `PROJECT.md` en la raiz con la identidad, las rutas, el remoto, las carpetas y
  los codigos. Los protocolos, los agentes y `CLAUDE.md` **dejan de llevar datos dentro** y los leen
  de ahi: `protocol-start` en su Paso 1b (antes que nada, porque las rutas de los pasos siguientes
  salen de el) y `protocol-close` al empezar el Paso 1.
- **Razon:** separa **instrucciones** de **datos**. `CLAUDE.md` dice como se trabaja y `PROJECT.md`
  sobre que; lo primero es reutilizable tal cual y lo segundo se reescribe una vez por proyecto.
  Verificado despues del cambio: **cero menciones especificas** quedan en `.claude/` ni en `CLAUDE.md`.
- **Se aprovecho para quitar lo coyuntural**, que era el problema mas silencioso: tres sitios decian
  «el alcance de AIzar no esta definido (T-004)». Eso no describe al proyecto, describe **hoy**, y
  habria quedado mintiendo en cuanto T-004 se cerrara. Ahora la regla es condicional: comprueba si el
  alcance esta registrado y, si no lo esta, dilo.
- **Limite honesto:** esto es indireccion, no plantillas. No hay sustitucion automatica de variables:
  el agente lee `PROJECT.md` y usa lo que dice. La ganancia es un solo sitio que cambiar; el coste,
  un archivo mas que leer al arrancar.
- **Regla que lo mantiene util:** en `PROJECT.md` va **solo lo estable**. Lo que cambia cada jornada
  va a `progress.md`. Un archivo de identidad que hay que actualizar cada dia deja de ser fiable,
  porque nadie lo mantiene y todos lo siguen citando.
- **Alternativas descartadas:** meter los datos dentro de `CLAUDE.md`, que mezcla instrucciones con
  datos y obliga a editar el archivo de reglas en cada proyecto nuevo; y copiar y buscar/reemplazar
  en cada proyecto, que diverge en cuanto haya mas de dos.

---

### D-022 - Los codigos de VERTICAL se renombran para no chocar con los nuestros
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** al incorporar el metodo VERTICAL (`_methodology/000_method.md`) se comprobo su tabla
  de identificadores (§46) contra los codigos ya en uso. **Tres prefijos chocaban:**

  | Prefijo | En VERTICAL | Aqui | En `contract.md` del auditor |
  |---|---|---|---|
  | `F-` | Feature | — | **Hallazgo**, correlativo global |
  | `S-` | Scenario | **Sesion de trabajo** | **Sesion del ejecutor**, base del conteo de huerfanas |
  | `T-` | Task de una Vertical Slice | **Tarea del proyecto** | **Tarea** que cita `Aceptado - pendiente` |

- **Decision:** cambiar los codigos de **VERTICAL**, no los nuestros. Feature pasa a **`FT-`** y
  Scenario a **`SC-`** (§46.1). Con `T-` no se renombra: **se fusiona** en nuestra `T-XXX`, que gana
  un **origen obligatorio** — `VS-XXX` cuando nace del producto, otro valor cuando no (§46.2).
- **Razon del sentido del cambio:** nuestros prefijos estan en el historial de commits, en el
  mecanismo con que el auditor cuenta sesiones, y en un **contrato bilateral** que prohibe reutilizar
  codigos para que `F-012` siga significando lo mismo seis sesiones despues. Los de VERTICAL no
  estan escritos en ningun sitio todavia: hay **cero instancias**. Se cambia lo unilateral y gratuito,
  no lo bilateral y caro. Y la fuente `005 §27` los propone como recomendacion de forma, no como regla.
- **Por que `T-` se fusiona en vez de renombrarse:** dos prefijos distintos llamados los dos «tarea»
  es un choque que **no se ve** —el peor tipo—, porque no produce error: produce una lista con dos
  poblaciones y reglas distintas sin que nada lo señale. Un solo espacio con origen tipado lo evita.
- **Efecto sobre §47:** la refuerza. «Nada se construye sin una razon trazable» pasa de norma que hay
  que recordar a **campo que esta o no esta**: una tarea sin origen es la tarea huerfana que §47 manda
  cuestionar, y ahora se detecta mirando. Un origen distinto de `VS-XXX` no es una excepcion a §47,
  es su respuesta: la razon existe, solo que no es de producto — que es justo el caso del meta-trabajo
  de esta etapa (`T-017` no traza a ninguna necesidad porque no es producto).
- **Alcance:** cambia la **notacion**, no el metodo. La cadena de trazabilidad, su direccion y su
  regla siguen siendo las de §45 y §47. `N-`, `VS-`, `TC-` y `ADR-` estaban libres y entran sin tocar
  nada.
- **Queda registrado en el canonico** como **Anexo A.13**, y se paso por el criterio del propio
  documento —«¿restringe el diseño del producto, o solo este documento?»—: **no requiere ADR**. El
  mismo producto se construye igual se llamen `F-` o `FT-`.
- **Alternativas descartadas:**
  - **Renombrar los nuestros.** Obliga a reescribir el historial de commits, rompe el conteo de
    sesiones del auditor y toca un contrato bilateral, todo para acomodar codigos que aun no existen.
  - **Separar los espacios por carpeta** y confiar en el contexto —codigos de producto solo en los
    artefactos de producto—. No sirve: un codigo existe para poder citarse **fuera** de su archivo,
    y en un mensaje de commit o en un informe de auditoria no hay contexto que desambigue.
  - **Prefijar por dominio** (`P-F-001`). Resuelve la colision al precio de volver ilegible cada cita.

---

### D-023 - `contract.md` del auditor se adopta como contrato vigente
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | executor, con el usuario |
| Estado | Vigente |

- **Contexto:** al revisar el renombrado de `_review/CANAL.md` a `channel.md` se descubrio que el
  rename era lo de menos: `channel.md` se declara **superado por `contract.md`**, un archivo nuevo en
  la raiz del repositorio del auditor que reune el reparto de autoridad, los dos canales, el acuse de
  recibo, los tres veredictos, el desacuerdo y los codigos de ambos lados. **Nada nuestro apuntaba a
  el, y no lo habiamos leido.** Su propio encabezado dice: «un contrato que solo conoce una terminal
  no es un contrato: es una suposicion».
- **Evaluacion previa (D-003):** se leyo entero y se contrasto contra `CLAUDE.md` y `_audit/index.md`.
  **Sin contradicciones:** los tres veredictos, el umbral de dos sesiones para `Huerfana`, la replica
  unica con evidencia nueva, el eje reversible/irreversible y las cuatro columnas de nuestro indice
  coinciden con lo ya implementado. Se adopta porque **coincide**, no por venir del auditor.
- **Decision:** registrar `contract.md` en `PROJECT.md` como ruta, **con la version leida y
  verificada**, y declarar en `CLAUDE.md` que obliga a los dos lados.
- **Por que la version y no solo la ruta:** una ruta dice donde esta; no dice si lo que hay ahi sigue
  siendo lo que leimos. Va por la **version 1**; anotarla convierte «no nos enteramos de que cambio»
  en algo comprobable de un vistazo.
- **El contrato no pasa por la evaluacion de D-003 en cada uso.** Esa evaluacion es para lo que el
  auditor **propone**; el contrato es lo que ya esta **acordado**. Una clausula que nos parezca mal se
  discute como discrepancia, no se incumple en silencio.
- **Lo que NO se hizo, a proposito:** no se toco ninguna de las menciones historicas a `CANAL.md` en
  `_audit/S-003.md`, `decisions.md` (D-018) ni `progress.md`. Describen correctamente lo que paso ese
  dia, cuando el archivo se llamaba asi. Reescribirlas falsificaria el registro.
- **Duplicidad conocida, no resuelta:** las secciones 1 y 8 de `contract.md` repiten datos que ya
  viven en nuestro `PROJECT.md` —nombre, rutas, rama, remoto, carpetas, codigos—. Son dos copias de
  la misma realidad en repositorios distintos, que es el problema que D-021 existia para evitar. No se
  resuelve aqui porque **el archivo es del auditor y es de solo lectura para nosotros** (C-002):
  requiere acuerdo entre las dos terminales, no una edicion nuestra.
- **Alternativas descartadas:** copiar `contract.md` a nuestro repositorio, que crea una tercera copia
  que divergira; y no registrarlo, que deja la relacion entre terminales dependiendo de que alguien se
  acuerde de mirar un archivo ajeno.

---

### D-024 - El veredicto de los Gates es del usuario
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** el metodo VERTICAL exige en su §32 que el veredicto de un Gate lo emita alguien
  **independiente de la construccion** y **declarado antes de emitirlo**, pero deliberadamente no
  dice quien: manda que cada proyecto lo asigne «en la definicion operativa del proyecto que lo
  aplique». Esa casilla estaba vacia. Se rellena ahora porque **su valor caduca**: §32 avisa de que
  un veredicto cuyo dueño se decide al llegar al Gate se asigna sabiendo ya que resultado conviene.
- **El choque que aparecio al aplicarlo:** el candidato obvio era `auditor` —no construye, verifica
  contra evidencia, no depende de `executor`—, pero **contradice el contrato**: `contract.md` §2 dice
  que el auditor «mide y recomienda, **no tiene veto**», y un Gate es exactamente un veto, porque su
  resultado «No aprobado» significa detener.
- **La distincion que lo resuelve:** auditar y decidir no son la misma operacion aunque miren la
  misma evidencia. **Auditar** responde «¿esto se sostiene contra la evidencia?» — pregunta sobre la
  **verdad**, verificable. **Un Gate** responde «¿vale la pena gastar lo que viene despues?» —
  pregunta sobre la **inversion**, que depende de quien absorbe el coste de equivocarse.
- **Decision:** el Gate se parte en **tres actos**, y ninguno modifica el contrato:

  | Acto | Quien | Que hace |
  |---|---|---|
  | 1 · Evidencia | `executor` | Construye y registra la evidencia. **Nunca emite veredicto** |
  | 2 · Dictamen | `auditor` | Verifica criterio por criterio si la evidencia los sostiene. **No decide** |
  | 3 · Veredicto | **el usuario** | Decide `Aprobado` / `No aprobado` |

  Aplica a los dos Gates: el 1 (§28–§32, criterios en §29) y el 2 (§51).
- **Razon de fondo:** decide quien paga. `auditor` no asume la perdida ni sabe cuanto vale seguir o
  parar; pedirle esa decision seria pedirle una opinion disfrazada de dictamen. En cambio un dictamen
  contra los siete criterios de §29 es exactamente lo que ya hace con cada informe, sin tocar el
  reparto de autoridad.
- **Donde se escribio:** la asignacion en `PROJECT.md` —que es la «definicion operativa» que §32
  manda escribir fuera del canonico—, y la prohibicion de que `executor` emita veredictos en
  `CLAUDE.md`, incluida la version encubierta («esto ya esta listo para pasar el Gate» es un
  veredicto con otras palabras).
- **Rastro de cada veredicto:** una `D-XXX` en este archivo, con su campo `Decidido por`, mas su fila
  en `progress.md`. **No se crea codigo propio para los Gates:** un veredicto es una decision con
  fecha, alternativas y consecuencias, y `decisions.md` ya tiene esa forma. Inventar `G-XXX` añadiria
  un espacio de codigos que mantener a cambio de nada.
- **Alternativas descartadas:**
  - **`auditor` emite el veredicto.** Es lo mas literal respecto de §32, pero exige enmendar
    `contract.md` §2, que es **bilateral** y de solo lectura para nosotros (C-002): requiere negociarlo
    con la otra terminal, no editarlo. Y le pide una decision de inversion que no esta en condiciones
    de tomar.
  - **`executor` decide.** Es exactamente lo que §32 prohibe.
  - **No declararlo y resolverlo al llegar.** Es la opcion por defecto si no se hace nada, y es la que
    §32 señala como la peor de todas.
- **Consecuencia asumida:** el Gate deja de poder resolverse entre las dos terminales. **Requiere al
  usuario**, y por tanto puede esperar por el. Se acepta: una barrera de inversion que se puede
  atravesar sin que el que invierte se entere no es una barrera.

---

### D-025 - La trazabilidad se registra por declaracion hacia arriba, sin indice central
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** §45 del metodo exige recorrer la cadena `N → FT → SC → VS → T → TC` en las dos
  direcciones, y §47 prohibe construir sin razon trazable. **Ninguna de las tres fuentes dice donde
  se escribe el vinculo.** Una regla sin mecanismo no es comprobable: para poder cuestionar una tarea
  huerfana hay que poder **detectar** que lo es. Se resuelve ahora porque lo siguiente que produce el
  proyecto —las necesidades `N-XXX` de Descubrimiento (§14)— ya necesita sitio.
- **Decision, en una regla:** **cada elemento declara unicamente a su padre; nunca a sus hijos.** La
  necesidad es la raiz y no declara nada. `ADR-XXX` queda fuera de la cadena: cuelga de `ARCHIT`.
- **Por que una sola direccion:** un hijo conoce a su padre en el momento en que nace; un padre no
  conoce a sus hijos futuros. Escribir ambas crea dos afirmaciones sobre el mismo vinculo, y el dia
  que una cambie sin la otra hay que decidir cual miente.
- **Las dos direcciones de §45 se resuelven sin guardar nada:** hacia atras es una lectura encadenada
  (cada elemento lleva al siguiente); hacia adelante es una busqueda («¿quien declara a `N-001` como
  padre?»). Mecanico, sin criterio.
- **Efecto sobre §47:** pasa de norma a comprobacion. Una tarea huerfana deja de ser un juicio sobre
  si el trabajo «se justifica» y pasa a ser **un campo vacio o que apunta a algo inexistente**.
  Completa lo que la D-022 empezo con el `Origen` obligatorio de la tarea, que es el ultimo eslabon.
- **Carpeta:** `_product/`, cuarta pieza junto a `_methodology/` (**como** se construye),
  `_persistence/` (**como va** el trabajo) y `_audit/` (lo que entregamos a la auditoria).
  `_product/` es **que** se construye.
- **No se crean archivos todavia**, salvo el que haga falta. Descubrimiento solo produce las salidas
  de §14; el PRD, BDD, SPEC y ARCHIT nacen **despues** del Gate 1 (§33), y crearlos vacios ahora seria
  la documentacion anticipada que §6 y §39 mandan evitar. La carpeta se crea al entrar en
  Descubrimiento.
- **Alternativas descartadas:**
  - **Indice central de trazabilidad** (`traceability.md` con la cadena en una tabla). Comodo de leer
    y imposible de mantener: duplica cada vinculo. **Nuestro propio `_audit/index.md` ya lleva escrita
    esta leccion** — «no espejamos su tablero: dos copias de la misma realidad se separan, y entonces
    hay que decidir cual miente». Peor aun: la tabla es la que se lee y el elemento el que es cierto.
  - **Declarar en las dos direcciones.** Se lee mejor, pero admite contradiccion entre dos
    afirmaciones sobre el mismo vinculo.
  - **Meter el producto dentro de `_persistence/`.** Mezcla cosas con vidas distintas: el estado del
    trabajo se reescribe cada sesion, y una `N-001` debe seguir diciendo lo mismo dentro de dos años.
- **Registrado en el canonico** como **§47.1** y **Anexo A.14**, pasado por el criterio del propio
  documento: **no requiere ADR** — decide donde se escribe el vinculo, no que se construye.

---

### D-026 - Las etapas son las de VERTICAL, y `000_preproject` es su unica excepcion
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** `progress.md` viene usando `000_preproject` como etapa, un nombre nuestro que no
  existe en VERTICAL. Al incorporar el metodo habia que decidir si conviven dos nomenclaturas de
  etapas o una sola.
- **Decision:** **una sola, la del metodo** — `Descubrimiento → Prototipo → [Gate 1] → Product
  Baseline → WSLT → GRTH-NN → MVP → [Gate 2] → EVOL-NN`. `000_preproject` se conserva como **unica
  excepcion**, y al cerrarse **T-004** se entra en `Descubrimiento` y deja de usarse.
- **Por que `000_preproject` merece ser excepcion y no encajarse a la fuerza en `Descubrimiento`:**
  en ella no se construye producto, se monta la forma de trabajar. Llamarla `Descubrimiento` diria
  que el producto lleva cuatro sesiones avanzando, cuando lo que avanza es el andamio. Un nombre de
  etapa es una afirmacion sobre donde esta el producto.
- **Por que una sola nomenclatura y no dos en paralelo:** dos vocabularios para lo mismo obligan a
  traducir en cada informe y en cada auditoria, y la traduccion se hace mal tarde o temprano.
- **Donde vive:** el **vocabulario** en `PROJECT.md`, que es lo estable; **cual es la etapa de hoy**
  en `_persistence/progress.md`, que es lo que cambia.
- **Alternativas descartadas:** renombrar `000_preproject` a `Descubrimiento` retroactivamente, que
  falsea el registro de cuatro sesiones ya cerradas y auditables; y mantener una numeracion propia
  (`001_`, `002_`…) en paralelo a los nombres del metodo, que es la doble nomenclatura que esto evita.

---

### D-027 - Cada fase se disena antes de entrar en ella, con esqueleto fijo
| Campo | Valor |
|---|---|
| Fecha | 2026-08-28 |
| Etapa | 000_preproject |
| Decidido por | usuario |
| Estado | Vigente |

- **Contexto:** tras tres ajustes al metodo quedaban pendientes cuatro huecos mas —las salidas de la
  etapa Prototipo, la puerta ausente entre GRTH y MVP, la viabilidad hibrida sin dueño (§50.1) y la
  metrica del Gate 2 sin momento (A.6)—. El usuario propuso **no resolverlos ahora**, sino trabajar
  fase por fase entradas, salidas, procesos, agentes y flujo, y ajustar el metodo en ese momento.
- **Decision:** se acepta. **Los ajustes internos de una fase se hacen al definir esa fase**, no
  antes.
- **Razon:** es el propio metodo aplicado a si mismo. §6 y §39 mandan «definir suficientemente el
  futuro inmediato y no especular sobre el futuro lejano», y §59 exige proporcionalidad al
  esfuerzo. Diseñar las salidas del Prototipo **sin conocer el alcance** (T-004 sigue abierta) es
  exactamente el extremo de documentacion anticipada que §6 describe como riesgo. Ademas los agentes
  de una fase dependen del dominio: definidos antes de conocerlo, salen genericos.
- **Por que los tres ajustes ya hechos si tocaban ahora:** D-022, D-024 y D-025 **atraviesan todas
  las fases** —codigos, dueño de los Gates, trazabilidad— y no pertenecen a ninguna. Los que quedan
  son internos a una fase. El corte cae donde debe.
- **Condicion 1 — «al pasar a cada fase» significa ANTES de entrar.** La fase N se diseña al cerrar
  la fase N-1. Diseñada desde dentro, una fase no define lo que se exige: describe lo que salio. Es
  el mismo argumento que el metodo repite en §23, §32, A.6 y A.11.
- **Condicion 2 — el esqueleto se fija una sola vez, ahora.** Ocho secciones iguales para todas las
  fases (en `PROJECT.md`), porque ocho fases inventando cada una su estructura producen ocho
  documentos incomparables. La **seccion 7, criterio de cierre**, cubre de paso un hueco real del
  canonico: §41.1 avisa de que GRTH puede degenerar en Waterfall y §48 de que el MVP se estira, pero
  ninguna fase tiene criterio de terminacion. Exigirlo en cada definicion lo resuelve sin parchear el
  canonico fase por fase.
- **Donde viven:** `_methodology/phases/NNN_<fase>.md`. Esto mete contenido **propio del proyecto**
  dentro de una carpeta declarada agnostica, y queda anotado ahi mismo: `000_method.md` y `sources/`
  se copian a otro proyecto, `phases/` no. Es la segunda vez que aparece la frontera
  agnostico/propio, que sigue sin regla general (conversacion aplazada, sin decision).
- **Se aparcan dos hallazgos que NO dependen de ninguna fase**, para que no se pierdan: **T-018** (el
  criterio 6 de §29 es la pregunta del Gate puesta como requisito de si misma) y **T-019** (el
  principio sin nombre que el metodo repite en cinco sitios).
- **Alternativas descartadas:** resolver los cuatro huecos ahora, que especula sobre fases que estan
  a meses y sin alcance conocido; y aplazarlos sin fijar esqueleto ni momento, que es aplazar sin
  plan — y lo aplazado sin momento no se retoma, se olvida.

---

### D-028 - La guia transversal se copia por proyecto, con sello de version

- **Fecha:** 2026-08-28
- **Contexto:** `_global/guide.md` es un recetario transversal del **como** se hacen las cosas en
  cualquier proyecto de software. El archivo ordenaba copiarse a cada proyecto y adaptarse alli,
  pero su propia seccion 0 condena las segundas fuentes de verdad («envejece sin avisar»). El mismo
  argumento se aplicaba en un sitio y se ignoraba en el otro, con un agravante: dos documentos que
  un lector tiene delante se pueden ver discrepar; N copias en N proyectos no las ve nadie juntas
  nunca.
- **Decision:** se mantiene la copia por proyecto —**copia sellada**— y se le anaden las tres piezas
  que la hacen sostenible:
  1. **Sello de version.** La global lleva un numero (`VERSION 1`) que sube solo cuando cambia el
     fondo de una receta. Cada copia declara en cabecera de que version salio.
  2. **`_global/CHANGELOG.md`.** Una linea por version, la mas reciente arriba.
  3. **En la copia se borra y se anade, nunca se reescribe.** Una receta que se queda, se queda
     intacta; el aterrizaje al proyecto va en un bloque marcado debajo.
- **Razon:** el argumento a favor de copiar se sostiene —una guia compartida no se puede corregir
  sin romper a los demas, y una guia que no se corrige miente—. Lo que faltaba era **saber cuando
  una copia se quedo vieja**. El sello convierte esa comprobacion de «comparar 640 lineas a ojo» a
  «comparar dos numeros», y esa es la diferencia entre una comprobacion que se hace y una que no.
- **Por que la pieza 3 es la que sostiene las otras dos:** una frase distinta dentro de una receta
  puede ser una mejora local, una adaptacion al proyecto o texto viejo, y **las tres se ven igual en
  un diff**. Prohibiendo reescribir, cada diferencia tiene una lectura unica: lo que falta es poda,
  lo que sobra es aterrizaje, y lo que esta debe ser identico. De paso hace ejecutable la vuelta que
  la guia ya prometia: una correccion se hace **en la global** y baja a las copias, en vez de morir
  en el proyecto donde se encontro.
- **Coste asumido y aun sin dueno:** alguien tiene que comparar los dos numeros. Si ese momento no
  tiene sitio fijo, no ocurrira —es el mismo fallo que `RR-002` describe—. El candidato es el
  arranque de sesion, pero **no se decide aqui**: la guia dice que lo fija cada proyecto el dia que
  la copia.
- **Tambien en esta pasada:** se retira `lessons-global.md`, que la guia declaraba como su pareja y
  que **no se va a crear** (decision del usuario). El porque transversal ya viaja dentro de cada
  receta, asi que la retirada fue editorial: cabecera, la tabla de tres archivos del §0 —ahora dos—
  y el §1. El porque de un dia concreto sigue yendo al `lessons.md` del proyecto.
- **Alternativas descartadas:**
  - **Fuente unica compartida** (un solo archivo leido desde todos los proyectos): corrige una vez y
    vale para todos, pero **ningun proyecto puede podarla**, y un lector que aprende a saltarse
    secciones que no le aplican termina saltandose el archivo. Ademas corregirla pensando en el
    proyecto de hoy se la cambia a los demas sin mirarlos.
  - **Copia sin sello** (lo que habia): permite adaptar, pero la vuelta que el propio archivo promete
    —«sube y corrige esta»— no se puede ejecutar sin comparar el documento entero contra cada copia.
    Nadie lo hace, y la global se congela mientras las copias mejoran en secreto.
  - **Permitir reescribir en la copia y sincronizar despues:** es la version comoda, y es la que
    borra la distincion entre mejora, adaptacion y texto viejo. Sin esa distincion no hay
    sincronizacion posible.

---

### D-029 - La fuente de la guia se congela en `_global/sources/`, y las flechas se anclan por titulo

- **Fecha:** 2026-08-28
- **Contexto:** cada receta de `_global/guide.md` abre con una flecha `↳ GUIDE §N` a su origen. Ese
  `GUIDE` resulto ser `Edu_TripleS/GUIDE.md` (2.554 lineas, el manual del curso del que se destilo
  el recetario), pero **la ruta aparecia una sola vez y de pasada**, en el Anexo A. Tres problemas:
  en la maquina hay tres archivos llamados `GUIDE.md`; una copia de la guia en otro proyecto no
  tiene ese archivo al lado; y los numeros de seccion de un documento vivo **se mueven sin avisar**.
- **Decision:** tres cosas.
  1. **La fuente se congela dentro del repo**, en `_global/sources/GUIDE.md`, con cabecera de
     snapshot: fecha de la toma, «no se edita aqui», y la regla de precedencia (**si la fuente y
     `guide.md` discrepan, manda `guide.md`**).
  2. **La flecha se declara como procedencia, no como lectura obligatoria**, en la cabecera de
     `guide.md`. Una copia sin la fuente al lado **no esta rota**.
  3. **Las 13 flechas se anclan por titulo ademas del numero.**
- **Razon 1 - congelar mata el problema del renumerado.** Una fuente congelada no mueve sus
  secciones: `§8.l` significa lo mismo dentro de dos anos. Ademas **el patron ya existia en el
  proyecto**: `_methodology/000_method.md` guarda sus fuentes intactas en `sources/` con la misma
  regla de precedencia. `guide.md` vs `GUIDE.md` es a `_global/` lo que `000_method.md` vs
  `005_vertical.md` es a `_methodology/`.
- **Razon 2 - la declaracion cubre lo que congelar no cubre.** El manual son 2.500 lineas y **no
  viaja con las copias**. Sin declarar que la flecha es procedencia, en cada copia serian trece
  punteros rotos - y un puntero que promete lo que no cumple quema la confianza en los que si
  funcionan.
- **Razon 3 - el titulo se puede buscar, el numero no.** El propio indice de `guide.md` prohibe los
  numeros de linea porque «se desplazan y mienten sin avisar», y el archivo apuntaba trece veces a
  numeros de seccion de un documento vivo: **no se estaba aplicando a si mismo su regla**. Congelar
  lo resuelve hoy, pero el dia que se retome el snapshot los numeros vuelven a moverse; el titulo
  sigue siendo lo grepeable.
- **Por que `_global/sources/` y no `_methodology/sources/`** (que fue la propuesta inicial del
  usuario): `PROJECT.md` declara que `_methodology/` es **VERTICAL** - `000_method.md` y `sources/`,
  agnosticos, se copian tal cual. `GUIDE.md` no es VERTICAL ni es metodo; la propia guia dice «no
  es el metodo». Meterlo ahi difuminaba una frontera recien fijada y separaba la fuente de su
  destilado. Se copia el **patron**, no la carpeta.
- **Verificacion previa (`RR-003` aplicado a nosotros mismos):** antes de meter 2.554 lineas de un
  manual personal en un repo con remoto publico en GitHub se escaneo la fuente. Claves con formato
  de secreto: cero. Correos: cero. Rutas personales: dos lineas con la ruta de usuario de Windows,
  generica. Apto para subir.
- **No sube la version de `guide.md`:** sigue en 1. La v1 se creo hoy y **no existe ninguna copia
  todavia**, asi que no hay nada que pueda estar atrasado. Subir a v2 antes de que la v1 llegue a
  ningun sitio seria ruido en el `changelog.md`. Se anota dentro de la linea de la v1.
- **Alternativas descartadas:**
  - **Dejar las flechas apuntando a `Edu_TripleS/`:** depende de una carpeta externa que ni viaja
    con el repo ni esta bajo su control, y cuyo renumerado nadie detecta.
  - **Borrar las flechas:** es la trazabilidad hacia el padre que `CLAUDE.md` exige. Borrarlas deja
    doce recetas huerfanas.
  - **Una tabla de correspondencias receta-seccion:** seria un indice de trazabilidad, que
    `CLAUDE.md` prohibe explicitamente - dos afirmaciones sobre el mismo vinculo, y un dia divergen.
- **Queda fuera de alcance, por decision del usuario:** `Proyectos_TripleS/_global/guide.md` (el
  original del que salio esta copia) y `Proyectos_TripleS/RandomAI/_guide/GUIDE.md`. Los borra el.
  Se anoto que «no tenerlos en cuenta» no es un estado que el disco recuerde: mientras existan, un
  archivo que no debe usarse se ve igual que uno que si - y hoy costo una edicion en el equivocado.

---

### D-030 - Lo que aplica de la guia se decide con dos ejes: quien construye, y si el producto llama a un modelo

- **Fecha:** 2026-08-28
- **Contexto:** `_global/guide.md` tenia **tres niveles de condicionalidad y ninguno declarado**:
  recetas universales, `RR-008`-`RR-010` condicionales pero en el cuerpo y sin marca, y dos anexos
  condicionales con marca. El paso «borra lo que no aplica» del ritual de adaptacion quedaba a
  juicio de quien copiaba. El usuario aporto los tres tipos de proyecto que va a construir: (1) la
  sesion principal construye todo, sin API en produccion; (2) orquestador + workers, sin API en
  produccion; (3) orquestador + workers, con API en produccion.
- **Decision:** el criterio son **dos ejes independientes**, declarados en la guia y respondidos al
  copiarla:
  - **Eje A - quien construye:** una persona / una sesion de IA sola / orquestador + workers.
  - **Eje B - que se construye:** el producto llama a un modelo en produccion, si o no.
  Cada bloque condicional se marca con 🅰️, 🅱️ o 💻 (maquina), y lo sin marca es universal.
- **Por que dos y no uno:** son ortogonales. El caso 2 del usuario construye con agentes y entrega
  una aplicacion sin IA; existe tambien el simetrico —una persona escribiendo a mano un producto que
  si llama a un modelo—. Un solo eje no puede separar esos casos.
- **El hallazgo que motivo la particion del Anexo A.** Se titulaba «Solo si el proyecto usa modelos
  de lenguaje», y **sus seis entradas no caian todas del mismo lado**: los diez frenos del harness,
  el control de coste y la inyeccion de prompt son del eje A (construccion); TDD-frente-a-evals y
  la rubrica/juez son del eje B (producto). Con ese titulo, **un proyecto del caso 2 se saltaba el
  anexo entero** —«mi aplicacion no lleva IA»— y perdia justo los frenos y el control de coste que
  mas falta le hacen, porque va a tener un orquestador quemando tokens sin techo. Es el modo de
  fallo que `RR-004` describe: una advertencia mal partida no avisa a medias, **tranquiliza**.
  Se parte en **Anexo A (construccion)** y **Anexo B (producto)**; Windows pasa a **Anexo C**.
- **`RR-008` sube de categoria en vez de bajar.** El analisis previo lo daba por condicional y
  proponia moverlo a un anexo. **Era falso para los tres casos del usuario:** en el caso 1 el que
  teclea sigue siendo una IA, y el problema que la receta describe —la misma sesion escribe el
  codigo y sus pruebas— esta intacto. Se queda en el cuerpo, sin marca, y se corrige su primera
  frase: suponia que «el ciclo lo corre una persona», que en estos proyectos **no pasa nunca**.
  `RR-009` y `RR-010` si llevan 🅰️: dependen de que haya reparto de trabajo.
- **El proveedor no es un tercer eje**, y se dice explicitamente: los frenos, medir tokens antes de
  pagar y validar al juez se hacen igual contra Anthropic, OpenAI o quien sea. Saltarse una receta
  «porque eso es de Anthropic» es saltarsela por un motivo que no existe.
- **Los ejes se declaran ANTES de podar**, en el paso 2 del ritual, junto al sello. Declarados al
  final describen lo que se borro; declarados antes deciden que se borra. Es el mismo argumento que
  `RR-008` hace con el criterio y que `CLAUDE.md` hace con las fases.
- **Tambien:** la fila del §1 que mandaba abrir «`RR-008` a `RR-011`» cuando teclea un agente metia
  `RR-011` (entregar un hallazgo) en un grupo condicional al que no pertenece. Se parte en tres
  filas.
- **No sube la version:** sigue en 1, por lo mismo que en D-029 — la v1 aun no se ha copiado a
  ningun sitio.
- **Alternativas descartadas:**
  - **Un solo eje «¿interviene un modelo?»:** es la pregunta ambigua que ya causaba el fallo. Los
    casos 2 y 3 la responden «si» y necesitan cosas distintas.
  - **Mover `RR-008`-`RR-010` a un anexo** (la propuesta inicial del executor): habria mandado al
    anexo la receta que la propia guia llama «la mas importante del archivo», en proyectos donde
    aplica siempre.
  - **Dejar el Anexo A entero y solo aclarar su titulo:** no basta. El problema no es el titulo, es
    que dentro conviven dos conjuntos que se borran en momentos distintos.
