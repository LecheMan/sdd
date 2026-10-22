# Estados de los artefactos

Los estados describen la situación del trabajo en la versión consultada.
Consulta la rama principal para lo integrado y la rama de trabajo para
la propuesta. Los estados no sustituyen el historial de Git.

## Flujo

| Estado | Significado |
|---|---|
| `en-diseño` | Comportamiento en definición; faltan reglas o elecciones |
| `listo` | Especificación comprobable y decisiones resueltas; permite preparar tareas e implementar |
| `vigente` | Implementación verificada que cumple la especificación en esa versión |

No añadas un estado de implementación al flujo: las tareas muestran ese
trabajo. Si aparece una elección que modifica el comportamiento propuesto,
vuelve a `en-diseño`.

En un cambio, modifica la versión de trabajo y conserva la principal hasta
integrar. En un refactor sin cambio de comportamiento, el flujo puede conservar
su estado. `vigente` no equivale a desplegado.

Cuando se retire un comportamiento del código integrado, elimina su flujo
y corrige sus enlaces. Git conserva la versión anterior.

## Tarea

| Estado | Significado |
|---|---|
| `propuesta` | Trabajo identificado, todavía sin especificación suficiente |
| `bloqueada` | Depende de una elección pendiente del usuario |
| `lista` | Criterios y contexto definidos; decisiones aplicables resueltas |
| `en-curso` | Implementación iniciada |
| `hecha` | Criterios de aceptación comprobados |

Una tarea sin decisiones pendientes puede pasar de propuesta a lista.
Una tarea en curso vuelve a bloqueada si requiere una nueva elección.
Al pasar a hecha, completa `cerrada:` con la fecha.

El cierre no obliga a conservar la tarea permanentemente. Puede retirarse
tras integrar el cambio y actualizar la especificación y sus referencias.

## Decisión

| Estado | Significado |
|---|---|
| `abierta` | Elección pendiente, con opciones y recomendación |
| `firme` | Elección resuelta y aplicable en esa versión |

Una decisión modificada se resuelve en la rama de trabajo y se revisa en
todos los flujos afectados. Cuando deje de aplicar al código integrado,
actualiza o retira la nota y sus enlaces. Git conserva la elección anterior.

## Área

| Estado | Significado |
|---|---|
| `activa` | Con trabajo en marcha o previsto |
| `congelada` | Sin trabajo previsto |

Los estados de tarea y área mantienen su clasificación actual. Sus
procedimientos específicos pertenecen a las skills de esos artefactos.
