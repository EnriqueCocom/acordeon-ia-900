# Práctica 5: Análisis de Sentimiento con la API de Text Analytics en Python  
**Objetivo:** Utilizar la API de Text Analytics de Azure para analizar el sentimiento de un texto mediante un script en Python.

#### Paso a Paso:

1. **Crear el recurso de Text Analytics:**
   - En Azure Portal, crea un recurso de “Text Analytics”.
   - Copia la *clave de suscripción* y el *endpoint*.

2. **Configurar el entorno en Python:**
   - Crea un archivo llamado `analisis_sentimiento.py`.
   - Instala la librería `requests` si aún no la tienes:
     ```bash
     pip install requests
     ```

3. **Escribir el código:**
   - Inserta el siguiente código en `analisis_sentimiento.py`:
     ```python
     import requests
     import json

     # Reemplaza estos valores por los de tu recurso de Azure
     subscription_key = "<tu-clave-de-suscripción>"
     endpoint = "https://<tu-endpoint>.cognitiveservices.azure.com/"

     # URL para el análisis de sentimiento
     sentiment_url = endpoint + "text/analytics/v3.0/sentiment"

     # Texto de ejemplo para analizar
     documents = {
         "documents": [
             {"id": "1", "language": "es", "text": "Me encanta trabajar con Azure AI, es muy innovador y fácil de usar."},
             {"id": "2", "language": "es", "text": "La implementación del modelo fue complicada y los resultados fueron mediocres."}
         ]
     }

     # Configurar cabeceras
     headers = {
         "Ocp-Apim-Subscription-Key": subscription_key,
         "Content-Type": "application/json"
     }

     # Realizar la solicitud POST
     response = requests.post(sentiment_url, headers=headers, json=documents)
     sentiments = response.json()

     # Mostrar resultados
     print(json.dumps(sentiments, indent=2, ensure_ascii=False))
     ```
4. **Ejecutar el script:**
   - Ejecuta el script:
     ```bash
     python analisis_sentimiento.py
     ```
   - Revisa en la consola la salida que muestra el análisis de sentimiento para cada documento, comprendiendo cómo el servicio clasifica el texto en positivo, negativo o neutral.