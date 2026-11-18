# Tarea: Mi prompt avanzado

## Tarea elegida
Diseñar la estructura de clases en Java para un sistema de registro de notas académicas con cálculo de promedios y estado de aprobación.

## Versión 1: prompt básico

```text
Disena las clases para un sistema de notas en Java.
```

* **Técnica agregada:** Ninguna (prompt básico inicial).
* **Por qué y qué mejoró:** Se usó como línea base. La IA respondió con clases muy generales, sin especificar tipos de datos exactos ni reglas de negocio para aprobar o desaprobar.

## Versión 2

```text
Actua como arquitecto de software Java senior que disena sistemas para una institucion educativa. Disena las clases necesarias para un sistema de registro de notas donde un estudiante tiene 3 evaluaciones (peso 30%, 30% y 40%) y aprueba con nota minima de 13. Presenta cada clase en una tabla con: Nombre de clase, Atributos (con tipo de dato) y Metodos principales.
```

* **Técnicas agregadas:** Role prompting y definición de contexto/formato.
* **Por qué y qué mejoró:** Al definir un rol específico (arquitecto Java senior para institución educativa) y exigir una tabla estructurada, la IA eliminó texto innecesario y definió los tipos de datos (`String`, `double`) y los métodos de cálculo exactos.

## Version 3: prompt final

```text
<rol>Actúa como arquitecto de software Java senior especializado en sistemas académicos.</rol>
<contexto>Se desarrollará un modulo de registro de notas en consola. Cada estudiante tiene código, nombre y 3 notas (Práctica 1: 30%, Práctica 2: 30%, Examen Final: 40%). La nota mínima aprobatoria es 13.0 en escala vigesimal (0 a 20).</contexto>
<tarea>Analiza paso a paso que validaciones de negocio se necesitan para evitar notas fuera de rango. Luego disena las clases necesarias indicando atributos con su tipo de dato y metodos principales.</tarea>
<formato>Presenta el diseño en una tabla Markdown con las columnas: Clase, Atributos y tipos de dato, Metodos y responsabilidades.</formato>
<autocritica>Revisa tu diseño: omitiste alguna validacion para notas negativas o mayores a 20, o algun metodo para listar estudiantes desaprobados? Agrega lo que falte al final e indica que agregaste.</autocritica>
```

* **Técnicas agregadas:** Prompt estructurado (etiquetas XML), Chain of Thought ("Analiza paso a paso") y Autocrítica.
* **Por qué y qué mejoró:** Las etiquetas separaron claramente las reglas del formato. El razonamiento paso a paso obligó a la IA a prever errores de rango antes de armar la tabla, y la autocrítica añadió métodos de consulta que faltaban.

## Técnicas usadas en el prompt final

| Técnica | Parte del prompt donde se aplica |
| :--- | :--- |
| Role prompting | Etiqueta `<rol>`: asigna el perfil de arquitecto de software Java senior. |
| Prompt estructurado | Uso de las etiquetas `<rol>`, `<contexto>`, `<tarea>`, `<formato>` y `<autocritica>`. |
| Chain of Thought | Etiqueta `<tarea>`: instrucción "Analiza paso a paso que validaciones de negocio se necesitan...". |
| Autocrítica | Etiqueta `<autocritica>`: instrucción para revisar omisiones en validaciones y métodos. |

## Evaluación del resultado

| Criterio | Cumple (Si/No) |
| :--- | :---: |
| ¿Respeta exactamente las 3 columnas solicitadas en la tabla? | Si |
| ¿Aplica correctamente los pesos (30%, 30%, 40%) y la nota mínima de 13? | Si |
| ¿Incluye validaciones para notas fuera del rango 0 a 20? | Si |
| ¿La autocrítica identificó y agregó elementos útiles al diseño? | Si |

## Por que elegí estas técnicas
Elegí el **Prompt estructurado** porque el problema tenía varias reglas matemáticas y de negocio que podían mezclarse en un párrafo normal. Combiné **Role prompting** con **Chain of Thought** para que el modelo razonara las validaciones críticas con criterio técnico antes de proponer las clases, y añadí **Autocrítica** para asegurar que no quedaran métodos de consulta pendientes en el diseño final.
