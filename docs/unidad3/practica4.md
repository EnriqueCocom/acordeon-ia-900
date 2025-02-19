# Práctica 4: Simulación de Reconocimiento del Lenguaje Conversacional con LUIS

**Objetivo:** Utilizar Language Understanding (LUIS) para identificar la intención y entidades en una consulta conversacional.

### Paso 1: Crear una Aplicación LUIS  
1. Ingresa a [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/).  
2. Crea una nueva aplicación LUIS:
   - Define algunas intenciones (por ejemplo, "ReservarVuelo", "ConsultarEstado") y entrena el modelo con ejemplos de frases.
   - Publica la aplicación y anota el **App ID** y la **Clave de Predicción**.

### Paso 2: Probar la Aplicación con Postman  
1. Crea una solicitud **GET** o **POST** (según la documentación de LUIS) a la URL de predicción, por ejemplo:
   ```
   https://<tu-region>.api.cognitive.microsoft.com/luis/prediction/v3.0/apps/<tu-app-id>/slots/production/predict?verbose=true&show-all-intents=true&log=true&query=Quiero reservar un vuelo a Madrid
   ```
2. Agrega el header:
   - `Ocp-Apim-Subscription-Key: <tu-clave-de-predicción>`
3. Envía la solicitud y revisa la respuesta para ver la intención identificada y las entidades extraídas.

### Paso 3: Código en Python para Consultar LUIS  
1. Crea un archivo llamado `luis_query.py`:
   ```python
   import requests
   import json

   endpoint = "https://<tu-region>.api.cognitive.microsoft.com/luis/prediction/v3.0/apps/<tu-app-id>/slots/production/predict"
   params = {
       "verbose": "true",
       "show-all-intents": "true",
       "log": "true",
       "query": "Quiero reservar un vuelo a Madrid"
   }
   headers = {
       "Ocp-Apim-Subscription-Key": "<tu-clave-de-predicción>"
   }

   response = requests.get(endpoint, headers=headers, params=params)
   result = response.json()

   print(json.dumps(result, indent=2, ensure_ascii=False))
   ```
2. Ejecuta el script:
   ```bash
   python luis_query.py
   ```
3. Verifica que la salida muestre la intención detectada (por ejemplo, "ReservarVuelo") y las entidades (como "Madrid").