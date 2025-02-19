# Práctica 3: Implementación de Reconocimiento Facial con Azure Face API en Python

**Objetivo:**  
Detectar y analizar atributos faciales (edad, género, emociones) utilizando el servicio Face de Azure.

**Pasos:**

1. **Crear el recurso de Face API:**
   - En Azure Portal, crea un recurso “Face” siguiendo pasos similares a los de Computer Vision.
   - Copia la clave y el endpoint del recurso.

2. **Preparar el entorno de Python:**
   - Asegúrate de tener instalada la librería `requests` (ver Práctica 2).

3. **Escribir el código:**
   - Crea un archivo llamado `face_recognition.py` con el siguiente contenido:
     ```python
     import requests
     import json

     subscription_key = "<tu-clave-de-suscripción-face>"
     endpoint = "https://<tu-endpoint-face>.cognitiveservices.azure.com/"

     face_api_url = endpoint + "face/v1.0/detect"

     # Parámetros para detectar atributos faciales
     params = {
         "returnFaceId": "true",
         "returnFaceAttributes": "age,gender,emotion"
     }

     # Imagen de ejemplo que contenga rostros
     image_url = "https://ejemplo.com/rostro.jpg"
     headers = {
         "Ocp-Apim-Subscription-Key": subscription_key,
         "Content-Type": "application/json"
     }
     data = {
         "url": image_url
     }

     response = requests.post(face_api_url, params=params, headers=headers, json=data)
     faces = response.json()

     print(json.dumps(faces, indent=2, ensure_ascii=False))
     ```
4. **Ejecutar y analizar:**
   - Ejecuta:
     ```bash
     python face_recognition.py
     ```
   - Analiza la salida JSON, donde se muestran el ID del rostro y los atributos como edad, género y emociones detectadas.