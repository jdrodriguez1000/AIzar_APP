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
| [D-011](#d-011---el-arranque-no-lee-al-auditor-hasta-que-t-005-defina-el-canal) | El arranque no lee al auditor hasta que T-005 defina el canal | 2026-08-28 | Vigente |
| [D-012](#d-012---el-arranque-lo-ejecuta-el-agente-session-starter-con-haiku) | El arranque lo ejecuta el agente `session-starter`, con haiku | 2026-08-28 | Vigente |
| [D-013](#d-013---el-arranque-es-de-solo-lectura-y-bash-es-su-unica-frontera) | El arranque es de solo lectura, y `Bash` es su unica frontera | 2026-08-28 | Vigente |
| [D-014](#d-014---el-arranque-precede-a-la-primera-peticion-de-la-conversacion) | El arranque precede a la primera peticion de la conversacion | 2026-08-28 | Vigente |
| [D-015](#d-015---temporal-queda-fuera-del-repositorio) | `temporal/` queda fuera del repositorio | 2026-08-28 | Vigente |

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
| Estado | Vigente |

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
