# Práctica 4: Desplegar un Modelo de Clasificación con Azure Machine Learning Studio  
**Objetivo:** Utilizar Azure Machine Learning para entrenar y desplegar un modelo de clasificación (por ejemplo, con el dataset Iris).

#### Paso a Paso:

1. **Crear un Workspace en Azure Machine Learning:**
   - Inicia sesión en [Azure ML Studio](https://ml.azure.com) y crea un nuevo Workspace si aún no lo tienes.

2. **Crear un Experimento:**
   - Dentro de tu Workspace, crea un nuevo "Pipeline" o "Experiment".
   - Importa el dataset Iris (puedes cargar un CSV o usar un dataset integrado si está disponible).

3. **Preparar y dividir los datos:**
   - Agrega un módulo para dividir el dataset en conjuntos de entrenamiento y prueba (por ejemplo, 70% entrenamiento, 30% prueba).

4. **Seleccionar y entrenar un modelo:**
   - Agrega un módulo de "Clasificador" (por ejemplo, Árbol de Decisión o Regresión Logística).
   - Conecta el dataset dividido al módulo del clasificador y ejecuta el entrenamiento.

5. **Evaluar el modelo:**
   - Añade un módulo de “Evaluación de modelos” para medir la precisión, la matriz de confusión, etc.
   - Revisa los resultados para determinar la efectividad del modelo.

6. **Publicar el modelo como servicio web:**
   - Una vez satisfecho con el desempeño, publica el modelo seleccionando “Deploy”.
   - Sigue el asistente para generar un endpoint REST, el cual podrás consumir desde una aplicación o script.
   - **Prueba del Endpoint:** Puedes usar Postman (como en la Práctica 1) para enviar datos de prueba y obtener predicciones.