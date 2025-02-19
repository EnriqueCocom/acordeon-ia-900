# Introducción a Python

## 1. ¿Qué es Python y por qué aprenderlo?

**Python** es un lenguaje de programación interpretado, de alto nivel y de propósito general. Es popular por su sintaxis clara y legible, lo que lo hace ideal para principiantes, pero también es muy poderoso para aplicaciones avanzadas, como el análisis de datos, la inteligencia artificial y el desarrollo web.

- **Características clave:**
  - **Fácil de aprender:** La sintaxis se asemeja al lenguaje natural.
  - **Multiplataforma:** Funciona en Windows, macOS y Linux.
  - **Gran comunidad y muchas librerías:** Existen paquetes para matemáticas, IA (como TensorFlow y PyTorch), análisis de datos (pandas, NumPy) y mucho más.

---

## 2. Instalación y Entorno de Trabajo

### Instalación
- **Descarga:** Ve a [python.org](https://www.python.org/downloads/) y descarga la versión más reciente (recomendada para principiantes).
- **Instalación:** Sigue el asistente; asegúrate de marcar la opción "Add Python to PATH" para poder usar Python desde la línea de comandos.
- **Gestión de paquetes:** Python utiliza `pip` para instalar paquetes adicionales.  
  Ejemplo:  
  ```bash
  pip install numpy
  ```

### Entornos de Desarrollo
- **IDLE:** El entorno de desarrollo básico que viene con Python.
- **Jupyter Notebook:** Ideal para escribir y ejecutar código de forma interactiva, muy utilizado en ciencia de datos.
- **Visual Studio Code (VSCode):** Un editor de código muy popular con extensiones para Python.

---

## 3. Sintaxis Básica de Python

### 3.1 Variables y Tipos de Datos

En Python, no es necesario declarar el tipo de variable; se asigna dinámicamente.

- **Variables numéricas:**  
  ```python
  a = 5           # Entero
  b = 3.14        # Flotante (número real)
  ```
- **Cadenas de texto (strings):**  
  ```python
  nombre = "Juan"
  ```
- **Booleanos:**  
  ```python
  verdad = True   # También False
  ```
- **Ejemplo de asignación y uso:**
  ```python
  x = 10
  y = 20
  suma = x + y
  print("La suma es:", suma)  # Imprime: La suma es: 30
  ```

### 3.2 Operadores y Expresiones

Los operadores en Python se usan para realizar cálculos y comparaciones.

- **Aritméticos:** \(+,-,*,/,\, \%\) (módulo), \(**\) (potencia).  
  Ejemplo:
  ```python
  # Suma, resta, multiplicación, división y potencia
  a = 4
  b = 2
  print(a + b)  # 6
  print(a - b)  # 2
  print(a * b)  # 8
  print(a / b)  # 2.0
  print(a ** b) # 16
  print(a % b)  # 0  (residuo de 4 dividido entre 2)
  ```

- **Comparación:** \(==, !=, >, <, >=, <=\).  
  Ejemplo:
  ```python
  if a > b:
      print("a es mayor que b")
  ```

- **Lógicos:** `and`, `or`, `not`.  
  Ejemplo:
  ```python
  if a > 0 and b > 0:
      print("Ambos son positivos")
  ```

---

## 4. Estructuras de Control

### 4.1 Condicionales

Permiten ejecutar bloques de código según condiciones.

```python
x = 10
if x > 0:
    print("x es positivo")
elif x == 0:
    print("x es cero")
else:
    print("x es negativo")
```

**Explicación:**
- `if` evalúa la condición \(x > 0\).
- `elif` (else if) evalúa condiciones adicionales.
- `else` se ejecuta si ninguna condición anterior se cumple.

### 4.2 Bucles

Permiten repetir instrucciones.

#### Bucle for:
```python
# Imprimir números del 0 al 4
for i in range(5):
    print(i)
```
- `range(5)` genera una secuencia de números de 0 a 4.

#### Bucle while:
```python
contador = 0
while contador < 5:
    print(contador)
    contador += 1  # Incrementa contador en 1
```

---

## 5. Funciones

Las funciones agrupan código para reutilizarlo y organizar programas.

### Definición de Función
```python
def saludar(nombre):
    """
    Esta función saluda a la persona cuyo nombre se le pasa como argumento.
    """
    return f"Hola, {nombre}!"

# Uso de la función
mensaje = saludar("Ana")
print(mensaje)  # Imprime: Hola, Ana!
```

### Ejemplo: Cálculo del Factorial

El factorial de \( n \) se define como:
\[
n! = n \times (n-1) \times (n-2) \times \dots \times 1 \quad \text{y} \quad 0! = 1
\]

#### Función Recursiva para Factorial
```python
def factorial(n):
    # Caso base: el factorial de 0 es 1
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)

# Ejemplo: Calcular 5!
resultado = factorial(5)
print("5! =", resultado)  # Imprime: 5! = 120
```

**Explicación paso a paso:**
- Si \( n = 5 \), se evalúa \( 5 \times factorial(4) \).
- \( factorial(4) = 4 \times factorial(3) \), y así sucesivamente hasta \( factorial(0) = 1 \).
- Se multiplica: \( 5 \times 4 \times 3 \times 2 \times 1 = 120 \).

---

## 6. Estructuras de Datos

### 6.1 Listas

Una lista es una colección ordenada y mutable de elementos.
```python
numeros = [1, 2, 3, 4, 5]
print(numeros[0])  # Imprime: 1 (primer elemento)
numeros.append(6)  # Agrega 6 al final de la lista
```

### 6.2 Tuplas

Una tupla es similar a una lista pero inmutable.
```python
coordenadas = (10, 20)
# No se pueden modificar sus elementos una vez creada
```

### 6.3 Diccionarios

Los diccionarios almacenan pares clave-valor.
```python
estudiante = {"nombre": "Carlos", "edad": 21, "carrera": "Matemáticas"}
print(estudiante["nombre"])  # Imprime: Carlos
```

### 6.4 Conjuntos (Sets)

Los conjuntos son colecciones de elementos únicos.
```python
frutas = {"manzana", "banana", "naranja"}
frutas.add("kiwi")
print(frutas)  # Imprime el conjunto (el orden no está garantizado)
```

---

## 7. Módulos y Librerías

Python cuenta con una extensa colección de módulos y librerías que amplían sus funcionalidades.

### 7.1 Importar un Módulo
```python
import math
# Uso de la función sqrt del módulo math para calcular la raíz cuadrada
numero = 16
raiz = math.sqrt(numero)
print("La raíz cuadrada de", numero, "es", raiz)  # Imprime: La raíz cuadrada de 16 es 4.0
```

### 7.2 Librerías para Matemáticas y Ciencia de Datos
- **NumPy:** Para operaciones avanzadas con matrices y funciones matemáticas.  
  Ejemplo:
  ```python
  import numpy as np
  # Crear un array de NumPy
  arr = np.array([1, 2, 3, 4, 5])
  print(arr * 2)  # Multiplica cada elemento por 2
  ```
- **Pandas:** Para manejo de datos en forma de tablas (DataFrames).

---

## 8. Ejemplo Completo: Cálculo de la Media y Desviación Estándar

Vamos a crear un programa en Python que calcule la media y la desviación estándar de una lista de números. Usaremos las siguientes fórmulas:

### Fórmulas Matemáticas
- **Media (\( \mu \)):**
  \[
  \mu = \frac{1}{n} \sum_{i=1}^{n} x_i
  \]
  Donde:
  - \( n \) es el número de elementos.
  - \( x_i \) son los valores de la lista.

- **Desviación Estándar (\( \sigma \)):**
  \[
  \sigma = \sqrt{\frac{1}{n} \sum_{i=1}^{n}(x_i - \mu)^2}
  \]
  Donde:
  - \( (x_i - \mu)^2 \) es el cuadrado de la diferencia entre cada elemento y la media.

### Código en Python
```python
import math

# Lista de números
datos = [2, 4, 4, 4, 5, 5, 7, 9]

# Calcular la media
n = len(datos)                # Número total de elementos
suma = sum(datos)             # Suma de todos los elementos
media = suma / n              # Fórmula de la media: μ = (Σx_i) / n
print("Media:", media)

# Calcular la desviación estándar
suma_cuadrados = 0
for x in datos:
    suma_cuadrados += (x - media) ** 2  # Acumula (x_i - μ)^2

desviacion_estandar = math.sqrt(suma_cuadrados / n)  # σ = sqrt((Σ(x_i - μ)^2) / n)
print("Desviación Estándar:", desviacion_estandar)
```

### Explicación Paso a Paso

1. **Cálculo de la Media:**
   - Se cuenta el número de elementos \( n \) con `len(datos)`.
   - Se suma todos los valores usando `sum(datos)`.
   - La media se obtiene dividiendo la suma entre \( n \).

2. **Cálculo de la Desviación Estándar:**
   - Se inicializa una variable `suma_cuadrados` en 0.
   - Se itera sobre cada valor \( x \) en la lista y se acumula \( (x - \text{media})^2 \).
   - Se divide la suma de los cuadrados por \( n \) y se aplica la función raíz cuadrada con `math.sqrt()`.

3. **Salida:**
   - El programa imprime la media y la desviación estándar, permitiendo validar los cálculos.

