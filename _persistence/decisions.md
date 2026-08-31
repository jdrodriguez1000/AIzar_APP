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
| [D-031](#d-031---_global-se-declara-en-projectmd-y-se-versiona-entera-sin-exclusiones) | `_global/` se declara en `PROJECT.md` y se versiona entera, sin exclusiones | 2026-08-30 | Vigente |
| [D-032](#d-032---rr-003-baja-los-patrones-anclados-pero-no-los-comandos-de-shell) | `RR-003` baja los patrones anclados, pero no los comandos de shell | 2026-08-30 | Vigente |
| [D-033](#d-033---los-codigos-rr-nnn-los-asigna-solo-la-guia-global-y-nunca-se-reasignan) | Los codigos `RR-NNN` los asigna solo la guia global, y nunca se reasignan | 2026-08-30 | Vigente |
| [D-034](#d-034---el-recetario-no-aspira-a-cubrirlo-todo-se-le-pone-criterio-de-admision-y-entra-una-sola-receta) | El recetario no aspira a cubrirlo todo: criterio de admision y una sola receta nueva | 2026-08-30 | Vigente |
| [D-035](#d-035---la-cabecera-de-guidemd-no-lleva-fechas-y-1-nombra-su-unica-lectura-completa) | La cabecera de `guide.md` no lleva fechas, y §1 nombra su unica lectura completa | 2026-08-30 | Vigente |
| [D-036](#d-036---los-dos-hallazgos-de-r-002-se-aceptan-y-f-002-se-corrige-con-nota-de-reescritura-no-con-codigo-nuevo) | Los dos hallazgos de `R-002` se aceptan, y `F-002` se corrige con nota de reescritura, no con codigo nuevo | 2026-08-30 | Vigente |
| [D-037](#d-037---los-tres-hallazgos-de-r-003-se-aceptan-y-f-005-se-corrige-hacia-adelante-no-reescribiendo-d-018) | Los tres hallazgos de `R-003` se aceptan, y `F-005` se corrige hacia adelante, no reescribiendo `D-018` | 2026-08-30 | Vigente |
| [D-038](#d-038---los-cinco-hallazgos-de-r-004-se-aceptan-f-009-se-corrige-en-el-fondo-pero-no-reescribiendo-d-021) | Los cinco hallazgos de `R-004` se aceptan; `F-009` se corrige en el fondo pero no reescribiendo `D-021` | 2026-08-30 | Vigente |
| [D-039](#d-039---las-rutas-relativas-se-escriben-en-forma-canonica-posix-y-el-paso-1c-conserva-la-indireccion) | Las rutas relativas se escriben en forma canonica POSIX, y el Paso 1c conserva la indireccion | 2026-08-30 | Vigente |
| [D-040](#d-040---dos-ampliaciones-de-alcance-sobre-f-008-y-el-motivo-de-cada-una) | Dos ampliaciones de alcance sobre `F-008`, y el motivo de cada una | 2026-08-30 | Vigente |
| [D-041](#d-041---los-cinco-hallazgos-de-r-005-se-aceptan-f-015-se-acepta-como-regla-y-no-se-reescribe-nada) | Los cinco hallazgos de `R-005` se aceptan; `F-015` se acepta como regla y no se reescribe nada | 2026-08-30 | Vigente |
| [D-042](#d-042---el-dictamen-de-gate-se-registra-por-partida-doble-supuesto-y-tarea-y-la-mitad-bilateral-se-eleva) | El dictamen de Gate se registra por partida doble —supuesto y tarea—, y la mitad bilateral se eleva | 2026-08-30 | Vigente |
| [D-043](#d-043---se-acepta-el-rechazo-del-auditor-contractmd-seguira-duplicando-y-lo-que-se-construye-es-el-detector) | Se acepta el rechazo del auditor: `contract.md` seguira duplicando, y lo que se construye es el detector | 2026-08-30 | Vigente |
| [D-044](#d-044---la-marca-de-no-copiar-phases-se-aplaza-porque-presupone-la-regla-que-dt-002-no-ha-decidido) | La marca de no copiar `phases/` se aplaza porque presupone la regla que `DT-002` no ha decidido | 2026-08-30 | Vigente |
| [D-045](#d-045---la-deuda-gana-un-eje-propio-si-es-deuda-separado-de-si-esta-pagada) | La deuda gana un eje propio: «si es deuda», separado de «si esta pagada» | 2026-08-30 | Vigente |

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
  existe. Se crea T-016 para poblar nuestro lado del inventario cuando T-004 se cierre.
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
  atado a AIzar: 17 menciones —nombre y rutas absolutas— repartidas por **seis** archivos: las dos
  skills, los dos agentes, `CLAUDE.md` y `_audit/index.md`. Cambiar de proyecto obligaba a editarlas una a una, y olvidar cualquiera
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

#### 📌 Nota anexa — 2026-08-30 (S-012, `T-035`, hallazgo `F-009` de `R-004`)

⚠️ **Esta nota se escribio el 2026-08-30, no el 2026-08-28.** El cuerpo de arriba queda tal cual se
escribio: no se le incrusta un comando que en su dia no se anoto, porque eso convertiria «falta
evidencia» en «hay evidencia falsa» (`D-037`, `T-031`). Lo que sigue es una comprobacion **hecha
hoy**, y se declara como tal.

- **Que faltaba:** el cuerpo afirma «cero menciones especificas» y «17 menciones» sin decir **que se
  busco ni como se conto**. Una afirmacion de ausencia sin el instrumento registrado no distingue
  «no queda ninguna» de «no se busco bien».

- **El patron y su ambito**, tal como se usan: expresion `AIzar|Company_TripleS|github\.com`, acotada
  a `.claude/` y `CLAUDE.md`. **La unidad del conteo es la linea**, no la ocurrencia.

- **Ejecutado hoy sobre el arbol de trabajo:**

```
$ git grep -nE "AIzar|Company_TripleS|github\.com" -- .claude CLAUDE.md
--- exit: 1 ---
```

  `exit 1` sin lineas es el resultado correcto: cero coincidencias. La afirmacion del cuerpo **se
  sostiene hoy**, y ademas la reprodujo el auditor de forma independiente sobre `31e2ff7`.

- **Correccion factual al cuerpo:** donde dice «repartidas por las dos skills, los dos agentes y
  `CLAUDE.md`» —cinco archivos, que suman **16** lineas— son **seis**: los cinco mas
  `_audit/index.md`. El numero 17 era correcto; la enumeracion, no. Corregido en el cuerpo.

- **Por que importa el ambito y no solo el patron:** `AIzar` sobre el arbol entero da siempre
  positivos **legitimos** —`PROJECT.md`, que es su sitio por diseño; los informes `_audit/S-XXX.md`
  ya entregados, que por `D-018` no se reescriben; y el registro historico de `_persistence/`—. Un
  control que avisa de todo termina apagado. `.claude/` + `CLAUDE.md` es el unico ambito donde
  «cero» es la respuesta correcta. El control queda escrito en `T-037`.

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


---

### D-031 - `_global/` se declara en `PROJECT.md` y se versiona entera, sin exclusiones

- **Fecha:** 2026-08-30
- **Contexto:** al preparar el arranque de la auditoria pendiente (informes `S-002` a `S-006`) se
  reviso que afirma cada informe frente a lo que hay registrado. `S-006` describe la incorporacion
  de `_global/` —`guide.md`, `changelog.md` y `sources/GUIDE.md`, 3.438 lineas en el commit
  `eb17b6e`— pero la tabla «Carpetas propias» de `PROJECT.md` seguia listando cinco carpetas sin
  ella. Estaba anotado como **DT-003**, propuesto y sin confirmar. Quien leyera solo `PROJECT.md`
  —que es el registro estable, y lo unico que se lee al llevar el metodo a otro proyecto— no sabria
  que `_global/` existe. El usuario zanjo: declararla y cerrar la deuda.
- **Decision:** `_global/` entra en la tabla «Carpetas propias» de `PROJECT.md`, junto a
  `_methodology/`, con tres notas que fijan sus reglas propias: se copia por proyecto con sello de
  version y no se comparte (D-028), `sources/GUIDE.md` es de solo lectura (C-005), y **se versiona
  entera, sin ninguna exclusion en `.gitignore`**.
- **Por que se declara en `PROJECT.md` y no basta con `decisions.md`:** las reglas de la carpeta
  existian desde S-006, pero solo en `decisions.md` y `constraints.md` — archivos de historia, que
  se leen para saber **como se llego aqui**. `PROJECT.md` es el registro de **lo que hay**, y es el
  unico archivo que se copia y edita al llevar el metodo a otro proyecto. Una carpeta de primer
  nivel que no figura ahi es invisible para ese uso.
- **Por que ninguna exclusion en `.gitignore`:** la segunda mitad de DT-003 preguntaba si hacia
  falta alguna. Se verifico y **no**: los tres archivos son registro del proyecto, no material en
  transito. El contraste es `temporal/`, que si se excluye (D-015) precisamente porque es area de
  trabajo del usuario. Esa mitad de la deuda **se cierra por verificacion, no por edicion** — y por
  eso se deja escrito en `PROJECT.md`, para que la proxima lectura no vuelva a abrir la duda. Una
  comprobacion que no queda escrita se repite.
- **Alternativas descartadas:**
  - **Dejar DT-003 abierta hasta que tocara `_global/` otra vez:** era la posicion por defecto
    —deuda `Baja` y `No bloqueante`—, pero el coste de pagarla resulto ser de minutos, y el de no
    pagarla era concreto e inminente: un hallazgo casi seguro en la auditoria de `S-006`, que
    obliga a una vuelta completa del ciclo (hallazgo → `T-XXX` → correccion → verificacion sobre un
    commit posterior) para lo que aqui es una fila de tabla.
  - **Anadir `_global/sources/` al `.gitignore` por ser fuente congelada:** se descarto. Congelada
    significa de solo lectura (C-005), no fuera del registro. Excluirla haria que la copia de otro
    proyecto llegara sin la fuente de la que se destilo el recetario, que es justo lo que D-029
    quiso conservar.

---

### D-032 - `RR-003` baja los patrones anclados, pero no los comandos de shell
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Estado | Vigente |
| Etapa | 000_preproject |
| Origen | usuario |

- **Contexto:** punto 5 del analisis de nueve de `_global/guide.md` (S-006), registrado como
  **T-020**. La cabecera de la guia se declara «procedimientos, **ordenes concretas**, formatos», y
  la subseccion «Auditar el historial» de `RR-003` era la unica pieza que describia un
  procedimiento entero —tres barridos sobre el historial de git— **sin nada concreto que pegar**.
  La fuente congelada `sources/GUIDE.md` §2.b si tiene los comandos reales, en PowerShell.
- **Decision:** bajan a la receta **los patrones ya anclados** de los tres barridos, el porque de
  cada anclaje, y un aviso 💻 sobre la sensibilidad a mayusculas. **No bajan los comandos de
  shell.** `guide.md` sube a **VERSION 2** con su linea en `changelog.md`.
- **Por que el patron si y el comando no:** el patron es lo concreto *y* lo agnostico a la vez —el
  mismo regex vale en `grep`, en `Select-String` y en `rg`—, mientras que el comando ata la receta a
  un shell. Y es lo que de verdad faltaba: la receta exigia «ancla al **formato** del secreto:
  prefijo, longitud, mayusculas» sin ensenar ni un formato anclado. Nadie deriva
  `sk-ant-[A-Za-z0-9_-]{20,}` de esa frase, que es justo el fallo contra el que la propia receta
  avisa —un detector que no se sabe escribir no se escribe.
- **Por que esto no rompe el agnosticismo, y donde si se rompe:** son dos agnosticismos distintos y
  solo se toca uno. `RR-003` **ya asume git** en todo su cuerpo; lo que no asumia era **shell**, y
  sigue sin asumirlo. Lo unico dependiente de herramienta —la sensibilidad a mayusculas de
  `Select-String`— va marcado 💻, que es el marcador que la guia ya tiene para lo que depende de la
  maquina y no del proyecto.
- **Por que se edita el cuerpo de la receta, si eso esta prohibido:** la prohibicion de reescribir
  («En la copia se borra y se anade — nunca se reescribe») aplica a **las copias**, y esta es la
  **global maestra**. La guia manda justo lo contrario para este caso: una receta que deja de valer
  se corrige aqui, sube la version y se vuelve a copiar. Una correccion que solo viviera en un
  proyecto es una correccion que los demas nunca tendrian.
- **Alternativas descartadas:**
  - **Bajar el bloque de comandos literal de §2.b, marcado 💻:** maxima comodidad —se copia y se
    pega—, pero convierte una receta **universal** en una dependiente de la maquina, y `RR-003` es
    de las tres que se abren al montar cualquier proyecto. El marcador 💻 sobre la unica parte
    operativa de la receta la haria borrable en el ritual de copia (paso 3) por trabajar en otro
    sistema operativo, y con ella se iria la auditoria entera.
  - **Dejarlo en prosa y cerrar T-020 como deuda reconocida:** era la lectura estricta del
    agnosticismo, pero el agnosticismo que protegia ya estaba roto por git, y el coste de dejarlo
    era el fallo concreto que la fuente documenta: patrones improvisados que mienten. Se descarto
    porque no defendia nada real.
  - **Traer la anecdota medida de la fuente —las 21 coincidencias de `dem·ASIA·do`—:** se descarto
    por la regla de la propia guia: aqui no van numeros medidos en otra maquina. Se conserva solo el
    mecanismo (`ASIA` cae dentro de una palabra normal), que es lo que se traslada.

---

### D-033 - Los codigos `RR-NNN` los asigna solo la guia global, y nunca se reasignan
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Estado | Vigente |
| Etapa | 000_preproject |
| Origen | usuario |

- **Contexto:** punto 6 del analisis de nueve de `_global/guide.md` (S-006), registrado como
  **T-021**. La guia no decia si los codigos `RR-NNN` son estables, y tenia dos piezas que juntas
  formaban una trampa: el indice ensena a navegar con `grep -n "RR-007" guide.md`, y el ritual de
  copia manda **borrar** las recetas que no aplican. Nada impedia que un proyecto podara `RR-005` y
  renumerara lo que sigue.
- **Decision:** se anade a §1 la subseccion «Los codigos son estables, y un hueco es informacion».
  Los `RR-NNN` **los asigna la global y solo ella**; no se reasignan, no se renumeran, no se
  reutilizan aunque su receta se borre; un hueco es informacion, no un error; y **una copia nunca
  escribe un codigo que la global no tenga**. `guide.md` sube a **VERSION 3** con su linea en
  `changelog.md`.
- **Por que el fallo era peor que un enlace roto:** un `grep` renumerado no falla — **devuelve la
  receta equivocada con toda naturalidad**. Un puntero roto se ve y se arregla; uno que apunta a
  otro sitio se cree. Es el mismo argumento que la guia ya hace contra los numeros de linea en el
  indice: se desplazan y mienten sin avisar.
- **Por que un hueco es informacion y no un defecto:** `RR-005` ausente es la unica prueba de que
  se podo a proposito, y remite a la tabla de exclusiones. `RR-005` ocupado por otra receta no
  prueba nada y ademas miente. Renumerar borra la evidencia de la poda, que es justo lo que el paso
  4 del ritual existe para conservar.
- **El hueco que T-021 no cubria, y se cerro aqui:** la tarea pedia fijar la estabilidad, pero la
  guia tampoco decia si una copia puede **crear** un codigo nuevo. El ritual contempla borrar y
  anadir *aterrizaje* —un bloque marcado bajo una receta existente— y prohibe reescribir; una
  receta sin padre no cabe en ninguna de las tres. Se cierra con tres destinos: transversal → sube
  a la global; propio del proyecto → no es del recetario, va a la documentacion del proyecto;
  matiz de una receta existente → aterrizaje marcado.
- **Ademas se completaron las dos tablas de «En la copia se borra y se anade»,** que sin esas filas
  se leian como completas y no lo eran: «**Crear** una receta con un codigo nuevo → ❌ nunca», y
  «hay una receta que la global no tiene → **error**». Una tabla incompleta no avisa a medias:
  tranquiliza — el mismo fallo que `RR-004` documenta con su tabla de archivos peligrosos.
- **Alternativas descartadas:**
  - **Rango propio reservado para la copia (`RR-P01`, `RR-P02`…):** no colisiona con la global y
    permite alojar en `guide.md` algo con forma de receta pero no transversal. Se descarto porque
    hace convivir dos espacios de nombres en el mismo archivo, y entonces comparar copia contra
    global exige saber que rango se mira **antes** de juzgar la diferencia — justo lo que la regla
    de «cada diferencia tiene una sola lectura posible» quiere evitar. Y el caso que resolvia no
    existe: lo no transversal no pertenece a una guia que se declara agnostica.
  - **Dejar que la copia continue la numeracion (`RR-013`, `RR-014`…):** es lo que pasaria solo si
    no se dice nada, y reintroduce exactamente la colision que T-021 abrio para cerrar. Dos
    proyectos inventando su `RR-013` la misma semana producen dos recetas distintas con el mismo
    nombre, indistinguibles sin abrir las dos.

---

### D-034 - El recetario no aspira a cubrirlo todo: se le pone criterio de admision y entra una sola receta
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Estado | Vigente |
| Etapa | 000_preproject |
| Origen | usuario |

- **Contexto:** punto 7 del analisis de nueve de `_global/guide.md` (S-006), registrado como
  **T-022**. Para servir a «todo proyecto de desarrollo de software», el recetario tenia cinco
  huecos de cobertura del *como* transversal: convencion de commits y ramas, deshacer algo ya
  publicado, como entra una dependencia nueva, copias antes de una migracion, y que corre en CI.
  La tarea no era anadirlas: era decidir que entra y que se poda a cambio.
- **Verificacion previa:** se comprobo que los huecos **no venian de una destilacion infiel**. Lo
  que `sources/GUIDE.md` tiene y no bajo —§3 errores de Python, §4 plantillas del SDK, §5 elegir
  modelo, §13 TypeScript— esta fuera con razon: no es agnostico. Los cinco huecos salen de la
  ambicion de la cabecera, no de un olvido.
- **Decision:** entra **una sola receta**, `RR-013` («Como se deshace algo ya publicado»), y se
  escribe en §1 el **criterio de admision** que no existia («Que merece ser una receta»). Las otras
  cuatro quedan **aplazadas a T-004**, como candidatas. `guide.md` sube a **VERSION 4**.
- **Por que solo `RR-013`, y por que esa:** es la unica de las cinco que **no es especulacion hoy**.
  Este repositorio ya es publico y recibe un push por sesion, asi que el riesgo es vivo. Y `RR-003`
  ya la invocaba sin tenerla —«es mas barato rotar la credencial que reescribir historia
  publicada»— dejando una referencia colgante a un procedimiento inexistente; ahora esa frase
  apunta a `RR-013`.
- **Por que las otras cuatro se aplazan y no se descartan:** dependencias, migraciones y CI son
  recetas sobre un stack que todavia no existe —`T-004` sigue bloqueante y no hay una linea de
  producto escrita—. `CLAUDE.md` prohibe disenar lo lejano, y el propio metodo lo repite: lo que se
  define sin el sujeto delante no es una definicion. Escritas hoy describirian lo que imaginamos, y
  habria que corregirlas justo cuando ya se hubieran copiado a otros proyectos.
- **Por que un criterio de admision y no una regla de canje 1:1:** T-022 daba por supuesto que cada
  receta nueva se paga podando otra. Se descarto: un canje por numero obliga a **borrar algo util
  para pagar algo util**. El presupuesto real es el **indice** —«si deja de leerse de un vistazo, se
  poda antes de anadir»—, y lo que de verdad frena la acumulacion es un filtro de entrada, que la
  guia no tenia. Sus cuatro preguntas: transversal, falla en silencio, hay procedimiento que
  ensenar, y no esta ya dicho en otra receta.
- **El filtro que hace el trabajo es el segundo,** y es el que descarta «convencion de mensajes de
  commit»: importante, transversal y con procedimiento, pero **falla a la vista de todos y se
  arregla al momento**. `RR-003` existe por lo contrario. Ese filtro es tambien el orden de poda el
  dia que haya que podar: primero lo que falla ruidosamente.
- **Erratas corregidas de paso:** la tabla de §1 anunciaba «los **cuatro** momentos en que se abre»
  y listaba seis; se quita el numero y se anade el septimo (`RR-013`).
- **Alternativas descartadas:**
  - **Admitir las cinco ahora y podar lo que hiciera falta:** cerraba el hueco de una vez, pero
    cuatro de ellas se escribirian sin saber que se construye, y la correccion posterior llegaria
    con las copias ya repartidas — cada una con su subida de version. Se cambia trabajo barato de
    hoy por trabajo caro y publico de manana.
  - **Escribir solo el criterio y no admitir ninguna receta:** maxima contencion, pero dejaba viva
    la referencia colgante de `RR-003` a un procedimiento que no existe. Un puntero que promete lo
    que no cumple quema la confianza en los que si funcionan — argumento que la propia cabecera de
    la guia usa para las flechas `↳`.

---

### D-035 - La cabecera de `guide.md` no lleva fechas, y §1 nombra su unica lectura completa
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Estado | Vigente |
| Etapa | 000_preproject |
| Origen | executor |

- **Contexto:** puntos 8 y 9 del analisis de nueve de `_global/guide.md` (S-006), registrados como
  **T-023** y **T-024**. El primero pedia buscar rastros de fecha huerfana que hubiera dejado el
  cambio de «Ultima revision» al sello `VERSION N` + `changelog.md` (D-028). El segundo, resolver
  que §1 diga «nunca se lee entera» mientras el paso 3 del ritual exige leerla entera para poder
  podar.
- **Decision (T-023):** la cabecera pierde las fechas y queda en `**VERSION N**` a secas, con una
  nota que dice **por que** no lleva ninguna. Y el sello de la copia deja de traer valores
  concretos: pasa a marcadores, `versión <N>` · `el <AAAA-MM-DD>`.
- **Decision (T-024):** §1 nombra la excepcion en vez de contradecirse — **el dia que se copia si
  se lee entera**, es la unica lectura completa prevista, ocurre una vez por proyecto y termina con
  la guia podada y sellada.
- **El primer rastro lo introdujo esta misma sesion.** Al subir a VERSION 2 (D-032) se escribio
  `Creado: 2026-08-28 · Actualizado: 2026-08-30` en la cabecera. Eso es exactamente lo que T-023
  buscaba: una fecha que **duplica** lo que la linea del `changelog.md` ya dice, y que se queda
  vieja el primer dia que alguien sube la version y no la toca. Se detecto al hacer la revision
  especifica que T-023 pedia, que es el argumento a favor de que estas revisiones se hagan aunque
  parezcan de tramite.
- **El segundo rastro es peor de lo que parecia:** la plantilla del sello de copia traia
  `versión 7` · `el 2026-08-28`. La fecha era la de creacion de la guia pegada dentro de algo que
  se copia **verbatim**, asi que cualquiera que sellara su copia otro dia pegaria una fecha falsa.
  Y el `7` convivia con un numero de version real en la cabecera, invitando a confundirlos. La
  guia ya usa marcadores en todas sus otras plantillas (`<ejecutar el módulo>` en `RR-004`); esta
  era la excepcion, sin motivo.
- **Por que T-024 no se arregla ablandando la frase:** «casi nunca se lee entera» habria quitado la
  contradiccion y con ella la regla. La lectura de un vistazo es lo que hace utilizable el archivo;
  lo correcto es **nombrar la excepcion**, no diluir el principio. Y nombrarla paga algo extra: fija
  **contra que se mide el tamano** —contra ese unico dia, no contra el uso diario— que es
  justamente el criterio que D-034 acababa de dejar sin anclar.
- **Alternativas descartadas:**
  - **Dejar `Creado:` en la cabecera y quitar solo `Actualizado:`:** parecia inofensivo, pero la
    fecha de creacion tambien esta en el `changelog.md` — es la linea de la v1. Dos fuentes para el
    mismo dato es el problema que se estaba arreglando, no una version suave de el.
  - **Mover la excepcion de T-024 al ritual, junto al paso 3, en vez de a §1:** ahi la leeria solo
    quien ya esta copiando. La contradiccion la ve quien lee §1, y es en §1 donde tiene que
    resolverse.

---

### D-036 - Los dos hallazgos de `R-002` se aceptan, y `F-002` se corrige con nota de reescritura, no con codigo nuevo
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Estado | Vigente |
| Etapa | 000_preproject |
| Origen | auditor |
| Decidido por | executor |

- **Contexto:** primera auditoria entregada del proyecto, `R-002` sobre `_audit/S-002.md`
  (commit auditado `dced7b5`). Veredicto `Con hallazgos (2)`, ambos de severidad `Media` y
  `REVERSIBLE`. `CLAUDE.md` obliga a evaluar antes de implementar: no se aceptan en automatico.
- **Evaluacion de `F-001`** (el anclaje del informe en el commit no tiene comprobacion que pueda
  salir roja): **se acepta**. Se verifico sobre `HEAD` (`3228ca1`) y persiste: el bucle del Paso 2b
  recorre solo `_persistence/`, el Paso 7 solo mira secretos, y la linea del Paso 8 es una
  afirmacion fija mientras su hermana de justo encima ya tiene tres salidas. Va a **T-027**.
- **Evaluacion de `F-002`** (`A-001` reescrito en el sitio contra la convencion del propio
  archivo): **se acepta**. Parte del hallazgo caduco sola —`A-001` ya esta `Confirmado` con nota de
  cierre—, pero el fondo sigue: el enunciado anterior no se puede recuperar sin ir al `git log`,
  y `D-011` y `T-005` lo citan con el significado antiguo. Va a **T-028**.
- **La eleccion real, dentro de `F-002`:** el auditor ofrece dos remedios. Se elige el segundo
  —anadir a `A-001` la linea «reescrito en S-002; el enunciado anterior era X»— **porque `A-001` ya
  esta cerrado**. Partirlo ahora en `A-001` `Confirmado` + un codigo nuevo para lo que quedaba
  abierto describiria un estado que ya no existe: lo que quedaba abierto se cerro en `ec8e982`. La
  nota documenta el historico; el codigo nuevo lo reescribiria por segunda vez, que es el defecto
  que el hallazgo denuncia.
- **Alternativas descartadas:**
  - **Abrir `A-005` para la mitad que estuvo abierta y apuntar `T-005` ahi:** es la via que el
    auditor pone primera, y era la correcta **en `dced7b5`**. Hoy crearia un supuesto que nace
    cerrado, y obligaria a tocar `D-011` y `T-005`, dos entradas ya asentadas, para arreglar un
    problema de legibilidad que una linea resuelve.
  - **Rechazar `F-002` alegando que `A-001` ya esta `Confirmado`:** es cierto y es irrelevante. El
    hallazgo no es sobre el estado del supuesto, sino sobre que su enunciado anterior desaparecio
    del archivo que lleva los supuestos. Confirmarlo no lo devuelve.
  - **Corregir las dos cosas ahora mismo, sin pasar por tarea:** se descarta para que el auditor
    pueda cerrar cada hallazgo sobre un commit posterior identificable, con la evidencia que el
    mismo declaro en `R-002`.

---

### D-037 - Los tres hallazgos de `R-003` se aceptan, y `F-005` se corrige hacia adelante, no reescribiendo `D-018`
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Estado | Vigente |
| Etapa | 000_preproject |
| Origen | auditor |
| Decidido por | executor |

- **Contexto:** segunda auditoria entregada, `R-003` sobre `_audit/S-003.md` (commit auditado
  `ec8e982`). Veredicto `Con hallazgos (3)`: `F-003` `Media`, `F-004` y `F-005` `Baja`, los tres
  `REVERSIBLE`. Ninguna afirmacion del informe S-003 resulto falsa; los tres hallazgos son de
  **coherencia interna**.

- **Verificado antes de aceptar** — comando y salida, no la conclusion. Esta entrada **aplica ya la
  regla que `F-005` pide** (T-031), en la misma decision que la acepta:

  ```
  $ git log -1 --format="%H %ad" --date=iso -- _audit/S-003.md
  ec8e982238b992c18c7eecb9814a977951a6aba8 2026-08-28 11:58:07 -0500
  ```
  → el hash que `R-003` declara auditar **es** el que contiene nuestro informe. La auditoria juzga
  el estado que dice juzgar.

  ```
  $ git grep -l "D-020" -- .
  _audit/S-003.md
  _persistence/decisions.md
  _persistence/progress.md
  _persistence/tasks.md
  ```
  → `F-003` se sostiene en `HEAD`: **ningun archivo operativo** (`CLAUDE.md`, ninguna skill,
  ningun agente) cita `D-020`. La salvedad vive solo donde no se lee al aplicarla.

  ```
  $ git grep -n "Se crea T-015" -- _persistence/decisions.md
  _persistence/decisions.md:504:  existe. Se crea T-015 para poblar nuestro lado del inventario cuando T-004 se cierre.
  ```
  → `F-004` se sostiene en `HEAD`. Y `T-015` figura `Implementada` en el indice
  (`_persistence/tasks.md:26`), que es lo que convierte el error de referencia en una respuesta
  falsa para el lector futuro.

  ```
  $ cd ../AIzar_Auditor && git log -1 --format="%H %ad" --date=iso -- _review/R-003.md
  7abbe3c02d5b932f53f13166ce6edce62acfdd06 2026-08-30 17:24:46 -0500
  ```
  → el informe existe y esta commiteado en el repositorio del auditor, no es un archivo suelto.

- **`F-003` se acepta** → **T-029**. El hallazgo señala algo que ya nos habiamos dicho a nosotros
  mismos y no llevamos al sitio donde se usa. El parentesis «(borrar datos, publicar, migrar,
  gastar)» de `CLAUDE.md:64` **es** la tabla que D-020 prohibio, escrita en prosa.

- **`F-004` se acepta** → **T-030**. Trivial de arreglar y peor de lo que su severidad `Baja`
  sugiere en un aspecto: no manda al lector a un sitio vacio, lo manda a una tarea `Implementada`,
  y por tanto **le responde que si** a la pregunta que fue a hacer.

- **`F-005` se acepta** → **T-031**, con una precision sobre el **como**, que es la eleccion real de
  esta decision: **no se reescribe `D-018`**. El auditor lo formula en su evidencia de cierre —«una
  decision **futura** […] cuyo bloque de verificacion contenga la orden ejecutada y su salida
  literal»— y es lo correcto: editar `D-018` para que exhiba un comando que en su dia no se anoto
  seria fabricar la evidencia que el hallazgo echa en falta. El registro diria «se comprobo asi»
  cuando lo unico cierto es «se comprobo». La regla se escribe donde se lee y se aplica desde hoy.

- **Alternativas descartadas:**
  - **Anadir a `D-018` el comando reconstruido a posteriori:** lo mas tentador, porque el resultado
    era correcto y hoy se puede recrear. Se descarta por lo de arriba: un bloque de verificacion
    que no se ejecuto cuando dice haberse ejecutado es peor que su ausencia — el hallazgo pasaria
    de «falta evidencia» a «hay evidencia falsa», y esta vez sin nadie que lo note.
  - **Cerrar `F-003` solo en `CLAUDE.md`, sin tocar `protocol-close`:** es la mitad barata. Se
    descarta porque quien redacta materialmente un rechazo es `session-closer` en el Paso 6b, y ese
    agente **no lee `decisions.md` entero**: la regla tiene que estar en el archivo que el si lee.
  - **Rechazar `F-004` por trivial:** se descarta. La severidad `Baja` mide el daño, no la
    prioridad de arreglarlo; cuesta una palabra y el rechazo costaria una entrada en `debt_tec.md`
    mas larga que la correccion.

- **Sobre el aviso del auditor (renombrado `CANAL.md` → `channel.md`):** no es hallazgo y no
  requiere accion, pero **conviene devolverselo**: ya lo detectamos por nuestra cuenta en S-005 y lo
  resolvimos con `D-023`, dejando las menciones historicas intactas **a proposito**
  (`_persistence/decisions.md:622`, `_persistence/progress.md:245-246`, y `PROJECT.md:47` declara el
  renombrado). El auditor lo anota «para que exista fuera de esta conversacion»; existe desde hace
  cuatro sesiones, y decirselo le ahorra volver a levantarlo.

---

### D-038 - Los cinco hallazgos de `R-004` se aceptan; `F-009` se corrige en el fondo pero no reescribiendo `D-021`
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** llega `R-004`, que audita `_audit/S-004.md` sobre el commit `31e2ff7` y entrega
  cinco hallazgos: `F-006` y `F-007` (`Media`), `F-008` (`Media`), `F-009` y `F-010` (`Baja`). Los
  cinco son de la misma familia: la indireccion de `D-021` quedo con tres puntos donde apunta a un
  sitio equivocado, a un formato inutilizable o a nada, y el registro permanente conserva una cifra
  y una localizacion que no reproducen. La auditoria se hizo sobre `31e2ff7` y nuestro arbol ya
  avanzo hasta `fc21369`, asi que **cada hallazgo se verifico de nuevo contra `HEAD`** antes de
  aceptarlo.

- **Verificacion — ordenes ejecutadas y salida cruda.** Las salidas completas de cada comprobacion
  viven en la tarea de cada hallazgo (`T-032` a `T-036`); aqui va la que sostiene la aceptacion en
  bloque, porque es la que podia haber invalidado varios a la vez:

```
$ git grep -nE "AIzar|Company_TripleS|github\.com" -- .claude CLAUDE.md
--- exit: 1 ---
```

```
$ git grep -nE "T-[0-9]{3}|D-[0-9]{3}" -- .claude
.claude/agents/session-closer.md:61:(decision D-003). **Tu no haces esa evaluacion**: si aparece algo de la auditoria sin evaluar,
.claude/skills/protocol-close/SKILL.md:34:evalue y la considere correcta (decision D-003).
.claude/skills/protocol-close/SKILL.md:301:estan; no las reportes como pendientes. Ver `D-037` y `T-031`.
.claude/skills/protocol-close/SKILL.md:349:- **Cita siempre codigo y ruta** (`T-014`, `D-018`, `_persistence/tasks.md`). Son su unica via
.claude/skills/protocol-close/SKILL.md:373:| F-001 — <resumen> | Implementado | T-014, en este commit |
.claude/skills/protocol-close/SKILL.md:374:| F-002 — <resumen> | Aceptado — pendiente | T-015, `No implementada` |
.claude/skills/protocol-close/SKILL.md:375:| F-003 — <resumen> | No se implementa | D-018 |
.claude/skills/protocol-close/SKILL.md:417:hizo a criterio** (`D-020`), en la propia fila o en el `D-XXX` que cita: «reversible a criterio,
.claude/skills/protocol-close/SKILL.md:418:porque…». **No existe ningun inventario de acciones irreversibles**: esta vacio hasta que `T-016`
.claude/skills/protocol-close/SKILL.md:419:lo pueble, y `T-016` no puede cerrarse sin alcance (`T-004`).
.claude/skills/protocol-close/SKILL.md:423:unica vez que veras `D-020`: si el eje aparece en la tabla, la salvedad va con el.
.claude/skills/protocol-close/SKILL.md:522:todo el valor de D-016: sin el, el auditor recibe un relato que no puede contrastar contra ningun
.claude/skills/protocol-start/SKILL.md:17:otra por la tarde y otra por la noche **de la misma fecha** (decision D-009).
.claude/skills/protocol-start/SKILL.md:86:Es el **canal de vuelta** (D-018): una fila por auditoria entregada, apuntando a un `R-XXX.md` que
.claude/skills/protocol-start/SKILL.md:270:falta mencionarla, se dice *«`DT-003`, cancelada»* — nunca lo que decia cuando estaba abierta.
.claude/skills/protocol-start/SKILL.md:278:> Ya hay un caso real en este proyecto: `D-007` dice «no crear el agente `session-closer`» y esta
.claude/skills/protocol-start/SKILL.md:279:> **`Revocada por D-008`**, que decidio justo lo contrario.
--- exit: 0 ---
```

```
$ grep -n "C-002" _persistence/tasks.md _persistence/debt_tec.md
_persistence/debt_tec.md:68:  (C-002); resolverlo exige acuerdo entre las dos terminales, no una edicion unilateral.
--- exit: 0 ---
```

- **Decision:** aceptar los cinco hallazgos y abrir `T-032` a `T-036`, uno por hallazgo. Ademas, dos
  matices que no vienen del informe:

  1. **`F-008` se acepta con mas alcance del que describe.** El hallazgo senala una linea
     (`protocol-close/SKILL.md:349`); el `grep` de arriba muestra que la plantilla de la seccion 0
     (`:373-375`) tiene el mismo problema con `T-014`, `T-015` y `D-018`. Son **cuatro** lineas, no
     una. El resto de apariciones son citas de decisiones estructurales y no se tocan — el propio
     criterio de cierre del auditor las admite.

  2. **`F-009` se acepta en el fondo y se diverge en la forma.** El auditor pide «anadir a `D-021`
     una linea con el comando y su salida cruda». Eso choca de frente con `D-037` / `T-031`, que
     esta terminal escribio hace una sesion a peticion del propio auditor (`F-005` de `R-003`): una
     entrada antigua **no se reescribe** para que exhiba un comando que en su dia no se anoto. Asi
     que se hacen dos cosas distintas: la **correccion factual** (cinco archivos → seis) va en el
     sitio, porque es un error de hecho de la misma clase que `T-030`; y el **comando con su salida**
     se anexa como nota **fechada hoy y ejecutada hoy**, nunca incrustado en el cuerpo original como
     si se hubiera anotado el 2026-08-28.

- **Razon:** los cinco se verificaron contra `HEAD` y los cinco persisten; ninguno depende de que el
  arbol siguiera en `31e2ff7`. El caso de `F-009` no es una discrepancia con el hallazgo —el fondo
  es correcto y no se gasta replica— sino con su remedio literal: aplicarlo tal cual convertiria
  «falta evidencia» en «hay evidencia falsa», que es exactamente el dano que `D-037` existe para
  impedir. Cumplir la peticion del auditor rompiendo la regla que el mismo auditor nos hizo escribir
  seria obedecer la letra contra el proposito.

- **Clasificacion del eje:** los cinco se clasifican **`REVERSIBLE` a criterio** (`D-020`), porque
  el inventario de acciones irreversibles sigue vacio hasta que `T-016` lo pueble, y `T-016` no
  puede cerrarse sin alcance (`T-004`). El criterio aplicado: todos son ediciones de texto en
  archivos versionados de este repositorio, sin borrado de datos, publicacion, migracion ni gasto, y
  cada una se deshace con un `git revert`. Por eso decide esta terminal y no se escala al usuario.

- **Alternativas descartadas:**
  - **Aplicar `F-009` al pie de la letra, incrustando el comando en `D-021`:** lo mas comodo, porque
    cierra el hallazgo exactamente como el auditor lo pidio y el resultado del comando es correcto
    hoy. Se descarta por lo de arriba, y se le devuelve el razonamiento en la seccion 0 en vez de
    hacerlo en silencio.
  - **Aceptar `F-008` solo en la linea que el informe senala:** cierra el hallazgo con el criterio
    literal del auditor y cuesta la mitad. Se descarta porque dejaria tres lineas con el mismo
    defecto exacto a la vista en el mismo `grep`, y el proximo informe tendria que levantarlo otra
    vez.
  - **Cerrar `F-010` con una `DT-XXX` que acepte el duplicado** (opcion (b) del propio hallazgo):
    valida y mas barata. Se descarta porque `C-002` no necesita las rutas para cumplir su funcion
    —su contenido util es la restriccion— y mantener el duplicado no compra nada.
  - **Rechazar `F-006` alegando que la tabla ya cambio desde `31e2ff7`:** se descarta; se anadio la
    fila del contrato, no la del `findings.md`, y el hueco es el mismo.

- **Consecuencia:** `T-032` a `T-036` con `Origen: auditor`, mas `T-037` con `Origen: executor`,
  esta ultima nacida de la seccion 5.3 del informe —donde el auditor responde a nuestra pregunta
  sobre la regresion de `D-021`— y que **no es un hallazgo**: es iniciativa propia. Ninguna
  discrepancia, ningun `DT-XXX`, ninguna replica gastada.

- **Sobre el aviso del auditor** (las citas historicas a `CANAL.md` en `decisions.md:415`,
  `tasks.md:119` y `progress.md:128`): el mismo lo declara «ruptura nuestra, nada que corregir en su
  lado». Coincidimos y no se toca nada; ya se le respondio lo equivalente en `D-037`.

---

### D-039 - Las rutas relativas se escriben en forma canonica POSIX, y el Paso 1c conserva la indireccion
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** al implementar `T-033` (hallazgo `F-007` de `R-004`) habia que resolver dos cosas a
  la vez. (a) `PROJECT.md` ofrecia **dos formas** de la misma ubicacion —absoluta en «Repositorio del
  auditor», relativa con `\` en «Canal de vuelta»— sin declarar cual se usa en un comando; y la
  relativa, con separadores de Windows, **no resuelve en un shell POSIX**. (b) El bloque `bash` del
  Paso 1c habia dejado de ser una orden ejecutable.

- **Decision, en dos partes:**

  1. **Forma canonica: relativa, con `/`, desde la raiz de este repositorio.** Es la unica valida
     para citar un archivo del auditor, y queda declarada en la propia tabla **Rutas** de
     `PROJECT.md`. Las dos absolutas se conservan como **excepcion declarada**: nombran donde vive
     cada repositorio en esta maquina, no sirven para navegar entre ellos.
  2. **El Paso 1c conserva la indireccion** —opcion (b) de las dos que ofrecia el hallazgo— en vez
     de llevar la ruta escrita dentro. Se refuerza con tres cosas: la orden a pegar literal, la
     prohibicion explicita de traducirla o reconstruirla de memoria, y **un bloque obligatorio
     «Tablero del auditor» en el reporte del Paso 3**, que nunca se omite.

- **Razon de la parte 1:** `/` funciona igual en Bash y en PowerShell; `\` solo en uno de los dos, y
  este proyecto usa ambos. Escribir la ruta **tal como se pega en un comando** es lo que convierte
  la indireccion en algo que se copia en vez de algo que se traduce.

- **Razon de la parte 2, que es la que costo:** la opcion (a) del hallazgo —poner
  `cat ../AIzar_Auditor/_review/index.md` en el bloque— es mas comoda y **se llego a escribir**;
  luego se revirtio. Reintroduce el nombre del auditor dentro de `.claude/`, que es exactamente lo
  que `D-021` vacio, **decidida por el usuario**. Habria hecho fallar el control de `T-037` en su
  primer dia, y deshacer de pasada una decision del usuario para cerrar un hallazgo de severidad
  `Media` no es un intercambio que corresponda hacer a esta terminal por su cuenta.
  El hallazgo ofrecia las dos opciones como igual de validas; se toma la que no crea el conflicto.

- **Lo que no arregla la parte 2, y por eso hace falta la tercera pieza:** con indireccion pura, el
  Paso 1c sigue exigiendo interpretar antes de correr, y su fallo es **silencioso** —saltarselo
  producia exactamente el mismo reporte que hacerlo—. Por eso el bloque obligatorio del Paso 3: **no
  hace el paso mas facil, hace su omision visible**, que es lo unico que un protocolo escrito puede
  garantizar de verdad.

- **Alternativas descartadas:**
  - **Opcion (a) del hallazgo, ruta escrita en el bloque:** descartada por lo de arriba. Tiene una
    ventaja real que conviene no ocultar —al copiar el metodo a otro proyecto, `cat` fallaria
    **ruidosamente**, mientras que la indireccion mal resuelta falla en silencio—, y aun asi pesa
    menos que revertir `D-021`.
  - **Adoptar el separador `\` como canonico** y marcar los bloques como `powershell`: descartada;
    ataria los protocolos a un shell concreto sin ganar nada.
  - **Un comando que extraiga el campo de `PROJECT.md` con `grep`/`sed`:** indireccion de verdad
    ejecutable, pero fragil ante cualquier cambio de formato de la tabla, e ilegible. El coste de
    depurarlo supera el del paso manual.

- **Consecuencia:** `PROJECT.md` gana la declaracion de forma canonica y la fila «Estado de los
  hallazgos» (`T-032`); `protocol-start` gana el bloque obligatorio del reporte. Ambas rutas nuevas
  se comprobaron ejecutandolas:

```
$ ls -la ../AIzar_Auditor/_persistence/findings.md
-rw-r--r-- 1 USUARIO 197121 11534 Aug 30 21:32 ../AIzar_Auditor/_persistence/findings.md
$ cat ../AIzar_Auditor/_review/index.md | head -3
# _review/index.md

> Tablero de las auditorias realizadas, con su estado y el de sus hallazgos.
```

---

### D-040 - Dos ampliaciones de alcance sobre `F-008`, y el motivo de cada una
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** `F-008` señala **una** linea de `protocol-close/SKILL.md` con codigos vivos de este
  proyecto usados como ejemplo. Al ir a corregirla, el mismo `grep` que la localiza muestra mas.

- **Decision:** corregir **cuatro** lineas en vez de una, y ademas una quinta que el patron del
  hallazgo no alcanzaba:

  1. `:349` — la que el hallazgo cita (`T-014`, `D-018` como ejemplo de «cita codigo y ruta»).
  2. `:373-375` — **ampliacion**: la plantilla de la seccion 0 del informe usa `T-014`, `T-015` y
     `D-018`. Es el mismo defecto exacto, en el mismo archivo, visible en la misma salida.
  3. `| Rama | main |` en la cabecera de la plantilla del informe — **ampliacion propia**: `main` es
     un dato de `PROJECT.md` («Rama principal») escrito dentro de un protocolo. El patron de `F-008`
     buscaba codigos `T-`/`D-` y no podia verlo; el patron de `F-009` busca nombre, rutas y remoto y
     tampoco. Cae exactamente entre los dos controles.

- **Razon:** corregir solo la linea citada dejaria tres con el defecto identico a la vista en la
  misma salida del `grep`, y el proximo informe tendria que levantarlas otra vez. El criterio de
  cierre que el propio auditor propone para `F-008` —«que solo aparezcan codigos genericos o citas
  de decisiones estructurales»— no se cumpliria arreglando una sola.

- **Lo que NO se toca, y por que:** las demas apariciones (`D-003`, `D-009`, `D-016`, `D-018`,
  `D-020`, `D-037`, `T-016`, `T-031`, `T-004`, `D-007`/`D-008`, `DT-003`) son **citas de decisiones
  estructurales**, no ejemplos ilustrativos: explican por que una regla es como es. El criterio de
  cierre del auditor las admite expresamente. Borrarlas dejaria las reglas sin su porque, que es
  peor que el problema.

- **Sobre `| Rama | main |`:** se sustituye por «la rama principal, segun `PROJECT.md`». Se anota
  aqui porque es la tercera fuga que aparece **despues** de que `D-021` declarara el barrido
  completo, y las tres se encontraron con controles distintos. **Ningun control de los dos que
  tenemos la habria detectado**: es un aviso sobre el alcance de `T-037`, no una tarea nueva.

- **Alternativa descartada:** limitarse al alcance literal del hallazgo y abrir una tarea aparte
  para el resto. Se descarta porque la correccion es la misma edicion, en el mismo archivo, y
  trocearla solo produce una tarea mas que seguir.

---

### D-041 - Los cinco hallazgos de `R-005` se aceptan; `F-015` se acepta como regla y no se reescribe nada
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** llega `R-005`, tercera auditoria recogida y **quinta entregada**, sobre `S-005`
  (commit `e9216f6`, del 2026-08-28). Veredicto **Con hallazgos (5)**: `F-011`, `F-012`, `F-013`
  (`Media`), `F-014`, `F-015` (`Baja`). El auditor contrasta 28 afirmaciones del informe y 23 se
  sostienen; ninguno de los cinco hallazgos toca la sustancia de la sesion —el canonico entra
  entero, el renombrado `F-`/`S-` a `FT-`/`SC-` no deja residuos, `_product/` no existe porque asi
  se declaro—. **Los cinco tocan el registro que debe sobrevivir a la sesion.**

- **Decision:** los cinco se **aceptan**, cero rechazos. Cuatro se implementan en el acto (`T-038`,
  `T-040`, `T-041` y, en su parte registrable, `T-039` con `A-005`); `F-015` se acepta de otra
  forma, ver abajo.

- **Que se verifico antes de aceptar:** los cinco contra `HEAD` (`57f3f2a`), no contra el commit
  auditado. Cuatro **persisten**; cada uno lleva su orden y su salida cruda en su `T-XXX`. El
  quinto, `F-015`, **ya no persiste** — y por eso se decide aparte.

- **Sobre `F-015`, y por que no se corrige nada:** el hallazgo dice que el numero de decisiones de
  `S-005` no coincide en los tres sitios donde se escribio —«cinco» en el informe, «cinco» en el
  mensaje del commit, «cuatro» en `progress.md`, seis en el diff—. Comprobado:

  ```
  $ git show e9216f6:_persistence/progress.md | sed -n '50p'
  ajusto contra el vocabulario propio en cuatro decisiones: **D-022** renombra Feature y Scenario a
  --- exit: 0 ---
  ```

  ```
  $ grep -n "decisiones" _persistence/progress.md | grep -i "cuatro\|cinco\|seis"
  --- exit: 1 ---
  ```

  La linea 50 era la fila **«Avance de la etapa»**, que se reescribe cada sesion: se sobrescribio
  sola. El bloque historico de `S-005` enumera las seis decisiones **sin declarar numero**. En el
  registro vivo **no queda cifra que corregir**.

  Las otras dos cifras viven en `_audit/S-005.md` y en el mensaje de `e9216f6`: **inmutables por
  `D-018`**. Se **descarta** reescribirlas, y no por pereza — hacerlo convertiria «hubo un error de
  conteo» en «no hubo ningun error», que es la falsificacion que `D-037` y `L-007` prohiben. El
  propio auditor formula su criterio de cierre hacia adelante, no hacia atras.

  Lo que queda de `F-015` es entonces **una regla, no una correccion**: en los informes siguientes
  **el numero sale de la enumeracion y no se escribe aparte**. Un numero escrito a mano al lado de
  una lista es una segunda afirmacion sobre el mismo hecho, y un dia diverge — es el mismo argumento
  con el que el metodo prohibe el indice de trazabilidad.

- **Reversibilidad:** los cinco son `REVERSIBLE`, y **lo clasifico asi a criterio** —son ediciones
  de texto en archivos versionados, deshacibles con un `git revert`—, no leyendolo de una tabla: el
  inventario de acciones irreversibles sigue vacio hasta que `T-016` lo pueble, y `T-016` no puede
  cerrarse sin alcance (`T-004`). Coincide con la clasificacion del auditor, que la declara igual.

- **Alternativa descartada:** aplazar los cuatro implementables hasta despues de `T-004`. Se
  descarta porque **ninguno depende del alcance** —los cuatro tocan registro y protocolo, no
  producto— y porque `F-013` protege el unico documento que obliga a las dos terminales: dejarlo
  esperando a una tarea bloqueada indefinidamente es dejarlo sin fecha.

---

### D-042 - El dictamen de Gate se registra por partida doble —supuesto y tarea—, y la mitad bilateral se eleva
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** `F-012` señala que `D-024` reparte el veredicto de un Gate en tres actos y da por
  hecho que el acto 2 —el dictamen del auditor— tendra donde escribirse, cuando `contract.md` §4
  define **una sola** forma de entrega: un `R-XXX.md` que audita un `S-XXX.md`, 1:1. El riesgo se
  detecto en `S-005` y se declaro explicitamente **no registrado**: vivia solo en el informe de esa
  jornada.

- **Decision:** registrarlo en **dos sitios**, no en uno. El auditor ofrecia «un `A-XXX` **o** una
  `T-XXX`»; se hacen los dos, y no por exceso de celo:

  - **`A-005`** en `assumptions.md`, porque lo que hay es un **supuesto sobre el que ya se
    construyo**: `D-024` esta escrita en `PROJECT.md` y en `CLAUDE.md` y se da por vigente. Eso es
    literalmente lo que `assumptions.md` existe para llevar, y lo que le da ciclo de vida —se
    confirma o se refuta—.
  - **`T-039`** en `tasks.md`, porque la validacion **no la podemos hacer nosotros** y por tanto es
    trabajo con dueño y momento, no una espera.

  Un supuesto sin tarea no se resuelve solo; una tarea sin supuesto pierde el registro de que
  estamos construyendo sobre arena. Separarlos no duplica: cada uno responde una pregunta distinta.

- **Disparador, y por que ese:** **al diseñar la fase Prototipo**, cuando el Gate 1 entra en el
  horizonte. Se **descarta** resolverlo ahora: diseñar hoy el formato del dictamen es exactamente la
  especulacion que `D-027` prohibe, y el auditor coincide («anticiparlo no urge; registrarlo si»).
  Se **descarta** tambien dejarlo sin disparador, que es como llego el hallazgo.

- **Lo que se eleva al usuario, y por que no lo decido yo:** el acto 2 **asigna al auditor una
  funcion que su contrato no le da**. `contract.md` obliga a los dos lados y **no se cambia por un
  lado**; `CLAUDE.md` lo dice y `C-002` lo refuerza. El auditor lo eleva igual desde su lado
  («modificar `contract.md` no es una decision de esta auditoria»). Queda por tanto **para el
  usuario y la sesion principal del auditor**, y esta anotado como tal en `A-005` y `T-039`.

---

### D-043 - Se acepta el rechazo del auditor: `contract.md` seguira duplicando, y lo que se construye es el detector
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** `S-005` pregunto al auditor si convenia que `contract.md` **citase** `PROJECT.md` en
  vez de repetir sus valores, para pagar `DT-001` (duplicidad de rutas, rama, carpetas y codigos
  entre los dos archivos). El auditor responde **no, con matiz**: el diagnostico es correcto, la
  solucion no.

- **Decision:** se **acepta el rechazo**, y con el su argumento, que es mejor que el nuestro:
  hacer que el contrato cite `PROJECT.md` dejaria **un contrato bilateral colgando de un archivo que
  solo una de las dos partes controla y puede cambiar sin avisar a la otra**, y obligaria a leer el
  repositorio del otro para resolverlo — con lo que el contrato dejaria de poder leerse de un tiron,
  que es su unica ventaja. **La duplicacion en un contrato es deliberada:** cada lado necesita las
  reglas comunes a mano.

- **Consecuencia sobre `DT-001`:** de sus dos vias de pago, la primera queda **cerrada**. Queda solo
  la segunda —aceptar la duplicacion y **detectar la divergencia**—, y esa es `F-013`, cuyo trabajo
  concreto es `T-040`. `DT-001` se reescribe en `debt_tec.md` dejando constancia de la via
  descartada y de por que, en vez de sustituirla en silencio: al diff solo llegaria la ganadora.

- **Por que no se replica:** `CLAUDE.md` admite **una sola replica, y solo con evidencia nueva**. No
  la hay: el auditor no contradice ningun hecho nuestro, evalua una propuesta y da un motivo
  estructural que no depende de datos que el no tuviera. Insistir seria repetir el mismo argumento
  con otras palabras, que es justo lo que esa regla llama no-replicar.

- **Lo que queda fuera de esta decision:** cambiar `contract.md` en cualquier direccion. Es
  bilateral y se eleva al usuario (ver `D-042`).

---

### D-044 - La marca de no copiar `phases/` se aplaza porque presupone la regla que `DT-002` no ha decidido
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** `S-005` pregunto si el parche de meter `_methodology/phases/` —contenido propio—
  dentro de una carpeta declarada agnostica era aceptable mientras se decide la regla general. El
  auditor responde que **si**, y que forzar ahora la regla repetiria el error que `D-027` evita:
  la primera fase no se escribe hasta cerrar `T-004`, asi que la decision de raiz **no bloquea nada
  hoy**. Pero recomienda arreglar la **detectabilidad**: hoy la exclusion la sostiene una nota en
  prosa dentro de `PROJECT.md`, y **quien copie la carpeta no leera `PROJECT.md`, leera la carpeta**.

- **Decision:** se acepta el fondo —la advertencia debe estar donde ocurre la accion— y se **aplaza
  la ejecucion**, registrada como `T-043`, con disparador **al cerrar `T-004` y antes de escribir la
  primera fase**. `DT-002` recibe el mismo disparador, que hasta ahora no tenia ninguno.

- **Por que se aplaza, y por que este motivo no es «cuesta tiempo»:** escribir la marca obliga a
  elegir **donde** va —cabecera del canonico, archivo dentro de `phases/`, `README.md` en la raiz de
  `_methodology/`—, y las tres opciones **presuponen la regla agnostico/propio que `DT-002` declara
  sin decidir**. Poner la marca hoy fijaria esa regla por la puerta de atras: el archivo escrito
  decidiria lo que nadie decidio. Es el mismo defecto que `CLAUDE.md` denuncia al prohibir diseñar
  una fase desde dentro —lo definido despues de ver el resultado no es una definicion—, aqui en su
  version inversa. Ademas `phases/` **no existe todavia**, asi que la mitad de las opciones ni
  siquiera son escribibles.

- **Alternativa descartada:** poner ya un `README.md` en `_methodology/` y ajustarlo despues. Se
  descarta porque un archivo puesto «provisionalmente» en la carpeta que se copia a otros proyectos
  **viaja con ella**, y lo provisional deja de serlo en cuanto alguien la copia.

- **Riesgo asumido, dicho en voz alta:** si alguien copia `_methodology/` **antes** de que se dispare
  `T-043`, se llevara `phases/` sin aviso. Se acepta porque hoy no hay `phases/` que llevarse y
  porque el disparador ocurre **antes** de que exista.

---

### D-045 - La deuda gana un eje propio: «si es deuda», separado de «si esta pagada»
| Campo | Valor |
|---|---|
| Fecha | 2026-08-30 |
| Etapa | 000_preproject |
| Decidido por | executor |
| Estado | Vigente |

- **Contexto:** `F-014` señala que `DT-001` y `DT-002` entraron al registro con
  `Origen: executor (PROPUESTA — pendiente de confirmar)`, un valor que la convencion de
  `debt_tec.md` no admite, invisible en el indice y **sin decir quien confirma**. Al ir a
  corregirlo aparecio un tercer caso que el auditor no vio: `DT-003` hacia lo mismo por la otra
  punta, con `Origen: executor (confirmada por el usuario el 2026-08-30)`. **Tres de tres**
  improvisando dentro del mismo campo.

- **Decision:** el auditor ofrecia dos salidas —«confirmarlas o retirarlas», o «darle un campo
  propio»—; se hacen **las dos**, porque responden a cosas distintas. Se crea el campo
  **`Confirmacion`** (`Confirmada` / `Propuesta (pendiente de <quien>)`), **con columna en el
  indice**, y `Origen` vuelve a sus tres valores. Las tres entradas quedan `Confirmada`: `DT-001` y
  `DT-002` por el propio auditor en `R-005`, `DT-003` por el usuario.

- **Por que un campo y no solo confirmarlas:** que hoy las tres esten confirmadas es una casualidad
  del momento, no una propiedad del registro. Sin el campo, la **siguiente** deuda dudosa volveria a
  improvisar dentro de `Origen` — que es lo que ya paso tres veces. Tres casos no son dos descuidos:
  son un eje que faltaba.

- **Lo que se declara junto al campo:** que `Estado` dice si la deuda **se pago** y `Confirmacion`
  si **es deuda** —son ortogonales, y por eso son dos campos—, y que **`Propuesta` lleva dueño
  dentro del valor siempre**. No existe `Propuesta` a secas: una propuesta sin dueño no espera, se
  queda propuesta para siempre. Si no se sabe quien confirma, lo que falta no es la confirmacion
  sino saber de quien es la decision, y eso es una `T-XXX`.

- **Alternativa descartada:** dejar el matiz en el cuerpo de la entrada, en prosa. Se descarta por
  lo mismo que `F-011` y `F-014` señalan en dos archivos distintos el mismo dia: **el ojo entra por
  la tabla**, y lo que solo esta en el detalle no se relee.
