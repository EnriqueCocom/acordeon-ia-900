# Práctica 1: Uso Avanzado de Azure OpenAI Service para Generación de Texto

**Objetivo:**  
Configurar y consumir la API de Azure OpenAI Service para generar contenido textual a partir de un prompt personalizado, evaluando la coherencia y creatividad del modelo.

### Paso a Paso:

1. **Crear el Recurso de Azure OpenAI Service:**
   - Inicia sesión en [Azure Portal](https://portal.azure.com) y crea un recurso de **Azure OpenAI Service**.
   - Selecciona la región y plan de precios adecuado.
   - Una vez creado, anota la clave de suscripción y el endpoint.

2. **Configurar el Entorno de Desarrollo en Python:**
   - Instala la librería `requests`:
     ```bash
     pip install requests
     ```
   - Crea un archivo llamado `openai_text_generation.py`.

3. **Implementar el Código:**
   - Copia y pega el siguiente código, reemplazando `<tu-clave>` y `<tu-endpoint>` por tus valores:
     ```python
     import requests
     import json

     # Configuración
     subscription_key = "<tu-clave>"
     endpoint = "https://<tu-endpoint>.openai.azure.com/"
     deployment_id = "<tu-deployment-id>"  # Por ejemplo, "text-davinci-003"

     # URL para la generación de texto
     url = f"{endpoint}openai/deployments/{deployment_id}/completions?api-version=2022-12-01"

     # Definir el prompt y parámetros de generación
     data = {
         "prompt": "Escribe un poema breve sobre la inteligencia artificial y el futuro.",
         "max_tokens": 100,
         "temperature": 0.7
     }

     headers = {
         "Content-Type": "application/json",
         "api-key": subscription_key
     }

     response = requests.post(url, headers=headers, json=data)
     result = response.json()

     print("Texto Generado:")
     print(result.get("choices", [{}])[0].get("text", "No se generó texto"))
     ```
   - **Explicación:**
     - Se define el prompt y parámetros como `max_tokens` (número máximo de tokens a generar) y `temperature` (nivel de aleatoriedad).
     - La solicitud se envía al endpoint de Azure OpenAI, y se imprime el resultado.

4. **Ejecutar y Evaluar:**
   - Ejecuta el script:
     ```bash
     python openai_text_generation.py
     ```
   - Revisa el texto generado y experimenta modificando parámetros (por ejemplo, el prompt o la temperatura) para observar cómo varían las salidas.