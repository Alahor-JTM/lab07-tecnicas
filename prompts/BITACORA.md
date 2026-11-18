# Bitácora de técnicas avanzadas

Laboratorio 07: Técnicas Avanzadas de Prompting. Herramienta de IA usada: (escribe aquí cual usaste)

##	Ejercicio	2:	Zero-shot, one-shot y few-shot

| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
| :--- | :---: | :--- | :---: |
| Zero-shot | 5 | Lista numerada con explicaciones o texto adicional | No |
| One-shot | 5 | Texto con flecha, pero conserva los números de lista | No |
| Few-shot | 5 | Exacto: `"comentario" -> Etiqueta` línea por línea | Si |


##	Ejercicio	3:	Chain of Thought

| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
| :--- | :--- | :---: | :---: |
| Directo | 318.60 | No | Si |
| Paso a paso | S/ 318.60 (con desglose de descuento, IGV y multiplicación) | Si | Si |

Ver el razonamiento permite auditar la lógica de la IA y verificar que aplicó las reglas en el orden correcto (primero el descuento y luego el IGV). Si hubiera un error matemático, el desglose permitiría detectar exactamente en qué paso ocurrió.

##	Ejercicio	4:	Role prompting

| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
| :--- | :--- | :--- | :--- |
| A. Sin rol | Intermedio | Ejemplo genérico de programación | Estudiantes con nociones básicas |
| B. Rol docente | Sencillo | Analogía de la vida diaria (una caja con etiqueta) | Principiantes que nunca han programado |
| C. Rol senior | Técnico | Código en Java, mención a memoria y tipos de datos | Desarrolladores o compañeros de equipo |

##	Ejercicio	5:	Descomposición

| Enfoque | Calidad y orden del codigo | Mantiene coherencia (Si/No) | Facilidad para corregir errores |
| :--- | :--- | :---: | :--- |
| Pedido de una sola vez | Código extenso, mezclado en un solo bloque o incompleto | No | Difícil, requiere revisar todo el programa |
| Pedido por pasos | Código modular, limpio y enfocado en una sola clase | Si | Fácil, se valida cada etapa antes de avanzar |

### Registro de los pasos ejecutados
* **Paso 1 (Requisitos):** La IA listó los 5 requisitos funcionales principales del inventario (registrar, actualizar stock, buscar, listar y eliminar productos).
* **Paso 2 (Diseño de clases):** Definió las clases `Producto`, `Inventario` y `Main`, respetando exactamente los requisitos del paso anterior.
* **Paso 3 (Codificación):** Generó únicamente el código de la clase `Producto.java` con sus atributos privados, constructor, getters y setters.
* **Paso 4 (Mejoras):** Al revisar su propio código en el mismo chat, propuso validaciones reales para evitar precios o cantidades de stock negativas.

### Conclusion de la tecnica
Dividir un problema grande en subtareas dentro del mismo chat permite que la IA aproveche el contexto acumulado. Esto evita que el modelo omita detalles o entregue código desordenado, facilitando la depuración paso a paso.

##	Ejercicio	6:	Prompt estructurado y autocrítica

| Qué revisar | Cumple (Si/No) |
| :--- | :---: |
| ¿Tiene las 4 columnas pedidas? | Si |
| ¿Incluye el bloqueo después de 3 intentos? | Si |
| ¿Incluye casos con campos vacíos? | Si |
| ¿Indica qué casos agregó en la autocrítica? | Si |
| ¿Hay algún caso repetido o que no tenga sentido? | No |

### Prompt Estructurado
```text
<rol>Actúa como analista de pruebas de software.</rol>
<contexto>Login web con correo y contraseña. La cuenta se bloquea
despues de 3 intentos fallidos.</contexto>
<tarea>Piensa paso a paso que puede fallar y escribe 6 casos de prueba.</tarea>
<formato>Tabla con las columnas: ID, escenario, datos de entrada,
resultado esperado.</formato>

Revisa tu tabla: faltan casos limite como campos vacios, correo sin @
o contrasena con espacios? Agrega los que falten e indica cuales agregaste.
```


