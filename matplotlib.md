### 1. Preparativos: ¿Qué es `matplotlib` y cómo lo usamos?

`matplotlib` es una librería de Python que nos permite crear gráficos. Dentro de `matplotlib`, la sub-librería `pyplot` facilita la creación de gráficos 2D, como los de vectores, de una forma sencilla.

Primero, necesitamos importar `matplotlib.pyplot` como `plt` para que sea más fácil de usar.

```python
import matplotlib.pyplot as plt
import numpy as np  # Necesitamos numpy para crear vectores
```

---

### 2. Representar un Vector

Imaginemos que queremos representar el vector `[2, 3]` en un plano. Para ello, necesitamos definir el origen del vector (normalmente `(0, 0)`) y el punto final, que en este caso es `(2, 3)`.

```python
# Crear un vector
vector_a = np.array([2, 3])

# Representar el vector
plt.quiver(0, 0, vector_a[0], vector_a[1], angles='xy', scale_units='xy', scale=1, color='blue')
plt.xlim(-5, 5)
plt.ylim(-5, 5)
plt.grid()
plt.show()
```

- `plt.quiver(0, 0, vector_a[0], vector_a[1], ...)`: Aquí, `(0, 0)` es el origen del vector, y `(vector_a[0], vector_a[1])` representa las coordenadas finales del vector.
- `angles='xy'`, `scale_units='xy'`, `scale=1`: Estos ajustes aseguran que el vector se represente de forma correcta en el gráfico.
- `plt.xlim(-5, 5)` y `plt.ylim(-5, 5)`: Ajustan el rango del gráfico en los ejes x e y, de -5 a 5 en este caso.
- `plt.grid()`: Muestra una cuadrícula en el gráfico para mayor claridad.
- `plt.show()`: Muestra el gráfico.

---

### 3. Representar la Magnitud de un Vector

La **magnitud** es la longitud del vector. Si quieres visualizarlo, simplemente puedes pensar en la longitud de la flecha en el gráfico. Para calcular y mostrar la magnitud, podríamos hacer algo así:

```python
# Calcular la magnitud del vector
magnitud = np.linalg.norm(vector_a)
print(f"La magnitud del vector es: {magnitud}")

# Representar el vector y la magnitud
plt.quiver(0, 0, vector_a[0], vector_a[1], angles='xy', scale_units='xy', scale=1, color='blue')
plt.xlim(-5, 5)
plt.ylim(-5, 5)
plt.grid()
plt.title(f"Vector [2, 3] con magnitud {magnitud:.2f}")
plt.show()
```

---

### 4. Representar el Producto Interno de dos Vectores

Para entender el producto interno, podemos dibujar dos vectores en el mismo gráfico. Si el producto interno es positivo, significa que apuntan en una dirección parecida; si es negativo, significa que están en direcciones opuestas.

Ejemplo con dos vectores `[2, 3]` y `[4, -1]`:

```python
# Crear los vectores
vector_a = np.array([2, 3])
vector_b = np.array([4, -1])

# Calcular el producto interno
producto_interno = np.dot(vector_a, vector_b)
print(f"El producto interno es: {producto_interno}")

# Representar los dos vectores
plt.quiver(0, 0, vector_a[0], vector_a[1], angles='xy', scale_units='xy', scale=1, color='blue', label='Vector A')
plt.quiver(0, 0, vector_b[0], vector_b[1], angles='xy', scale_units='xy', scale=1, color='red', label='Vector B')
plt.xlim(-5, 5)
plt.ylim(-5, 5)
plt.grid()
plt.legend()
plt.title(f"Producto Interno: {producto_interno}")
plt.show()
```

---

### 5. Ángulo entre dos Vectores

Para visualizar el **ángulo entre dos vectores**, podemos dibujarlos y calcular el ángulo en radianes o grados usando el coseno del ángulo. No podemos mostrar el ángulo directamente en el gráfico, pero podemos interpretarlo observando cómo están orientados los vectores.

```python
# Crear los vectores
vector_a = np.array([2, 3])
vector_b = np.array([4, -1])

# Calcular el producto interno y las magnitudes
producto_interno = np.dot(vector_a, vector_b)
magnitud_a = np.linalg.norm(vector_a)
magnitud_b = np.linalg.norm(vector_b)

# Calcular el coseno del ángulo
coseno_angulo = producto_interno / (magnitud_a * magnitud_b)
angulo = np.arccos(coseno_angulo)  # El ángulo en radianes
angulo_grados = np.degrees(angulo)  # Convertir a grados

print(f"El ángulo entre los vectores es: {angulo:.2f} radianes o {angulo_grados:.2f} grados")

# Representar los vectores
plt.quiver(0, 0, vector_a[0], vector_a[1], angles='xy', scale_units='xy', scale=1, color='blue', label='Vector A')
plt.quiver(0, 0, vector_b[0], vector_b[1], angles='xy', scale_units='xy', scale=1, color='red', label='Vector B')
plt.xlim(-5, 5)
plt.ylim(-5, 5)
plt.grid()
plt.legend()
plt.title(f"Ángulo entre A y B: {angulo_grados:.2f}°")
plt.show()
```

---

### 6. Comprobar Ortogonalidad (90° entre los vectores)

Dos vectores son ortogonales si el producto interno es cero, lo que significa que el ángulo entre ellos es de 90°. Al representarlos, se verán perpendiculares entre sí.

```python
# Vectores ortogonales
vector_a = np.array([1, 2])
vector_b = np.array([-2, 1])

# Calcular el producto interno
producto_interno = np.dot(vector_a, vector_b)
print(f"El producto interno es: {producto_interno}")

# Representar los vectores
plt.quiver(0, 0, vector_a[0], vector_a[1], angles='xy', scale_units='xy', scale=1, color='blue', label='Vector A')
plt.quiver(0, 0, vector_b[0], vector_b[1], angles='xy', scale_units='xy', scale=1, color='red', label='Vector B')
plt.xlim(-5, 5)
plt.ylim(-5, 5)
plt.grid()
plt.legend()
plt.title("Vectores Ortogonales (Producto Interno = 0)")
plt.show()
```

---

### 7. Similaridad del Coseno entre dos Vectores

Para representar la **similaridad del coseno** visualmente, simplemente podemos observar la orientación de los vectores. Si son muy similares, estarán casi en la misma dirección; si son opuestos, estarán en direcciones opuestas. Podemos mostrar el valor de la similaridad del coseno en el gráfico.

```python
# Vectores
vector_a = np.array([2, 3])
vector_b = np.array([4, 6])

# Calcular el producto interno y las magnitudes
producto_interno = np.dot(vector_a, vector_b)
magnitud_a = np.linalg.norm(vector_a)
magnitud_b = np.linalg.norm(vector_b)

# Calcular la similaridad del coseno
similaridad_coseno = producto_interno / (magnitud_a * magnitud_b)
print(f"La similaridad del coseno es: {similaridad_coseno}")

# Representar los vectores
plt.quiver(0, 0, vector_a[0], vector_a[1], angles='xy', scale_units='xy', scale=1, color='blue', label='Vector A')
plt.quiver(0, 0, vector_b[0], vector_b[1], angles='xy', scale_units='xy', scale=1, color='red', label='Vector B')
plt.xlim(-5, 5)
plt.ylim(-5, 5)
plt.grid()
plt.legend()
plt.title(f"Similaridad del Coseno: {similaridad_coseno:.2f}")
plt.show()
```
