# Práctica 2: Extracción de Frases Clave y Reconocimiento de Entidades

**Objetivo:** Extraer las frases clave y detectar entidades relevantes en un texto usando el servicio de Text Analytics.

### Paso 1: Configuración similar a la Práctica 1  
Utiliza el mismo recurso y clave que configuraste anteriormente.

### Paso 2: Probar con Postman  
1. Crea una solicitud **POST** en Postman.  
2. URL de la solicitud (por ejemplo, para extraer frases clave):
   ```
   https://<tu-endpoint>/text/analytics/v3.0/keyPhrases
   ```
3. Configura los **Headers** igual que en la práctica anterior.  
4. En el **Body**, utiliza el siguiente JSON:
   ```json
   {
     "documents": [
       {
         "id": "1",
         "language": "es",
         "text": "La nueva actualización de software mejora significativamente la seguridad y el rendimiento del sistema."
       }
     ]
   }
   ```
5. Envía la solicitud y revisa la respuesta para ver las frases clave.

### Paso 3: Código en Python para frases clave y entidades  
1. Crea un archivo llamado `keyphrases_entities.py`:
   ```python
   import requests
   import json

   subscription_key = "<tu-clave>"
   endpoint = "https://<tu-endpoint>.cognitiveservices.azure.com/"

   # URL para extraer frases clave
   keyphrases_url = endpoint + "text/analytics/v3.0/keyPhrases"
   # URL para el reconocimiento de entidades
   entities_url = endpoint + "text/analytics/v3.0/entities/recognition/general"

   document = {
       "documents": [
           {
               "id": "1",
               "language": "es",
               "text": "La nueva actualización de software mejora significativamente la seguridad y el rendimiento del sistema."
           }
       ]
   }

   headers = {
       "Ocp-Apim-Subscription-Key": subscription_key,
       "Content-Type": "application/json"
   }

   # Extraer frases clave
   response_key = requests.post(keyphrases_url, headers=headers, json=document)
   keyphrases_result = response_key.json()

   # Extraer entidades
   response_entities = requests.post(entities_url, headers=headers, json=document)
   entities_result = response_entities.json()

   print("Frases Clave:")
   print(json.dumps(keyphrases_result, indent=2, ensure_ascii=False))
   print("\nEntidades:")
   print(json.dumps(entities_result, indent=2, ensure_ascii=False))
   ```
2. Ejecuta el script:
   ```bash
   python keyphrases_entities.py
   ```
3. Revisa la salida para confirmar que se extraen las frases clave y se reconocen las entidades (por ejemplo, "software", "seguridad").