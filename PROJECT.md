# PROJECT.md

> **Los datos propios de este proyecto, en un solo sitio.** Todo lo que en los protocolos, agentes
> y `CLAUDE.md` aparece como «el proyecto», «el repositorio del auditor» o «el canal de vuelta» se
> resuelve aqui.
>
> 🔑 **Es lo unico que cambia al llevar este metodo a otro proyecto.** Si un archivo necesita saber
> un nombre o una ruta, lo lee de aqui en vez de llevarlo escrito dentro.

---

## Identidad

| Campo | Valor |
|---|---|
| Nombre del proyecto | AIzar |
| Terminal ejecutora | `executor` |
| Terminal auditora | `auditor` |
| Idioma de trabajo | Espanol |

## Rutas

| Campo | Valor |
|---|---|
| Repositorio del proyecto | `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_App` |
| Repositorio del auditor | `C:\Users\USUARIO\Documents\Company_TripleS\Proyectos_TripleS\AIzar_Auditor` |
| Canal de vuelta (tablero de auditorias) | `..\AIzar_Auditor\_review\index.md` |
| Auditorias en detalle | `..\AIzar_Auditor\_review\R-XXX.md` |

🚨 El repositorio del auditor es de **solo lectura** para nosotros (restriccion C-002).

## Control de versiones

| Campo | Valor |
|---|---|
| Remoto | `https://github.com/jdrodriguez1000/AIzar_APP.git` |
| Rama principal | `main` |

## Carpetas propias

| Carpeta | Que es |
|---|---|
| `_persistence/` | El estado del proyecto: siete archivos, indice arriba y detalle debajo |
| `_audit/` | Informes que entregamos a la auditoria, mas su `index.md` |
| `temporal/` | Area de trabajo del usuario. **Fuera del repositorio** (D-015) y fuera del registro |

## Codigos

| Codigo | Archivo | Que es |
|---|---|---|
| `S-XXX` | `_persistence/progress.md` | sesion de trabajo |
| `H-nn` | `_persistence/progress.md` | hito |
| `T-XXX` | `_persistence/tasks.md` | tarea |
| `D-XXX` | `_persistence/decisions.md` | decision |
| `C-XXX` | `_persistence/constraints.md` | restriccion |
| `A-XXX` | `_persistence/assumptions.md` | supuesto |
| `L-XXX` | `_persistence/lessons.md` | leccion aprendida |
| `DT-XXX` | `_persistence/debt_tec.md` | deuda tecnica |
| `F-NNN` | del auditor | hallazgo de auditoria |

---

## Que NO va en este archivo

⚠️ **Solo lo estable.** Si algo cambia de una sesion a otra —la etapa, el avance, las tareas
abiertas, los bloqueos— **no va aqui: va en `_persistence/progress.md`**.

Un archivo de identidad que hay que actualizar cada jornada deja de ser fiable, porque nadie
recuerda mantenerlo y todos lo siguen citando.
