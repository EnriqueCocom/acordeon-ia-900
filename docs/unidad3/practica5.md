# Práctica 5: Traducción de Textos con la API de Traducción de Azure

**Objetivo:** Traducir un fragmento de texto de un idioma a otro utilizando la API de Traducción de Azure.

### Paso 1: Configurar el Recurso de Traducción  
1. En el [Azure Portal](https://portal.azure.com), crea un recurso de **Translator**.  
2. Copia la clave de suscripción y el endpoint.

### Paso 2: Probar la API con Postman  
1. Crea una solicitud **POST** en Postman.  
2. URL (según la documentación de Translator):
   ```
   https://api.cognitive.microsofttranslator.com/translate?api-version=3.0&to=en
   ```
3. Headers:
   - `Ocp-Apim-Subscription-Key: <tu-clave>`
   - `Content-Type: application/json`
   - (Posiblemente, `Ocp-Apim-Subscription-Region: <tu-región>` si es requerido)
4. En el Body (modo raw, JSON):
   ```json
   [
     {
       "Text": "Hola, ¿cómo estás?"
     }
   ]
   ```
5. Envía la solicitud y revisa la respuesta para ver la traducción al inglés.

### Paso 3: Código en Python para Traducir Texto  
1. Crea un archivo llamado `translate_text.py`:
   ```python
   import requests
   import json

   subscription_key = "<tu-clave>"
   endpoint = "https://api.cognitive.microsofttranslator.com/"
   path = "translate?api-version=3.0"
   params = "&to=en"
   url = endpoint + path + params

   headers = {
       "Ocp-Apim-Subscription-Key": subscription_key,
       "Content-Type": "application/json",
       "Ocp-Apim-Subscription-Region": "<tu-región>"  # si es necesario
   }
   body = [
       {"Text": "Hola, ¿cómo estás?"}
   ]

   response = requests.post(url, headers=headers, json=body)
   result = response.json()

   print(json.dumps(result, indent=2, ensure_ascii=False))
   ```
2. Ejecuta el script:
   ```bash
   python translate_text.py
   ```
3. Verifica que la salida muestre el texto traducido al inglés (por ejemplo, "Hello, how are you?").