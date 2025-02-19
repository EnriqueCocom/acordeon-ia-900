# Práctica 4: Comparación de Rostros para Verificación de Identidad con Face API

**Objetivo:**  
Comparar dos imágenes para verificar si contienen el mismo rostro, utilizando la API de Face.

**Pasos:**

1. **Reutiliza el recurso de Face API creado en la práctica anterior.**

2. **Detectar rostros en ambas imágenes:**
   - Utiliza el mismo código de detección (como en la práctica 3) para obtener los `faceId` de cada imagen.
   - Por ejemplo, crea dos archivos o modifica el script para obtener los `faceId` de dos URLs diferentes.

3. **Realizar la comparación:**
   - Una vez que tienes dos `faceId`, usa la API de verificación de rostros. Crea un archivo llamado `face_verification.py`:
     ```python
     import requests
     import json

     subscription_key = "<tu-clave-de-suscripción-face>"
     endpoint = "https://<tu-endpoint-face>.cognitiveservices.azure.com/"

     verify_url = endpoint + "face/v1.0/verify"

     # Suponiendo que ya obtuviste dos faceId
     face_id1 = "faceId_obtenido_de_imagen1"
     face_id2 = "faceId_obtenido_de_imagen2"

     headers = {
         "Ocp-Apim-Subscription-Key": subscription_key,
         "Content-Type": "application/json"
     }
     data = {
         "faceId1": face_id1,
         "faceId2": face_id2
     }

     response = requests.post(verify_url, headers=headers, json=data)
     result = response.json()

     print(json.dumps(result, indent=2, ensure_ascii=False))
     ```
4. **Ejecutar y analizar:**
   - Ejecuta:
     ```bash
     python face_verification.py
     ```
   - La respuesta indicará un valor de similitud y si se consideran la misma persona (por ejemplo, un campo `"isIdentical": true/false` y `"confidence"`).