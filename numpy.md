### 1. ¿Qué es un vector?

Un **vector** es una lista ordenada de números. Puedes imaginarlo como una flecha que apunta en una dirección específica en el espacio. Por ejemplo, el vector `[2, 6, 3]` representa una flecha en el espacio tridimensional que apunta a la posición `(2, 6, 3)`.

En `numpy`, podemos crear vectores usando la función `np.array`. Aquí, `np` es la abreviatura que se usa para `numpy` (así es más corto de escribir). Observa cómo se hace:

```python
import numpy as np  # Importamos numpy y lo llamamos "np"

# Creamos un vector llamado "vector_a"
vector_a = np.array([2, 6, 3])
print(vector_a)  # Esto mostrará [2 6 3]
```

---

### 2. ¿Qué significa "linalg" en `numpy`?

`linalg` es una abreviatura para "algebra lineal" (en inglés, "linear algebra"). `numpy` tiene una sub-librería llamada `linalg` que contiene herramientas matemáticas especiales para trabajar con vectores y matrices. Cuando usamos `np.linalg`, estamos usando las funciones de álgebra lineal de `numpy`.

---

### 3. Magnitud de un vector (Norma del vector)

La **magnitud** o **norma** de un vector es una medida de su "longitud" o "tamaño". Si te imaginas el vector como una flecha en el espacio, la magnitud es la longitud de esa flecha.

Para calcularla en `numpy`, usamos `np.linalg.norm()`. 

Ejemplo:

```python
# Calcular la magnitud de "vector_a"
magnitud = np.linalg.norm(vector_a)
print(magnitud)  # Imprime la longitud del vector [2, 6, 3]
```

En este caso, `np.linalg.norm()` calcula la distancia del punto `(2, 6, 3)` hasta el origen `(0, 0, 0)`. Esto se hace usando el Teorema de Pitágoras.

---

### 4. Producto Interno (Dot Product)

El **producto interno** es una operación matemática entre dos vectores que nos dice cuánto se parecen o están "alineados" en la misma dirección. Se calcula multiplicando los elementos correspondientes y sumándolos. En `numpy`, usamos `np.dot()`.

Ejemplo:

```python
# Crear otro vector llamado "vector_b"
vector_b = np.array([1, 4, 5])

# Producto interno entre "vector_a" y "vector_b"
producto_interno = np.dot(vector_a, vector_b)
print(producto_interno)  # Muestra el resultado de multiplicar los vectores
```

Este cálculo toma los números de cada vector, los multiplica entre sí (como `2*1 + 6*4 + 3*5`) y suma los resultados. El valor final es una medida de cuánto apuntan los vectores en la misma dirección.

---

### 5. Ángulo entre dos vectores

Para encontrar el **ángulo** entre dos vectores, usamos el producto interno y las magnitudes (o longitudes) de los vectores. El coseno del ángulo se puede obtener dividiendo el producto interno entre el producto de las magnitudes.

```python
# Calcular las magnitudes de los vectores
magnitud_a = np.linalg.norm(vector_a)
magnitud_b = np.linalg.norm(vector_b)

# Calcular el coseno del ángulo
coseno_angulo = producto_interno / (magnitud_a * magnitud_b)
print(coseno_angulo)
```

El resultado que obtienes es el coseno del ángulo entre los vectores. Si quieres el ángulo en sí (en radianes), puedes usar `np.arccos(coseno_angulo)`.

---

### 6. Condición Ortogonal

Dos vectores son **ortogonales** (o perpendiculares) si el ángulo entre ellos es de 90 grados. En este caso, el producto interno entre los dos vectores es igual a cero. Podemos comprobarlo así:

```python
# Verificar si los vectores son ortogonales
if np.dot(vector_a, vector_b) == 0:
    print("Los vectores son ortogonales")  # Esto se mostrará si el producto interno es 0
else:
    print("Los vectores no son ortogonales")
```

---

### 7. Similaridad del Coseno

La **similaridad del coseno** es una medida que nos dice qué tan parecidos son dos vectores. Esta medida toma un valor entre -1 y 1:
- **1** significa que los vectores son idénticos en dirección.
- **-1** significa que los vectores son opuestos.
- **0** significa que los vectores son ortogonales.

Para calcular esta similaridad:

```python
# Calcular la similaridad del coseno
similaridad_coseno = producto_interno / (magnitud_a * magnitud_b)
print(similaridad_coseno)
```

Un valor cercano a 1 indica que los vectores apuntan en la misma dirección, mientras que un valor cercano a -1 indica que apuntan en direcciones opuestas.

---

### Resumen

1. Usamos `np.array` para crear vectores.
2. `np.linalg.norm()` nos da la magnitud (o longitud) del vector.
3. `np.dot()` calcula el producto interno entre dos vectores.
4. El coseno del ángulo entre dos vectores se puede calcular con el producto interno y las magnitudes.
5. Dos vectores son ortogonales si su producto interno es cero.
6. La similaridad del coseno mide qué tan parecidos son dos vectores.
