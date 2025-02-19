# Práctica 1: Análisis de Sentimiento con la API de Text Analytics

**Objetivo:** Utilizar el servicio de Text Analytics para analizar el sentimiento de un fragmento de texto.

### Paso 1: Configurar el recurso en Azure  
1. Ingresa al [Azure Portal](https://portal.azure.com).  
2. Crea un recurso de **Cognitive Services** o específicamente **Text Analytics**.  
3. Una vez creado, copia la clave de suscripción y el endpoint desde la sección “Claves y Endpoint”.

### Paso 2: Probar la API con Postman  
1. Abre **Postman** y crea una nueva solicitud (**Request**).  
2. Selecciona el método **POST**.  
3. Establece la URL con tu endpoint y la ruta para análisis de sentimiento, por ejemplo:  
   ```
   https://<tu-endpoint>/text/analytics/v3.0/sentiment
   ```
4. Configura los **Headers**:
   - `Ocp-Apim-Subscription-Key: <tu-clave>`
   - `Content-Type: application/json`
5. En la pestaña **Body** (modo raw, JSON), inserta:
   ```json
   {
     "documents": [
       {
         "id": "1",
         "language": "es",
         "text": "Estoy muy contento con el servicio, la experiencia fue excelente."
       }
     ]
   }
   ```
6. Haz clic en **Send** y revisa la respuesta, la cual debe incluir la clasificación del sentimiento (por ejemplo, "positive").

### Paso 3: Implementar en Python  
1. Asegúrate de tener Python 3 instalado y la librería `requests`:
   ```bash
   pip install requests
   ```
2. Crea un archivo llamado `sentiment_analysis.py` y agrega el siguiente código:
   ```python
   import requests
   import json

   # Configuración: reemplaza con tu clave y endpoint
   subscription_key = "<tu-clave>"
   endpoint = "https://<tu-endpoint>.cognitiveservices.azure.com/"

   sentiment_url = endpoint + "text/analytics/v3.0/sentiment"

   # Texto de ejemplo para analizar
   documents = {
       "documents": [
           {
               "id": "1",
               "language": "es",
               "text": "Estoy muy contento con el servicio, la experiencia fue excelente."
           }
       ]
   }

   headers = {
       "Ocp-Apim-Subscription-Key": subscription_key,
       "Content-Type": "application/json"
   }

   response = requests.post(sentiment_url, headers=headers, json=documents)
   sentiments = response.json()

   print(json.dumps(sentiments, indent=2, ensure_ascii=False))
   ```
3. Ejecuta el script:
   ```bash
   python sentiment_analysis.py
   ```
4. Verifica que la salida muestre el sentimiento (por ejemplo, "positive" con un puntaje asociado).
