# Tema Complementario 2: Comparación entre Aprendizaje Automático Tradicional y Deep Learning

### Descripción  
Este tema profundiza en las diferencias fundamentales entre los algoritmos de machine learning tradicionales (como regresión, árboles de decisión, SVM) y las técnicas de deep learning, que utilizan redes neuronales profundas. Se analiza cuándo es más adecuado utilizar cada enfoque en función del problema, los datos y los recursos disponibles.

### Aspectos Clave

1. **Definición y Diferencias:**
   - **Algoritmos Tradicionales:**  
     Se basan en modelos estadísticos y reglas predefinidas. Son interpretables y generalmente requieren menos datos para entrenar.
   - **Deep Learning:**  
     Emplea redes neuronales con múltiples capas para extraer características complejas. Es ideal para tareas como reconocimiento de imágenes y procesamiento de lenguaje natural, pero requiere gran cantidad de datos y potencia computacional.
   - **Ejemplo Práctico Comparativo:**  
     - Implementar un clasificador simple usando una regresión logística versus una red neuronal en Python (usando scikit‑learn y TensorFlow/Keras).
     - **Código Base para Regresión Logística (Tradicional):**
       ```python
       from sklearn.linear_model import LogisticRegression
       model = LogisticRegression()
       model.fit(X_train, y_train)
       accuracy_trad = model.score(X_test, y_test)
       print(f"Exactitud (Tradicional): {accuracy_trad:.2f}")
       ```
     - **Código Base para Red Neuronal (Deep Learning):**
       ```python
       from tensorflow.keras.models import Sequential
       from tensorflow.keras.layers import Dense
       model = Sequential([
           Dense(64, activation='relu', input_shape=(X_train.shape[1],)),
           Dense(64, activation='relu'),
           Dense(1, activation='sigmoid')
       ])
       model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
       model.fit(X_train, y_train, epochs=50, batch_size=32, verbose=0)
       loss, accuracy_dl = model.evaluate(X_test, y_test, verbose=0)
       print(f"Exactitud (Deep Learning): {accuracy_dl:.2f}")
       ```

2. **Ventajas y Limitaciones:**  
   - **Tradicional:**  
     - *Ventajas:* Interpretabilidad, menor requerimiento de datos, entrenamiento más rápido.  
     - *Limitaciones:* Menor capacidad para capturar patrones complejos.
   - **Deep Learning:**  
     - *Ventajas:* Gran capacidad para modelar relaciones no lineales y características complejas.  
     - *Limitaciones:* Necesita grandes volúmenes de datos, alto consumo de recursos, difícil interpretabilidad.

3. **Aplicación en Azure:**  
   - **Azure Machine Learning:**  
     Soporta ambos enfoques. Se pueden crear experimentos utilizando pipelines que integren modelos tradicionales y de deep learning.  
   - **Ejemplo de Caso de Uso:**  
     Un proyecto de análisis de imágenes en Azure puede utilizar un modelo de deep learning para extraer características visuales y luego aplicar un clasificador tradicional para la decisión final, combinando lo mejor de ambos mundos.