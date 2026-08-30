# guide.md — Recetario transversal de desarrollo de software

> **Qué es.** El **cómo** se hacen las cosas que se hacen en todo proyecto: procedimientos,
> órdenes concretas, formatos. Agnóstico de lenguaje, de librería y de dominio.
>
> **El porqué va dentro.** Cada receta lleva pegada la razón por la que existe — qué falla cuando
> no se sigue. No hay un archivo aparte para eso: una receta sin su porqué se salta.

**VERSIÓN 5**

> 🔢 **Este número es lo único que dice si una copia está atrasada.** Sube en cada cambio de fondo,
> y solo entonces. Qué cambió en cada versión está en `changelog.md`, una línea por versión. Cómo
> se usa, en [Cómo se adapta a un proyecto nuevo](#cómo-se-adapta-a-un-proyecto-nuevo).
>
> 📌 **Aquí no va ninguna fecha, y es a propósito.** La de cada versión está en su línea del
> `changelog.md`, que es donde se escribe al cambiar. Una fecha repetida en la cabecera se queda
> vieja el primer día que alguien sube la versión y no la toca — y entonces hay dos respuestas a
> «¿de cuándo es esto?».

**De dónde sale cada receta.** Cada una abre con una flecha a su origen:

```
↳ GUIDE §6.e — «Un script que gasta NO puede gastar por defecto»
```

Ese `GUIDE` es **`sources/GUIDE.md`**, el manual del que se destiló este archivo: se conserva
intacto al lado, igual que `_methodology/sources/` guarda las fuentes de `000_method.md`. La
flecha es **procedencia, no lectura obligatoria** — la receta se basta sola, y quien la sigue no
necesita abrir nada más.

> 📌 **Por eso una copia sin la fuente al lado no está rota.** El manual son 2.500 líneas y **no
> viaja con las copias**: en un proyecto que no lo tenga, las flechas son historia y no falta
> nada. Un puntero que promete lo que no cumple quema la confianza en los que sí funcionan; este
> no promete.

⚠️ **La flecha lleva el título, no solo el número, y es a propósito.** Un número de sección se
mueve en cuanto la fuente crece — es el mismo fallo del que avisa el índice de aquí abajo con los
números de línea: **se desplazan y mienten sin avisar**. El título se puede buscar:
`grep -n "Un script que gasta" sources/GUIDE.md`.

---

## Índice

<!-- =====================================================================
     ÍNDICE ESCRITO A MANO. Que no lo regenere ningún automatismo.
     Un generador de TOC vuelve a colgar «Cómo se adapta» de «Anexos»,
     duplica las secciones 0 y 1, y mete el título del propio documento
     como si fuera una sección. Si tu editor lo reinyecta al guardar,
     apaga su índice automático — no lo arregles cada vez.
     ===================================================================== -->

> **No lleva números de línea a propósito**: se desplazan con la primera edición y mienten sin
> avisar. Salta con el enlace, o busca por código: `grep -n "RR-007" guide.md`
>
> 📌 **Se escribe a mano, y por eso hay que tocarlo al añadir una sección.** Una receta que no
> está aquí no existe: nadie la va a encontrar leyendo de corrido, porque este archivo no se lee
> de corrido.

**Antes del recetario**
- [0. Para qué sirve, y qué no es](#0-para-qué-sirve-y-qué-no-es)
- [Los dos ejes: qué aplica a este proyecto](#los-dos-ejes-qué-aplica-a-este-proyecto)
- [1. Cuándo se usa, y cómo se mantiene](#1-cuándo-se-usa-y-cómo-se-mantiene)
  - [Qué merece ser una receta](#qué-merece-ser-una-receta)
  - [Los códigos son estables, y un hueco es información](#los-códigos-son-estables-y-un-hueco-es-información)

**El recetario**
- [`RR-001` · Arranque de un proyecto: el orden](#rr-001--arranque-de-un-proyecto-el-orden)
- [`RR-002` · Las tres preguntas](#rr-002--las-tres-preguntas)
- [`RR-003` · Qué nunca sube a Git](#rr-003--qué-nunca-sube-a-git)
  - [Auditar el historial](#auditar-el-historial)
- [`RR-004` · Nada corre solo por defecto](#rr-004--nada-corre-solo-por-defecto)
- [`RR-005` · Preflight: falla temprano, de barato a caro](#rr-005--preflight-falla-temprano-de-barato-a-caro)
- [`RR-006` · Cómo se prueba: el contrato](#rr-006--cómo-se-prueba-el-contrato)
  - [El caso de prueba es un DATO, no código repetido](#el-caso-de-prueba-es-un-dato-no-código-repetido)
  - [Las tres familias, y la que todo el mundo se salta](#las-tres-familias-y-la-que-todo-el-mundo-se-salta)
  - [Las seis reglas](#las-seis-reglas)
  - [Pruebas de coherencia — las que cazan olvidos](#pruebas-de-coherencia--las-que-cazan-olvidos)
  - [Lo que cambia el mundo: efectos secundarios](#lo-que-cambia-el-mundo-efectos-secundarios)
  - [El límite, que hay que saber decir](#el-límite-que-hay-que-saber-decir)
- [`RR-007` · Sabotea: comprueba que tus pruebas sirven](#rr-007--sabotea-comprueba-que-tus-pruebas-sirven)
- [`RR-008` · El ciclo cuando el que teclea no es una persona](#rr-008--el-ciclo-cuando-el-que-teclea-no-es-una-persona)
  - [La tentación que hay que nombrar para no caer en ella](#-la-tentación-que-hay-que-nombrar-para-no-caer-en-ella)
- [🅰️ `RR-009` · Cuándo crear un subagente](#-rr-009--cuándo-crear-un-subagente)
- [🅰️ `RR-010` · Evidencia, nunca veredicto](#-rr-010--evidencia-nunca-veredicto)
- [`RR-011` · Cómo se entrega un hallazgo](#rr-011--cómo-se-entrega-un-hallazgo)
- [`RR-012` · Cuando el defecto está en el criterio, no en el código](#rr-012--cuando-el-defecto-está-en-el-criterio-no-en-el-código)
- [`RR-013` · Cómo se deshace algo ya publicado](#rr-013--cómo-se-deshace-algo-ya-publicado)

**Anexos** — no aplican a todo proyecto
- [🅰️ Anexo A — Si un modelo interviene en la CONSTRUCCIÓN](#-anexo-a--si-un-modelo-interviene-en-la-construcción)
- [🅱️ Anexo B — Si el PRODUCTO llama a un modelo en producción](#-anexo-b--si-el-producto-llama-a-un-modelo-en-producción)
- [💻 Anexo C — Si trabajas en Windows](#-anexo-c--si-trabajas-en-windows)

**Al final**
- [Cómo se adapta a un proyecto nuevo](#cómo-se-adapta-a-un-proyecto-nuevo)
  - [El ritual, y son cinco pasos](#el-ritual-y-son-cinco-pasos)
  - [En la copia se borra y se añade — nunca se reescribe](#-en-la-copia-se-borra-y-se-añade--nunca-se-reescribe)
  - [La comprobación del desfase](#la-comprobación-del-desfase)

---

## Los dos ejes: qué aplica a este proyecto

No todas las recetas valen para todos los proyectos, y **el criterio son dos preguntas
independientes**. Se responden **al copiar la guía** (paso 2 del ritual), y sus respuestas dicen
mecánicamente qué se borra:

| | Eje | Pregunta | Valores |
|---|---|---|---|
| **A** | **Quién construye** | ¿quién teclea el código y la documentación? | una persona · una sesión de IA sola · **orquestador + workers** |
| **B** | **Qué se construye** | ¿el producto llama a un modelo **en producción**? | no · sí |

**Son independientes, y por eso son dos y no una.** Un proyecto construido íntegramente por
agentes puede entregar una aplicación que no llama a ningún modelo; y una persona puede escribir a
mano un producto que sí lo llama.

| Marca | Qué significa | Se borra si… |
|---|---|---|
| *(sin marca)* | **universal**, siempre aplica | nunca |
| 🅰️ | depende del eje A | la construcción no lo alcanza |
| 🅱️ | depende del eje B | el producto no llama a ningún modelo |
| 💻 | depende de la **máquina**, no del proyecto | trabajas en otro sistema operativo |

> 🚨 **El proveedor NO es un tercer eje.** Anthropic, OpenAI o quien sea: los frenos del harness,
> medir tokens antes de pagar y validar al juez se hacen igual contra cualquier API. Ninguna receta
> de aquí cambia por cambiar de proveedor, y **saltárselas porque «eso es de Anthropic» es
> saltárselas por un motivo que no existe.**

⚠️ **Ojo con la pregunta B, que es la que más se responde mal.** *«¿Usa modelos?»* no se pregunta
sobre cómo se construye el proyecto: se pregunta sobre **lo que se entrega**. Un proyecto que se
construye con agentes y entrega una aplicación sin IA responde **A = agentes, B = no** — y eso
significa que necesita el Anexo A entero y nada del Anexo B.

---

## 0. Para qué sirve, y qué no es

Dos archivos, dos verbos. Si dicen cosas distintas, manda el de arriba:

| Archivo | Verbo | Ejemplo |
|---|---|---|
| `CLAUDE.md` del proyecto | **manda** — qué está prohibido y qué es obligatorio | *«ante una prueba roja se arregla el código»* |
| `guide.md` *(este)* | **enseña a hacer** — el procedimiento | *«el preflight se ordena de barato a caro, y cada fallo imprime dos líneas»* |

Una regla dice que hay que probar. **La guía dice cómo se escribe la prueba.** Y el día concreto
en que no probaste va al `lessons.md` del proyecto, que no es transversal: es suyo.

🚨 **Este archivo no repite reglas.** Si una regla vive en el `CLAUDE.md` del proyecto, aquí se
cita y no se copia: una segunda fuente de verdad envejece sin avisar.

⚠️ **Y no lleva números medidos.** Un umbral medido en otra máquina, con otro stack, no es un
dato aquí: es una anécdota con cifras. Donde haga falta un número, se mide en el proyecto y se
anota allí.

**Tres cosas que este archivo NO es:**

- **No es el método.** No dice qué fases tiene el proyecto ni cuándo se pasa de una a otra.
- **No es documentación del producto.** No describe qué hace la aplicación.
- **No es un diario.** Lo que pasó una vez va al `lessons.md` del proyecto.

---

## 1. Cuándo se usa, y cómo se mantiene

**Nunca se lee entero, y nunca de corrido.** Se abre por la receta que toca, en el momento de
hacer esa tarea, y se cierra. Por eso tiene índice y por eso puede crecer sin estorbar.

⚠️ **Con una excepción, y es una sola: el día que se copia.** El paso 3 del ritual manda borrar
lo que no aplica, y eso no se puede decidir sin haber visto lo que hay. **Esa es la única lectura
completa prevista de este archivo**, ocurre una vez por proyecto, y termina con la guía podada y
sellada.

📌 **Por eso el tamaño se mide contra ese día, no contra el uso diario.** En el uso diario un
archivo largo no estorba: se entra por el índice. Lo que un archivo largo encarece es **la única
lectura entera que alguien va a hacer de él** — y encarecerla es la forma de que la poda se haga
mal, o de que no se haga.

**Los momentos en que se abre:**

| Momento | Qué se abre |
|---|---|
| Al montar el proyecto, antes de la primera línea del producto | `RR-001`, `RR-002`, `RR-003` |
| Antes de escribir algo que sale a la red, escribe, borra o cuesta | `RR-004`, `RR-005` |
| Al escribir o revisar pruebas | `RR-006`, `RR-007` |
| Siempre que el que teclea no sea una persona | `RR-008` |
| 🅰️ Cuando hay orquestador y workers, y alguien revisa a alguien | `RR-009`, `RR-010` |
| Al entregar un hallazgo, o al sospechar que el defecto no está en el código | `RR-011`, `RR-012` |
| Antes de deshacer algo que ya está publicado | `RR-013` |

**Cómo se mantiene:**

> **Una lección solo crece. Una receta se corrige.**

Una lección vieja sigue siendo cierta: pasó. Una receta obsoleta **miente**, y quien la sigue
hace mal el trabajo creyendo que lo hace bien. Por eso, cuando una receta deja de valer, **se
reescribe o se borra**. No se añade la nueva debajo — y **la versión de la cabecera sube**.

📌 **Lo único que se acumula es el `changelog.md`**, una línea por versión. No contradice lo de
arriba: la receta corregida sigue siendo una sola. Lo que se guarda es el **aviso de que cambió**,
y sin ese aviso la corrección se queda aquí en vez de llegar a las copias.

⚠️ **Este archivo tiene un enemigo y es su propio tamaño.** Una corrección exacta, bien escrita,
mil líneas más abajo, no llega. Si deja de leerse el índice de un vistazo, se poda antes de
añadir.

### Qué merece ser una receta

**Esta guía no aspira a cubrirlo todo, y es a propósito.** Una guía completa es una guía que ya
no se abre. Lo que decide no es si el tema es importante — casi todos lo son — sino si pasa los
cuatro filtros:

| | La pregunta | Si la respuesta es «no», dónde va |
|---|---|---|
| 1 | **¿Es transversal?** ¿valdría igual en otro lenguaje, otro stack, otro dominio | a la documentación del proyecto |
| 2 | **¿Falla en silencio?** ¿el que se equivoca se entera cuando ya es caro | a ningún sitio: si el error salta en tu cara al momento, el error ya es la receta |
| 3 | **¿Hay un procedimiento que enseñar?** un formato, un orden, unos pasos | es una **regla**, no una receta, y las reglas viven en el `CLAUDE.md` del proyecto |
| 4 | **¿No está ya dicho en otra receta?** | debajo de esa, como aterrizaje o como matiz |

🚨 **El filtro 2 es el que descarta más candidatas, y el que más cuesta aplicar.** «Convención de
mensajes de commit» es importante, transversal y tiene procedimiento — pero se falla a la vista
de todos y se arregla al momento. `RR-003` existe por lo contrario: git no avisa de nada, y
cuando avisa ya está publicado.

⛔ **Y no se admite una receta sobre algo que el proyecto todavía no hace.** Escrita antes de que
exista el stack que la juzgue, describe lo que uno imagina, no lo que muerde — y llegará el día
de corregirla, cuando ya se haya copiado. Es el mismo argumento de siempre: **lo que se define sin
el sujeto delante no es una definición.**

📌 **El presupuesto no es el número de recetas: es el índice.** Mientras se lea de un vistazo,
añadir una no obliga a podar otra — un canje 1:1 solo consigue borrar algo útil para pagar algo
útil. El día que el índice deje de leerse de un vistazo, se poda **antes** de añadir, y se poda
por el filtro 2: primero lo que falla ruidosamente, que es lo que menos falta hace aquí.

### Los códigos son estables, y un hueco es información

Los códigos `RR-NNN` **los asigna esta guía global, y solo ella.** Una vez puesto, un código no
se reasigna, no se renumera y no se reutiliza aunque su receta se borre.

🚨 **Por qué importa, si parece contabilidad:** el índice de aquí arriba enseña a navegar con
`grep -n "RR-007" guide.md`, y el ritual de copia manda **borrar** las recetas que no aplican. Si
al podar `RR-005` se renumera lo que va detrás, el `RR-007` de ese proyecto deja de ser el de los
demás — y el `grep` no falla: **devuelve la receta equivocada con toda naturalidad.** Un puntero
roto se ve; uno que apunta a otro sitio, no.

📌 **Por eso un hueco en la numeración no es un error a corregir: es la única prueba de que se
podó a propósito.** `RR-005` ausente dice «aquí no aplica, y está en la tabla de exclusiones».
`RR-005` ocupado por otra receta no dice nada, y encima miente.

**Y por eso una copia nunca escribe un código que la global no tenga.** Cuando en un proyecto
aparece algo que merece receta, tiene tres destinos y ninguno es inventar un `RR-NNN`:

| Lo que apareció | Dónde va |
|---|---|
| **Es transversal** — valdría en otro proyecto | **sube a la global**: se escribe aquí, sube la versión, se anota en `changelog.md` y se vuelve a copiar |
| **Es propio de este proyecto** — su stack, su dominio, su despliegue | **no es del recetario**: va a la documentación del proyecto. Esta guía es agnóstica por definición |
| **Matiza una receta que ya existe** | **aterrizaje marcado**, en un bloque debajo de ella (ritual, paso 5) |

⚠️ **El destino que más se falla es el primero, y falla por comodidad.** Escribirlo en la copia
cuesta un minuto y subirlo aquí cuesta cinco. Pero dos proyectos que inventan su `RR-013` la misma
semana crean dos recetas distintas con el mismo nombre, y ya no hay forma de saber cuál es cuál
sin abrir las dos.

---

# El recetario

## `RR-001` · Arranque de un proyecto: el orden

↳ *GUIDE §6 — «Checklist: proyecto nuevo desde cero»*

El orden importa: cada paso hace barato el siguiente.

- [ ] Carpeta del proyecto y repositorio inicializado
- [ ] Entorno aislado del sistema (virtualenv, contenedor, lo que use el stack)
- [ ] Archivo de dependencias declarado y versionado
- [ ] `.gitignore` **antes** del primer commit → `RR-003`
- [ ] Plantilla de configuración con los **nombres** de las variables, sin valores reales
- [ ] Configuración real, fuera del repositorio
- [ ] Un script de verificación que falle temprano y claro → `RR-005`
- [ ] **Correrlo y verlo pasar antes de escribir la primera línea del producto**
- [ ] Las tres preguntas declaradas → `RR-002`

📌 **El último paso es el que se salta todo el mundo.** Un preflight que nunca se corrió no
distingue *«el entorno está bien»* de *«el preflight está roto»*.

---

## `RR-002` · Las tres preguntas

↳ *GUIDE §6.b — «Las tres preguntas — se declaran antes de la primera línea del producto»*

No se construyen el día 1: se les da **dueño y sitio** antes de la primera línea del producto.
Las tres se cobran solas cuando ya hay algo que perder, y entonces se construyen a la carrera.

- [ ] **Evaluación** — *¿funciona?* → **dónde viven las pruebas.** Se crea el archivo aunque
      tenga un solo caso. **Y ese caso tiene que salir en ROJO una vez**, antes de arreglarlo.
- [ ] **Observabilidad** — *¿qué está haciendo ahora?* → **dónde se escribe el registro.** Una
      línea estructurada por evento ya sirve: cuándo, qué se pidió, qué se hizo, qué falló.
      **Ábrelo una vez y responde una pregunta con él**; un registro que nadie leyó es disco
      ocupado.
- [ ] **Seguridad** — *¿qué puede hacer, y qué le pueden hacer?* → **la lista de lo que el
      sistema puede tocar del mundo real**, y con permisos de quién. Esa lista *es* la
      superficie de ataque.

> ⚠️ **Ninguna se marca prometiendo tenerla en cuenta.** Se marca con un artefacto que existe:
> un archivo, una corrida en rojo, un registro abierto.

**El orden es por dependencia, no por importancia:** observabilidad antes que seguridad. Sin
registro no puedes ver morder un freno ni demostrar qué pasó el día que pasó.

📌 **Traduce la tercera a tu dominio, o se queda abstracta.** Si consumes una fuente externa:
*¿qué pasa si cambia su formato? ¿si responde a medias? ¿si devuelve éxito con una página de
mantenimiento? ¿cuántas veces al día es razonable pedirle algo?*

---

## `RR-003` · Qué nunca sube a Git

↳ *GUIDE §2 — «Mapa de archivos de la raíz» · §2.b — «Auditar el historial de un repo público»*

⚠️ **Git no olvida.** Borrar un archivo después **no lo borra del historial**. Por eso lo que
nunca debe subir se decide **antes** del primer commit.

| Qué | ¿Sube? |
|---|---|
| Documentación, memoria del proceso, código | **Sí** |
| Archivos de configuración con valores reales | ❌ **Nunca**, y va al `.gitignore` |
| Credenciales, tokens, rutas personales, datos de personas | ❌ **Nunca** — y el `.gitignore` **no las cubre** si están pegadas dentro de un `.md` |

🚨 **El camino por el que algo se escapa no es el archivo grande que alguien vigila: es el
ejemplo pequeño dentro de una lección que nadie revisó.**

### Auditar el historial

Responde una sola pregunta: **¿entró alguna vez algo que no debía?** Tres barridos, y cada uno
mira una cosa distinta:

| # | La pregunta | Sobre qué mira |
|---|---|---|
| 1 | ¿Existió alguna vez un archivo prohibido? | los **nombres** de todo el historial |
| 2 | ¿Entró alguna vez una credencial? | el **contenido** de todos los commits |
| 3 | ¿Entró un dato personal? | el **contenido**, con el patrón del dato |

**Los patrones, ya anclados** — se pegan en el buscador que use la máquina; la receta no elige
herramienta, pero **el patrón no se improvisa**:

```
1.  (^|/)\.env$      (^|/)data/      \.pem$      \.key$

2.  (AKIA|ASIA|AIDA|AROA)[0-9A-Z]{16}
    sk-ant-[A-Za-z0-9_-]{20,}
    ghp_[A-Za-z0-9]{36}
    -----BEGIN [A-Z ]*PRIVATE KEY-----

3.  [A-Za-z0-9._%+-]+@(gmail|hotmail|outlook)\.com
```

**Por qué cada uno está escrito así, que es lo que se traslada a un patrón nuevo:**

- **El 1 ancla al separador de ruta, no a la raíz.** Con `^` solo, un archivo prohibido dentro de
  una subcarpeta se escapa; por eso `(^|/)` y no `^`.
- **El 2 ancla al formato del secreto** —prefijo, longitud, mayúsculas—, nunca a una palabra. Sin
  la longitud, `ASIA` cae dentro de *dem·ASIA·do* y el detector se llena de basura; sin el
  prefijo `sk-ant-`, una llave entera pasa sin verse.
- **El 3 lleva el patrón del dato, nunca una dirección escrita en el propio comando.**

💻 **El buscador tiene que ir en modo sensible a mayúsculas.** Si por defecto no lo está —y en
PowerShell `Select-String` no lo está—, `asia` vale por `ASIA` y el barrido 2 se apaga solo el
primer día.

**Lo esperado es CERO en los tres.** Si alguno devuelve algo, el arreglo **no** es borrar el
archivo: es **rotar la credencial**. Es más barato y más seguro que reescribir historia
publicada → `RR-013`.

> 🚨 **Un patrón flojo miente, y mentir mucho es peor que no mirar.** Un detector que grita
> veinte veces y las veinte son falsas **es un detector que dejarás de mirar**. El día que haya
> algo de verdad, tus ojos ya aprendieron a saltárselo. Ancla al formato, nunca a una palabra
> suelta.

📌 **Y un patrón solo es creíble después de verlo en rojo.** Dale líneas envenenadas a propósito
y comprueba que las caza. Un detector que solo se ha visto en verde no se distingue de uno vacío.

⚠️ **Ojo con el falso positivo estructural:** un barrido sobre el historial completo también lee
las cabeceras de cada commit. Si tu correo real está en el autor, el patrón de correos saltará
en **todos** los commits, y eso apaga el detector el primer día.

---

## `RR-004` · Nada corre solo por defecto

↳ *GUIDE §6.e — «Un script que gasta NO puede gastar por defecto»*

> **La pregunta es: ¿qué pasa si corro esto sin mirar?**

Ejecutar un módulo en pelado es lo que se hace para ver si sigue compilando y si sus pruebas
siguen verdes. **Si ese mismo comando dispara lo caro, la comprobación más inocente del día se
convierte en un incidente** — y no avisa: se ve igual que una suite.

**Qué es «lo caro» cambia por proyecto. La regla no.** Puede ser dinero, tráfico contra un
tercero, una escritura en la base de datos, un correo enviado, un despliegue.

**La forma:**

```
<ejecutar el módulo>              -> SIEMPRE inofensivo. Pruebas, informes, comprobaciones.
<ejecutar el módulo> --<bandera>  -> lo que toca el mundo real, y solo con la bandera puesta.
```

En pelado, el módulo imprime su informe y **dice con todas las letras** qué bandera hace falta.

> 🚨 **Y la lección que cuesta dos veces: la prosa no es un freno.**
>
> Primero se escribe una tabla avisando de qué archivos son peligrosos. Falla por estar
> incompleta — quien busca el suyo y no lo encuentra concluye que es de los seguros; **una
> advertencia con lista incompleta no avisa a medias: tranquiliza**. Se completa la tabla, y
> **vuelve a fallar igual**: nadie consulta una tabla antes de un comando que lleva cien veces
> saliendo bien.
>
> **El arreglo no es una tabla mejor: es un freno en el código.** Un módulo capaz de tocar el
> mundo real debe tener el freno puesto, o una razón escrita de por qué no lo necesita. **La
> prosa es el mapa; el que para la mano es el código.**

---

## `RR-005` · Preflight: falla temprano, de barato a caro

↳ *GUIDE §7 — «Patrón: script de verificación (preflight)»*

Un script de verificación que se corre **antes** de lo caro, ordenado de más barato a más caro
para que lo que falla más falle primero:

```
1. ¿Está el entorno de ejecución en la versión que hace falta?
2. ¿Están las dependencias?
3. ¿Existe la configuración, y no es la plantilla de ejemplo sin rellenar?
4. ¿La configuración FUNCIONA?  -> una operación real, mínima, contra el recurso de verdad
```

> **El paso 4 es el que casi todos se saltan, y es el único que prueba la verdad.** Que exista
> una credencial no dice que sirva; que el servicio responda no dice que devuelva lo que esperas.

🚨 **Cada fallo imprime DOS cosas: qué pasó y qué hacer.**

```
[FALTA] <qué pasó>
        -> <qué hacer para arreglarlo>
```

Uno que solo dice qué falta obliga a buscar la solución; uno que dice las dos cosas se resuelve
sin salir de la terminal. Es la diferencia entre un diagnóstico y una tarea.

📌 **El paso 4 usa la operación más pequeña posible**, y va con la bandera de `RR-004`: **el
preflight no dispara la carga pesada.**

---

## `RR-006` · Cómo se prueba: el contrato

↳ *GUIDE §8.l — «Probar tus propias funciones (sin modelo, sin red, $0.00)» · §8.c — «Evals de coherencia (los que cazan olvidos)»*

### El caso de prueba es un DATO, no código repetido

Una tabla de casos —etiqueta, entradas, resultado esperado— recorrida por un bucle que compara e
imprime `ok`/`FALLA`. **Añadir el caso 27 debe ser una línea.**

Con aserciones sueltas son dos líneas por caso, y **el primer fallo mata el programa**: te
enteras de un problema por corrida en vez de los siete que hay.

### Las tres familias, y la que todo el mundo se salta

| Familia | Qué es |
|---|---|
| camino feliz | la entrada normal |
| **bordes** | el cero, el vacío, lo negativo, lo enorme, **el límite exacto por sus dos lados** |
| lo malo | lo que **debe** ser rechazado |

> El camino feliz se prueba solo mientras escribes, y lo malo se prueba porque acabas de escribir
> la validación. **Los bordes no se le ocurren a nadie hasta que un usuario los encuentra.**

### Las seis reglas

1. **Imprimir no es probar.** Si tú miras la salida y decides, el juez eres tú y no hay prueba.
   La prueba dice `ok`/`FALLA` sola.
2. **Un caso, una variable.** Un caso con dos defectos pasa a verde cuando arreglas uno, con el
   otro todavía roto.
3. **Captura los reventones como un resultado más.** Que algo reviente **es un comportamiento**,
   y va en la misma tabla. Sin eso, la suite muere en el caso que revienta.
4. **No compares el texto del error, solo que haya error.** Si comparas la redacción, mejorar el
   mensaje rompe la prueba.
5. **Cada caso independiente.** Si el orden importa, son N casos encadenados, no N pruebas.
6. **Un caso de prueba es la forma más duradera de escribir una decisión.** El comentario se
   ignora; el caso rojo pregunta *«¿seguro?»*.

### Pruebas de coherencia — las que cazan olvidos

No prueban comportamiento: prueban que **no se te olvidó nada al añadir una pieza**. Cuestan cero
y avisan en un segundo. *¿Toda regla declarada tiene una comprobación que la aplique? ¿Todo campo
que el contrato exige se está guardando?* Su momento llega cuando añades la sexta regla y se te
olvida enchufarla.

### Lo que cambia el mundo: efectos secundarios

Cuando la función **escribe**, lo que devuelve **es un recibo, no la verdad**.

- **Estado conocido antes de CADA caso**, no una vez al principio. El dato que dejó la corrida de
  ayer hace pasar *«el registro existe»* aunque la función ya no escriba.
- **Comprueba dos cosas:** que exista **y** que el contenido coincida.
- **En los casos que esperan rechazo, comprueba que el almacén quedó intacto.** Una función puede
  escribir y *después* devolver error.
- **Nunca contra el almacén de verdad.** Una suite con efecto secundario destructivo **no se ve
  roja: se ve verde**, mientras borra lo que no debía.

### El límite, que hay que saber decir

Una suite no dice *«mi código está bien»*. Dice *«estas 26 cosas se comportan como dije»*. Todo lo
demás sigue sin explorar — y **anotar dónde acaba la prueba es parte de tenerla**.

---

## `RR-007` · Sabotea: comprueba que tus pruebas sirven

↳ *GUIDE §8.l — «Probar tus propias funciones (sin modelo, sin red, $0.00)»*

**Ninguna prueba vale hasta verla roja.**

Rompe a propósito la línea que hace el trabajo y **exige ver el rojo**. Si sigue en verde, la
prueba no estaba mirando lo que creías. Restaura y confirma el verde.

> Una prueba en rojo dice dónde está el problema. Una prueba en verde **no** dice que no haya
> problema: dice que **tu comparación no lo ve**.

**Qué sabotear, en orden de lo que más enseña:**

| Rompe esto | Y mira si la prueba ve que… |
|---|---|
| **quién** entra en el resultado, no cuántos | no basta contar elementos |
| una **validación**, invirtiendo su comparador | lo prohibido sigue prohibido |
| un **borde** exacto (`<=` → `<`) | probaste los **dos** lados, no uno |
| el **orden** cuando el orden importa | *«¿está?»* no es *«en qué posición?»* |
| el **desvío** al almacén de pruebas | tu trampa contra el almacén real salta |

**Y tres cosas que solo se aprenden saboteando:**

1. ⭐ **Un defecto puede reportar ÉXITO.** El conteo sigue dando lo mismo y el mensaje sigue
   diciendo lo mismo, con el valor equivocado dentro. Solo lo ven los casos que preguntan
   **quién**.
2. ⚠️ **Prefiere el caso genérico al concreto.** El concreto revienta y dice *«se rompió»*; el que
   recorre la tabla entera dice **qué** arreglar.
3. ⚠️ **Si al romper algo la prueba se cuelga o revienta en vez de ponerse roja, no lo ignores.**
   Un rojo que dice *«me colgué»* no dice *«la tabla está mal»*.

---

## `RR-008` · El ciclo cuando el que teclea no es una persona

↳ *GUIDE §11.i — «Cuando el que teclea es un agente»* — **la receta más importante de este archivo.**

**Esta receta no lleva marca de eje: aplica siempre que teclee una IA**, y da igual si es una
sesión sola o un orquestador con veinte workers. Basta con que **la misma sesión que escribe el
código escriba y corra sus pruebas** — y eso pasa ya en el caso más simple de todos.

> ⚠️ **Que teclee una persona es hoy el caso raro, no el normal.** Si en tu proyecto teclea alguien
> de carne y hueso, esta receta sobra y se borra. En cualquier otro caso —incluido el proyecto de
> una sola sesión— **es la receta más importante del archivo**, porque describe el único agujero
> que el resto del recetario no puede tapar: quién puede ser testigo de qué.

> **El ciclo no cambia. Cambia quién puede ser testigo de qué.**

| Paso | Quién | Qué se exige VER |
|---|---|---|
| **1. El criterio** | **el usuario**, en prosa, **antes** | la frase escrita, con sus casos de borde |
| **2. Rojo → verde** | la sesión que construye | **el rojo**, con su salida cruda. Sin rojo previo no hubo prueba |
| **3. Refactor** | la sesión que construye | el diff toca código y **no** toca pruebas |
| **4. Verificar** | **desde fuera** | lo medido contra lo dicho, **no el reporte** |

⚠️ **El paso 1 no es opcional y es el que sostiene los otros tres.** Si el criterio lo inventa la
misma sesión que escribe el código, el paso 2 se vuelve teatro —una prueba que él definió, que él
hace fallar, que él hace pasar— y el paso 4 audita **contra un criterio que escribió el auditado**.

**Lo que se mira, y es barato y local:**

- 🔍 **El diff de las pruebas, APARTE del diff del código.** Una prueba ablandada no se anuncia:
  solo se ve ahí.
- 🔍 **Que el rojo EXISTIERA.** Una prueba que nunca falló no probó nada, y **mirando el verde no
  se distingue de una vacía**.

📌 **El saboteo (`RR-007`) es obligatorio, pero no cubre esto.** Demuestra que la prueba vigila esa
línea; **nunca que la línea sea la correcta**. Eso solo lo dice el criterio del paso 1.

### 🚨 La tentación que hay que nombrar para no caer en ella

**Repartir el ciclo entre varios agentes:** uno que escribe, otro que revisa, otro que certifica.
**No.**

Es cortar **por fases del trabajo**, que copia el organigrama de una empresa — donde los roles
existen porque una persona no puede estar en dos sitios. **Un agente no tiene ese problema.**

Y falla por dos sitios: el revisor lee lo que escribió el otro, así que **no hay testigo
independiente**; y el que certifica emite un **veredicto**, y un veredicto desplaza la auditoría —
en cuanto alguien escribe *«certificado»*, nadie vuelve a mirar.

**El ciclo lo corre un solo agente, seguido:** la continuidad es lo que el ciclo fabrica.

---

## 🅰️ `RR-009` · Cuándo crear un subagente

↳ *GUIDE §11.i.2 — «Cuándo crear un subagente (y cuándo no)»*

**🅰️ Eje A — solo si se pueden crear subagentes.** Si teclea una sesión sola y nunca reparte
trabajo, esta receta y la siguiente se borran juntas.

Vale para cualquier trabajo, no solo para pruebas. **Un agente puede hacer dos cosas seguidas; lo
que no puede es ser testigo de sí mismo.** Ese es el único corte que compra algo.

> ⭐ **LA PREGUNTA QUE DECIDE:**
> **¿Este agente necesita saber MENOS que yo, o MÁS?**
>
> **Menos, y su valor está en no saber** → es un agente.
> **Más, o todo lo mío** → es un traspaso, y los traspasos pierden. Hazlo tú.

| Razón para crearlo | Qué compra | Señal de que NO es el caso |
|---|---|---|
| **Independencia de criterio** | un testigo que no vio construir | tienes que pasarle tu contexto → es un eco |
| **Aislamiento de ruido** | que una salida enorme no entre en tu contexto | te importa el detalle, no la conclusión |
| **Paralelismo real** | tiempo | la segunda tarea espera el resultado de la primera |

❌ **El corte equivocado es por fases del trabajo** (analizar → escribir → probar → revisar).
Ver `RR-008`.

---

## 🅰️ `RR-010` · Evidencia, nunca veredicto

↳ *GUIDE §11.i.3 — «El subagente verificador — evidencia, nunca veredicto»*

Si se crea un revisor —agente o persona— que mire el trabajo **antes** de que salga:

| Recibe | **No** recibe |
|---|---|
| el criterio escrito por el usuario | el relato de cómo se llegó al código |
| el diff y los artefactos | qué se intentó y se descartó |
| poder correr comandos | **permiso de escribir** |

> 🚨 **Las dos reglas que impiden que se vuelva una coartada:**
>
> 1. **Entrega evidencia, no veredicto.** No dice *«todo bien»*: dice *«corrí esto, salió esto»*,
>    con la salida cruda pegada. **Un veredicto desplaza la auditoría; una evidencia la alimenta.**
> 2. **Lista cerrada, no «busca problemas».** Lo que no está en la lista **no se declara limpio:
>    se declara NO MIRADO.**

⚠️ **No sustituye a un testigo de fuera.** No puede juzgar si el criterio estaba bien ni si algo se
recortó en silencio: eso exige estar **fuera del marco**, no en otro proceso dentro de él. Lo que
hace es quitarle el trabajo mecánico.

📌 **Y por qué la regla 1 no es cosmética:** *el resumen sale peor que el documento*. Un verificador
que resume convierte la evidencia en opinión, que es lo único que no queríamos.

---

## `RR-011` · Cómo se entrega un hallazgo

↳ *GUIDE §6.d — «Plantilla: entregar un hallazgo con su prioridad»*

**Las dos marcas van en la PRIMERA línea, nunca en el remate.** Quien lee no puede recuperar la
gravedad; quien escribe la tiene gratis.

- **Importancia:** baja · media · alta → *¿vale la pena corregirlo?* Es juicio, y se discute.
- **Urgencia:** bloqueante o no → *¿se hace ya?* **Es un hecho o es una mentira.**

**Un hallazgo suelto:**

```markdown
## 🔴 Importancia ALTA · no bloqueante

<qué pasa, en una o dos frases>

<la evidencia: ruta:línea, o el comando que lo enseña>

<el arreglo>

**No es bloqueante** porque <qué NO impide hoy>.
```

**Varios de golpe** — tabla, y se lee sin abrir ninguno:

```markdown
| qué | importancia | urgencia | qué significa |
|---|---|---|---|
| <cosa> | **alta** | **bloqueante** | <qué se rompe si sigues> |
| <cosa> | media | no | <por qué puede esperar> |
```

**Qué obliga cada marca:**

| Marca | Qué se escribe |
|---|---|
| 🔴 **alta** | el párrafo completo con evidencia |
| 🟡 **media** | dos o tres líneas |
| ⚪ **baja** | **una línea, o no se entrega** |
| **bloqueante** | **obligatorio**: la frase que dice qué bloquea y qué se rompe si sigues |
| no bloqueante | nada extra |

⚠️ **Los dos errores que esta plantilla existe para evitar:**

1. **Escribir «bloqueante» sin la frase de qué se rompe.** Si no sale la frase, no era bloqueante:
   era una tarea que apetecía hacer primero.
2. **Argumentar bien algo de importancia baja.** Un párrafo sólido sobre una nimiedad cuesta lo
   mismo de leer que uno sobre lo que paraba el trabajo, y **se lleva la atención por delante.**

📌 **Si clasificas algo alta sin haberlo medido, dilo en la misma línea** (*«alta, sin medir»*).
Así la marca no se disfraza de dato.

📌 **La casilla que se pierde siempre es `alta / no bloqueante`:** importante y sin fecha, no grita,
y espera turnos enteros. Se revisa al cerrar sesión.

📌 **Y el hallazgo llega mientras la sesión del que construye sigue abierta.** Lo que nace después
de su cierre no tiene dueño: su commit ya está hecho.

---

## `RR-012` · Cuando el defecto está en el criterio, no en el código

↳ *GUIDE §10 — «Cuando el defecto está en el PROMPT, no en el código» · §11.c — «La pregunta que va ANTES de escribir un criterio»*

Antes de arreglar código, pregunta **dónde vive de verdad el defecto**. Hay tres sitios, y solo
uno se arregla programando:

| Dónde | Cómo se ve | Cómo se arregla |
|---|---|---|
| **El código** | hace algo distinto de lo que dice el criterio | se programa |
| **El criterio** | el código cumple, y el resultado sigue siendo malo | se reescribe el criterio |
| **La evidencia** | quien juzga no podía ver lo que hacía falta para juzgar | se le da el dato, no se cambia nada más |

> 🚨 **Escribir un criterio sin decir con qué evidencia se comprueba no lo deja sin medir: lo deja
> midiendo mal**, con resultados que se ven igual de buenos que los verdaderos.

**Dos reglas al escribir criterios:**

1. **Ordena más de lo que prohíbes.** Una prohibición deja infinitas formas de cumplirla mal.
2. **Cada cosa se castiga en UN solo lugar.** Dos criterios que miden lo mismo no miden el doble:
   se contradicen. Cuando dos veredictos choquen, sospecha primero del criterio.

📌 **Y cuándo parar de parchear:** si el tercer parche al criterio destapa un defecto nuevo, el
problema no es el parche — es que el criterio estaba mal partido.

---

## `RR-013` · Cómo se deshace algo ya publicado

↳ *GUIDE §2.b — «Auditar el historial de un repo público» · §3.a — «Dos shells en la misma máquina, dos gramáticas»*

> **La pregunta es una sola: ¿lo que quiero deshacer ya lo tiene alguien más?**

Son dos mundos distintos, y confundirlos es el fallo:

| Dónde está lo que quieres deshacer | Qué se puede hacer |
|---|---|
| **Solo en tu máquina**, sin publicar | reescribir a gusto: rehacer el commit, reordenarlo, tirarlo |
| **Ya publicado** | ❌ **no se reescribe.** Se deshace **hacia adelante**: un commit nuevo que revierte al anterior |

🚨 **Por qué reescribir lo publicado no es «arreglar»: es romperle el repositorio a los demás.**
Quien reescribe historia ya publicada **no ve el daño** — su copia queda perfecta. Lo ven los que
ya tenían la versión vieja, y lo ven más tarde, con un conflicto que no explica de dónde sale. Es
un fallo silencioso **y ajeno**: las dos condiciones que hacen que nadie lo relacione con su
causa.

**Y por eso deshacer hacia adelante deja cicatriz, que es exactamente lo que se quiere.** El
commit malo sigue ahí y encima está el que lo revierte. Quien lo lea mañana ve **que pasó y que se
corrigió**; con la historia reescrita vería un pasado limpio que nunca existió.

**Qué arregla cada cosa, según lo que se publicó:**

| Lo que se publicó | Lo que NO lo arregla | Lo que sí |
|---|---|---|
| Código o texto equivocado | borrarlo del historial | un commit que lo revierte |
| Una credencial, una ruta, un dato de una persona | borrar el archivo — el historial lo conserva | **rotar la credencial** → `RR-003` |
| Ruido cosmético: un mensaje de commit malformado | reescribir la historia por una errata | **nada: se deja.** El arreglo cuesta más que el ruido |

📌 **La tercera fila es la que cuesta aceptar,** y es la más frecuente. Un mensaje de commit con
un carácter de más se ve mal para siempre, y da igual: reescribir historia publicada por eso es
pagar un riesgo real con moneda de vanidad.

⚠️ **La excepción existe, y tiene una sola forma.** Reescribir lo publicado se hace **solo con
acuerdo previo y explícito de todos los que ya tienen esa historia**, y anunciado **antes**, nunca
después. Un aviso posterior no es un aviso: es un parte de daños.

---

# Anexos

## 🅰️ Anexo A — Si un modelo interviene en la CONSTRUCCIÓN

**Aplica si el eje A dice «sesión de IA» u «orquestador + workers»** — aunque el producto final no
llame a ningún modelo. Lo que corre aquí es **el harness que construye**, y cuesta dinero y puede
irse de las manos igual que el que se entrega.

> 🚨 **Este es el anexo que se salta quien no debe.** Un proyecto construido por agentes cuyo
> producto no usa IA lee «modelos de lenguaje», piensa *«mi aplicación no lleva IA»* y lo descarta
> entero — perdiendo justo los frenos y el control de coste que **más falta le hacen**, porque va a
> tener un orquestador quemando tokens sin techo. La pregunta no es qué entregas: es **quién
> teclea**.

Estas recetas **no** están aquí: viven en `sources/GUIDE.md` y se traen al proyecto el día que
haga falta. Se listan para que la ausencia no se lea como olvido.

| Qué | Dónde | Cuándo traerlo |
|---|---|---|
| Los diez frenos del harness — timeout, reintentos, presupuesto, tope de vueltas, permisos, registro | §4.c | al escribir el primer bucle que llama a un modelo |
| Medir tokens sin pagar, ventanas de contexto, experimentar barato | §5.b, §5.c | antes de estimar coste. **Nunca estimes dividiendo caracteres** |
| Elegir modelo | §5 | al decidir qué modelo hace qué |
| Guardrail frente a inyección de prompt | §6.c | si entra texto que no escribiste tú — **y a un orquestador que lee archivos y páginas, le entra** |

📌 **La barrera nunca es el modelo.** Una frase en el prompt es una sugerencia; que la herramienta
peligrosa **no exista** en la lista es una barrera física. Ninguna frase la mueve.

📌 **`RR-004` es la versión agnóstica de la primera fila**, y esa sí está aquí: nada corre solo por
defecto. Los diez frenos son su forma concreta cuando lo caro es una llamada a un modelo.

---

## 🅱️ Anexo B — Si el PRODUCTO llama a un modelo en producción

**Aplica si el eje B dice «sí»**, y **no** por construir con agentes. Aquí no se mide el harness
que construye: se mide **la conducta de lo que se entrega**, que es un problema distinto y con
herramientas distintas.

| Qué | Dónde | Cuándo traerlo |
|---|---|---|
| TDD frente a evals — **la regla que parte el mundo en dos** | §11.a | ver abajo |
| Rúbrica, juez, y validar al juez | §8.g, §8.h | al medir conducta |
| Guardrail frente a inyección de prompt | §6.c | si el producto recibe texto de sus usuarios |

> 🔑 **La regla que decide dónde va algo:** *si la respuesta correcta se puede escribir en un `if`,
> es una prueba (`RR-006`). Si necesita criterio, es un eval.*
>
> Una prueba da rojo o verde, cuesta cero y da un trinquete: lo que pasó a verde se queda verde. Un
> eval da un porcentaje, cuesta dinero, y **puede bajar mañana sin que nadie haya tocado nada.**

⚠️ **Y una diferencia que se paga cara si se ignora:** al medir conducta se cambia **una sola cosa
por vuelta**. Un porcentaje que se movió no dice por qué se movió.

📌 **El guardrail sale en los dos anexos, y no es un descuido.** Son dos superficies distintas: en
el Anexo A el texto que no escribiste tú entra por lo que el orquestador lee; aquí entra por lo que
escriben tus usuarios. Se cierran por separado y una no protege de la otra.

---

## 💻 Anexo C — Si trabajas en Windows

↳ *GUIDE §3.a — «Dos shells en la misma máquina, dos gramáticas»*

⚠️ **Este anexo no depende del proyecto, sino de la máquina.** El mismo repositorio abierto en
Linux lo lleva de sobra. Si un proyecto se toca desde dos sistemas, no se borra: se deja.

Conviven **PowerShell** y **Bash** (Git Bash). Se parecen lo suficiente para confundirse y **no
comparten sintaxis**. Escribir la de uno en el otro no siempre da error: a veces «funciona» y
ensucia algo.

| Para esto | PowerShell | Bash |
|---|---|---|
| Texto de varias líneas | `@'` … `'@` | `<<'EOF'` … `EOF` |
| Variable de entorno | `$env:NOMBRE` | `$NOMBRE` |
| Tirar la salida a la basura | `2>$null` | `2>/dev/null` |
| Escapar un carácter | `` ` `` (tilde invertida) | `\` |

> 🔑 **El modo de fallo que importa no es el error: es el resultado ligeramente equivocado.** Un
> error se arregla en el momento. Un mensaje de commit malformado ya subido, no.

⚠️ **Rutas:** una ruta estilo Unix escrita desde Bash y leída después por otra herramienta **no es
la misma ruta**. Si un archivo se escribe desde una herramienta y se usa desde otra, **rutas
absolutas**.

---

# Cómo se adapta a un proyecto nuevo

Este archivo **no se usa desde aquí**: se **copia** al proyecto como `guide.md` y se adapta. Una
guía compartida entre proyectos no se puede corregir sin romper a los demás, y una guía que no se
corrige miente.

⚠️ **Pero copiar crea tantas verdades como proyectos, y nadie las ve nunca juntas.** Un arreglo
hecho en la copia de un proyecto no llega a los demás, y no hay nada que avise: el que abre otro
proyecto tropieza otra vez con lo que ya estaba resuelto. Lo que sigue existe solo para eso, y son
tres piezas — el **sello**, la **regla de no reescribir** y la **comprobación del desfase**.

### El ritual, y son cinco pasos

1. **Copia** este archivo al proyecto.

2. **Sella la copia y declara los dos ejes.** En su cabecera, la versión se sustituye por esto:

   ```markdown
   > **Copiada de la guía global, versión <N>** · el <AAAA-MM-DD>
   > **A. Quién construye:** orquestador + workers
   > **B. ¿El producto llama a un modelo en producción?:** no
   > Lo que se dejó fuera está en la tabla de exclusiones, al final.
   ```

   ⚠️ **Los ejes se declaran ANTES de podar, no después.** Declarados al final describen lo que
   borraste; declarados antes deciden qué se borra. Es el mismo argumento que `RR-008` hace con el
   criterio: lo que se define después de ver el resultado no es una definición.

3. **Borra lo que no aplica**, receta entera, sin dejar el título huérfano. Con los ejes
   declarados esto deja de ser un juicio y pasa a ser mecánico:

   | Si el eje A es… | Se borra |
   |---|---|
   | una persona | `RR-008`, y con él `RR-009` y `RR-010` |
   | una sesión de IA sola | 🅰️ `RR-009` y `RR-010`, si nunca reparte trabajo |
   | orquestador + workers | nada del eje A |

   | Si el eje B es… | Se borra |
   |---|---|
   | no | el 🅱️ Anexo B entero |
   | sí | nada del eje B |

4. **Escribe la tabla de lo que se dejó fuera, con su motivo.** Un salto sin motivo escrito se lee
   como veredicto sobre lo saltado. Esta tabla es la que evita que dentro de tres meses alguien
   —tú— piense que se olvidó.

   ```markdown
   | Receta | Por qué no aplica en este proyecto |
   |---|---|
   | `RR-008` | aquí no teclea ningún agente |
   ```

5. **Aterriza cada receta que se queda**, en un bloque **debajo** de ella y marcado como propio:
   `RR-002` con las preguntas de tu dominio, `RR-004` con tus dos o tres comandos peligrosos,
   `RR-006` con tus bordes reales.

### 🔑 En la copia se borra y se añade — nunca se reescribe

| En la copia se puede… | |
|---|---|
| **Borrar** una receta entera que no aplica | ✅ es la razón de ser del ritual |
| **Añadir** debajo el aterrizaje al proyecto | ✅ marcado, para que se distinga de lo copiado |
| **Reescribir** el cuerpo de una receta que se queda | ❌ **nunca** |
| **Crear** una receta con un código nuevo | ❌ **nunca** — los códigos los asigna la global ([§1](#los-códigos-son-estables-y-un-hueco-es-información)) |

**Por qué lo tercero está prohibido, aunque parezca inofensivo.** Una frase distinta dentro de una
receta puede ser tres cosas —una mejora tuya, una adaptación local, o texto viejo de una versión
anterior— y **las tres se ven exactamente igual.** Cuando algo no se puede distinguir, se deja de
mirar.

Con la regla puesta, cada diferencia tiene una sola lectura posible:

| Lo que ves al comparar | Qué significa, sin dudar |
|---|---|
| falta una receta | se podó a propósito → está en la tabla de exclusiones |
| hay texto extra debajo de una receta | es el aterrizaje a ese proyecto |
| una receta dice algo distinto | **error**: o la copia está atrasada, o alguien la reescribió |
| hay una receta que la global no tiene | **error**: un código inventado en la copia. O es transversal y sube aquí, o no era del recetario |

> 🚨 **Y esto es lo que la regla compra de verdad.** Si trabajando descubres que una receta está
> mal, **no la arreglas en tu copia**: la arreglas aquí, en la global, subes la versión, anotas su
> línea en el `changelog.md` y vuelves a copiar. **Una corrección que solo vive en un proyecto es
> una corrección que los demás nunca tendrán.**

### La comprobación del desfase

El sello no sirve de nada si nadie lo mira. Al volver a un proyecto son dos números:

```
versión de la guía global   ->  7
versión de la copia         ->  3     <- atrasada
```

Si no coinciden, se leen las líneas del `changelog.md` que hay en medio —una por versión— y se
decide si se re-copia. **Es la comprobación más barata de todo este archivo**, y por eso es la
única que se puede exigir cada vez.

⚠️ **Si ese momento no tiene dueño ni sitio, no ocurrirá.** Es lo mismo que avisa `RR-002` de las
tres preguntas: lo que «ya se hará» se cobra solo cuando ya hay algo que perder. Dónde vive esa
comprobación lo decide cada proyecto, y **se decide el día que se copia la guía, no después**.

⚠️ **Ningún número de otro proyecto se copia.** Sus cifras se midieron en otra máquina, con otro
stack. Donde haga falta un umbral, se mide en el proyecto o se registra como suposición con su
forma de comprobarla.
