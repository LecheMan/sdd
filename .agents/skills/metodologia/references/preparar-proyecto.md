# Preparar el proyecto

Si el proyecto no tiene `workspace/`, montarlo antes de cualquier otra cosa.

**1. Crear las carpetas**

```
workspace/areas/  workspace/flujos/  workspace/decisiones/
workspace/tareas/
```

**2. Copiar los archivos de `assets/` de esta skill**

| Origen en la skill | Destino en el proyecto |
|---|---|
| `assets/Panel.md` | `workspace/Panel.md` |
| `assets/tablero.base` | `workspace/tablero.base` |
| `assets/flujo-tareas.base` | `workspace/flujo-tareas.base` |
| `assets/area-flujos.base` | `workspace/area-flujos.base` |

Los `.base` definen las vistas iniciales de Obsidian. Ajusta sus consultas
cuando cambien las propiedades utilizadas, mediante la skill `obsidian-bases`.

Las plantillas permanecen en las skills. Al crear un artefacto, lee la
plantilla correspondiente, completa su contenido y guarda el resultado
directamente en su carpeta del workspace. No copies las plantillas al proyecto.

**3. Preguntar al usuario sus áreas**

Identifica los dominios del producto con el usuario. Crea una nota por área en `workspace/areas/` desde
`assets/plantillas/area.md` de esta skill, y añadir cada una como wikilink bajo `## Áreas` en
`Panel.md`. Esa es la única lista que se mantiene a mano en todo el sistema.

**4. Preparar Obsidian**

Comprueba que Obsidian y las skills indicadas al inicio estén disponibles.
Registra `workspace/` como vault del proyecto si todavía no está registrado.
Consulta `obsidian-cli` para las operaciones que requieran la aplicación.

Después de abrir el vault una vez, copia `assets/graph.json` a
`workspace/.obsidian/graph.json` si no existe una configuración del proyecto.
No sobrescribas una configuración existente. La vista usa colores por tipo
de artefacto.

**5. Avisar de `.gitignore`**

`workspace/.obsidian/workspace.json` guarda estado de la interfaz y cambia al
mover cualquier panel. Conviene ignorarlo para que no ensucie los diffs.

