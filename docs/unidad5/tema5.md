# Tema Complementario 5: Experimentación y Ajuste de Parámetros en Modelos Generativos

### Descripción  
La experimentación es clave para optimizar el rendimiento de los modelos generativos. Este tema profundiza en cómo ajustar parámetros como la temperatura, el número de tokens y otros hiperparámetros para mejorar la calidad y coherencia de las salidas.

### Aspectos Clave

1. **Parámetros Principales:**
   - **Temperatura:** Controla la aleatoriedad de la salida. Valores bajos producen respuestas más deterministas, mientras que valores altos aumentan la diversidad.
   - **Max_tokens:** Define la longitud máxima del texto generado.
   - **Top_p y frecuencia de penalización:** Otros parámetros que influyen en la creatividad y repetición.

2. **Proceso de Experimentación:**
   - **Configuración de Experimentos:** Crear un conjunto de prompts de prueba y definir un rango de valores para cada parámetro.
   - **Análisis de Resultados:** Evaluar las salidas mediante métricas de calidad (como coherencia, relevancia y diversidad) y feedback manual.
   - **Iteración:** Ajustar los parámetros con base en los resultados y repetir el proceso para encontrar la configuración óptima.

3. **Ejemplo Práctico: Script para Experimentar con Parámetros**
   - **Código en Python:**
     ```python
     import requests
     import json

     subscription_key = "<tu-clave>"
     endpoint = "https://<tu-endpoint>.openai.azure.com/"
     deployment_id = "<tu-deployment-id>"
     url = f"{endpoint}openai/deployments/{deployment_id}/completions?api-version=2022-12-01"

     # Función para generar texto con parámetros variables
     def generar_texto(prompt, max_tokens, temperature):
         data = {
             "prompt": prompt,
             "max_tokens": max_tokens,
             "temperature": temperature
         }
         headers = {
             "Content-Type": "application/json",
             "api-key": subscription_key
         }
         response = requests.post(url, headers=headers, json=data)
         result = response.json()
         return result.get("choices", [{}])[0].get("text", "")

     # Ejemplo de experimentación
     prompt = "Explica brevemente los beneficios de la inteligencia artificial generativa."
     configuraciones = [
         {"max_tokens": 100, "temperature": 0.5},
         {"max_tokens": 100, "temperature": 0.7},
         {"max_tokens": 150, "temperature": 0.7},
         {"max_tokens": 150, "temperature": 0.9}
     ]

     for config in configuraciones:
         salida = generar_texto(prompt, config["max_tokens"], config["temperature"])
         print(f"Configuración: max_tokens={config['max_tokens']}, temperature={config['temperature']}")
         print("Salida Generada:")
         print(salida)
         print("-" * 50)
     ```
   - **Explicación:**  
     Se prueban diferentes combinaciones de `max_tokens` y `temperature` para evaluar el impacto en la calidad del contenido generado. Se imprime cada salida para su análisis comparativo.

### Beneficios  
Experimentar y ajustar los parámetros de generación permite optimizar el rendimiento del modelo para distintos escenarios, asegurando respuestas más coherentes y adaptadas a los requisitos de la aplicación.