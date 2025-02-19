# Práctica 2: Extracción de Texto de Imágenes mediante OCR con Python

**Objetivo:**  
Utilizar la API de OCR de Azure para extraer texto de una imagen, implementado en un script de Python.

**Pasos:**

1. **Crear el recurso de Computer Vision (OCR):**
   - Si ya creaste el recurso en la práctica anterior, utiliza las mismas claves y endpoint.
  
2. **Preparar el entorno de Python:**
   - Asegúrate de tener Python 3 instalado.
   - Crea un entorno virtual (opcional) y ejecuta:
     ```bash
     pip install requests
     ```

3. **Escribir el código:**
   - Crea un archivo llamado `ocr_extraction.py` y pega el siguiente código:
     ```python
     import requests
     import json

     # Configuración: reemplaza con tu clave y endpoint
     subscription_key = "<tu-clave-de-suscripción>"
     endpoint = "https://<tu-endpoint>.cognitiveservices.azure.com/"

     ocr_url = endpoint + "vision/v3.2/ocr"

     # Imagen de ejemplo (puede ser una URL pública)
     image_url = "https://ejemplo.com/texto-en-imagen.jpg"

     headers = {
         "Ocp-Apim-Subscription-Key": subscription_key,
         "Content-Type": "application/json"
     }

     data = {
         "url": image_url
     }

     response = requests.post(ocr_url, headers=headers, json=data)
     result = response.json()

     print(json.dumps(result, indent=2, ensure_ascii=False))
     ```
4. **Ejecutar y analizar:**
   - En la terminal, ejecuta:
     ```bash
     python ocr_extraction.py
     ```
   - Revisa la salida, donde se mostrará el texto detectado, organizado en regiones y líneas.  
   - Comprende cómo el OCR segmenta y extrae cada parte del texto.