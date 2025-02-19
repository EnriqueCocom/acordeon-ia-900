# Práctica 2: Entrenamiento de un Modelo de Regresión Simple en Python  
**Objetivo:** Aplicar los fundamentos del aprendizaje automático entrenando un modelo de regresión utilizando scikit‑learn.

#### Paso a Paso:

1. **Preparar el entorno:**
   - Asegúrate de tener instalado Python (preferiblemente 3.x) y crea un entorno virtual.
   - Instala las librerías necesarias:
     ```bash
     pip install numpy pandas scikit-learn matplotlib
     ```

2. **Cargar y preparar los datos:**
   - En este ejemplo utilizaremos el dataset de diabetes, disponible en scikit‑learn.
   - Crea un archivo `regresion.py` y agrega el siguiente código:
     ```python
     import numpy as np
     import pandas as pd
     from sklearn.datasets import load_diabetes
     from sklearn.model_selection import train_test_split
     from sklearn.linear_model import LinearRegression
     from sklearn.metrics import mean_squared_error
     import matplotlib.pyplot as plt

     # Cargar el dataset
     diabetes = load_diabetes()
     X = diabetes.data
     y = diabetes.target

     # Dividir en conjunto de entrenamiento y prueba (80% entrenamiento, 20% prueba)
     X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

     # Crear y entrenar el modelo de regresión lineal
     modelo = LinearRegression()
     modelo.fit(X_train, y_train)

     # Realizar predicciones en el conjunto de prueba
     y_pred = modelo.predict(X_test)

     # Calcular el error cuadrático medio
     mse = mean_squared_error(y_test, y_pred)
     print(f"Error Cuadrático Medio: {mse:.2f}")

     # Graficar los valores reales vs. los predichos (para una característica, por ejemplo, la primera)
     plt.scatter(X_test[:, 0], y_test, color='blue', label='Valores reales')
     plt.scatter(X_test[:, 0], y_pred, color='red', label='Predicciones')
     plt.xlabel('Característica 1')
     plt.ylabel('Target')
     plt.legend()
     plt.title('Regresión Lineal Simple')
     plt.show()
     ```
3. **Ejecutar y analizar:**
   - Ejecuta el script:
     ```bash
     python regresion.py
     ```
   - Observa la salida en la consola (el error) y la gráfica generada. Analiza cómo se han dividido los datos (features y labels) y cómo el modelo se ha entrenado y evaluado.