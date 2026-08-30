# changelog.md — Qué cambió en cada versión de `guide.md`

> **Para qué existe.** Cuando la copia de un proyecto dice *versión 3* y la global dice *versión 7*,
> este archivo es lo que se lee para saber qué te perdiste — **sin volver a leer la guía entera.**
>
> **Su regla:** una línea por versión, la más reciente arriba. Si una versión necesita un párrafo,
> el cambio era demasiado grande para una sola versión.

---

| Versión | Fecha | Qué cambió |
|---|---|---|
| **5** | 2026-08-30 | Cabecera — se le quitan las fechas: la de cada version vive en su linea de aqui y no se repite. El sello de la copia pasa a marcadores (`<N>`, `<AAAA-MM-DD>`). §1 — nombra su unica excepcion: el dia que se copia si se lee entera, y el tamano se mide contra ese dia |
| **4** | 2026-08-30 | §1 — anadido el criterio de admision («Que merece ser una receta»: cuatro filtros, y el presupuesto es el indice, no el numero de recetas). Nueva `RR-013` — como se deshace algo ya publicado |
| **3** | 2026-08-30 | §1 — anadida la regla de estabilidad de los codigos: los `RR-NNN` los asigna solo la global, no se renumeran ni se reutilizan, un hueco es informacion, y una copia nunca inventa un codigo nuevo |
| **2** | 2026-08-30 | `RR-003` — la subseccion «Auditar el historial» baja los patrones ya anclados de los tres barridos, con el porque de cada anclaje y el aviso 💻 de sensibilidad a mayusculas. Los comandos de shell no bajan: la receta sigue sin elegir herramienta |
| **1** | 2026-08-28 | Punto de partida. 12 recetas (`RR-001`…`RR-012`), Anexo A (modelos en la construccion), Anexo B (el producto llama a un modelo) y Anexo C (Windows). Se retira la pareja `lessons-global.md`: el porqué va dentro de cada receta. Se añade el sello de versión, este registro, y la regla de que en la copia se borra y se añade pero nunca se reescribe. La fuente se congela en `sources/GUIDE.md` y las flechas `↳` se anclan por título además del número. |

---

## Cómo se anota una versión nueva

**Sube la versión cuando cambia el fondo de una receta** — lo que hay que hacer, o por qué. Una
errata, una coma o un enlace arreglado **no suben versión**: si cualquier retoque la sube, el número
deja de significar «esto te afecta» y las copias empiezan a ignorarlo.

La línea nombra **la receta tocada y el cambio**, no la intención:

```
| 8 | 2026-09-14 | `RR-006` — añadida la regla 7: el estado de partida se afirma, no se supone |
| 7 | 2026-09-02 | `RR-003` — borrado el tercer barrido: daba falsos positivos por el autor del commit |
```

⚠️ **Se anota en la misma pasada que el cambio, nunca después.** Un cambio sin su línea aquí es un
cambio que las copias no sabrán que existe — y la copia seguirá diciendo que está al día.
