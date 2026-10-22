# Crear y cambiar software

Aplica las cinco fases de la metodología. El ciclo de cambio comienza
con comportamiento o trabajo existente; puede afectar decisiones, flujos,
tareas y código. Modifica solo lo que necesite el cambio.

## Clasificar el trabajo

| Trabajo | Qué revisar |
|---|---|
| Crear una funcionalidad | Necesidad, flujos relacionados y componentes reutilizables |
| Ampliar o corregir comportamiento | Diferencia entre lo actual y lo propuesto, reglas y resultados |
| Cambiar una decisión | Flujos que la utilizan, implementación y tareas afectadas |
| Ajustar una tarea | Criterios, contexto y dependencias; verificar si cambia el diseño |
| Refactorizar | Implementación y pruebas; conservar comportamiento y actualizar referencias |
| Retirar comportamiento | Código, flujos conectados, decisiones compartidas y tareas pendientes |

## Separar lo vigente de la propuesta

Una rama representa una unidad de cambio que puede revisarse y validarse
por separado. Puede corresponder a una tarea o reunir varias tareas.
Los artefactos y el código afectados acompañan esa unidad.

Antes de editar la propuesta o implementar, define el resultado comprobable
de la rama. Si varias tareas necesitan completarse juntas para conseguirlo,
comparten rama. Si una tarea puede validarse e integrarse de forma independiente,
puede tener su propia rama. Divide cambios amplios en unidades coherentes;
no crees una rama automáticamente por cada tarea o artefacto.

Utiliza una rama de Git para desarrollar el cambio. La rama principal del
proyecto conserva la especificación y el código integrados. La rama de trabajo
contiene la propuesta y su implementación.

Reutiliza una rama adecuada si el trabajo ya está aislado. Identifica la rama
principal y el estado de trabajo antes de cambiar de rama. Conserva cambios
ajenos; no los descartes ni cambies de rama de forma que los pierda el usuario.
Si falta Git, establece el control de versiones antes de usar este procedimiento.

El agente crea la rama al comenzar el trabajo autorizado. Si el usuario ya
preparó una rama adecuada, reutilízala. Para discutir una idea sin editar
archivos, no hace falta crear una rama.

Identifica la rama principal real del proyecto; no asumas que se llama
`main`. Parte de ella para un cambio independiente. Si el trabajo depende
de otra rama, revisa esa dependencia antes de elegir la base.

### Nombres de ramas

Respeta la convención existente del proyecto. Si no tiene una, usa
`tipo/descripcion-del-cambio`, en minúsculas y con palabras separadas
por guiones.

| Tipo | Uso | Ejemplo |
|---|---|---|
| `feat` | Agregar o ampliar comportamiento | `feat/recomendar-laptops` |
| `fix` | Corregir comportamiento incorrecto | `fix/limite-presupuesto` |
| `refactor` | Reorganizar implementación conservando comportamiento | `refactor/consulta-catalogo` |
| `docs` | Cambiar instrucciones o documentación sin modificar comportamiento | `docs/ajustar-metodologia` |

Nombra el resultado o el cambio concreto, no los artefactos que contiene.
Por ejemplo, `feat/recomendar-laptops` puede reunir varias tareas y
modificaciones de flujos y decisiones.

Modifica los artefactos en la rama de trabajo. Evita notas duplicadas como
Flujo nuevo o Flujo versión 2. El historial y la separación de versiones
corresponden a Git.

Un refactor que conserva el comportamiento no obliga a reescribir el flujo.
Un cambio de comportamiento sí requiere actualizar su especificación.
Git por sí solo no elimina conflictos entre propuestas concurrentes.

## Analizar el impacto

1. Localiza los artefactos de partida y compara el resultado actual con el
   solicitado.
2. Si cambia una decisión, consulta los flujos que la enlazan.
3. Para cada flujo afectado, revisa sus puntos de entrada `codigo:`, los
   flujos conectados y las pruebas pertinentes.
4. Sigue las dependencias relevantes, incluido el código compartido. Las
   relaciones documentadas no garantizan encontrar todo el impacto.
5. Consulta las tareas relacionadas y su contexto adicional. Determina cuáles
   siguen siendo válidas, cuáles necesitan ajustes y cuáles deben retirarse.
6. Crea el trabajo que falta y define cómo comprobar los comportamientos
   afectados.

No necesitas conservar tareas terminadas para localizar la implementación:
sus puntos de entrada pertenecen al flujo. Tampoco mantengas en el flujo
un inventario de todos los archivos.

Si un cambio afecta varios flujos, prepara tareas para sus responsabilidades
y comprueba las conexiones entre ellos. No dupliques una tarea solo para
enlazarla desde varios sitios.

## Diseñar y preparar

Usa la skill `flujo` cuando cambie el comportamiento. Actualiza las decisiones
aplicables y conserva sus enlaces desde los flujos. Una tarea obtiene esas
decisiones a través de su flujo.

Marca el flujo propuesto como `en-diseño` mientras queden elecciones o reglas
sin resolver y como `listo` cuando sea comprobable y sus decisiones estén
resueltas. No cambies el estado de un flujo solo por un refactor que mantiene
su comportamiento.

Las tareas consultan los puntos de entrada del flujo y añaden únicamente
el contexto que necesiten. Comprueba las dependencias antes de implementarlas.

## Validar e integrar

Crear una rama prepara el trabajo; no autoriza por sí solo su integración.
Respeta las autorizaciones y reglas de revisión del proyecto para publicar
o hacer merge.

Verifica el resultado nuevo y los comportamientos que deben conservarse.
En un refactor, comprueba entradas, salidas, errores y reglas existentes.

Antes de integrar:

- Actualiza las referencias cuando cambien archivos o puntos de entrada.
- Comprueba decisiones aplicables, enlaces y resultados del flujo.
- Verifica que las tareas afectadas no describan trabajo incompatible.
- Revisa los cambios concurrentes que puedan invalidar el análisis.
- Prepara especificación y código correspondientes para integrarlos juntos.

Un flujo puede marcarse `vigente` cuando su implementación en esa versión
esté verificada. La rama principal solo recibe esa versión tras la integración.
Este estado no afirma que haya sido desplegada a usuarios.

Retira flujos eliminados y decisiones que ya no aplican cuando el código
integrado refleje su retiro. Revisa los enlaces antes de eliminarlos. Conserva
una decisión si otros flujos todavía la utilizan.

Las tareas verificadas pueden retirarse tras integrar el cambio y reconciliar
la especificación. Conserva su historia en Git y evita depender de ellas como
única referencia de implementación.
