# Práctica 5: Integración Completa: Aplicación de Escritorio Simple que Utilice Computer Vision, Face API y OCR

**Objetivo:**  
Crear una aplicación simple (por ejemplo, en Python) que permita seleccionar una imagen y ejecutar las tres funciones: análisis general, reconocimiento facial y OCR.

**Pasos:**

1. **Preparación del entorno:**
   - Instala las librerías necesarias:
     ```bash
     pip install requests tkinter pillow
     ```
   - Tkinter se usará para crear una interfaz gráfica simple y Pillow para procesar imágenes.

2. **Diseñar la interfaz:**
   - Crea un archivo llamado `vision_app.py` y escribe el siguiente código:
     ```python
     import tkinter as tk
     from tkinter import filedialog, Label, Button
     from PIL import Image, ImageTk
     import requests
     import json

     # Configuración de las API (reemplaza con tus claves y endpoints)
     cv_subscription_key = "<tu-clave-computer-vision>"
     cv_endpoint = "https://<tu-endpoint-computer-vision>.cognitiveservices.azure.com/"
     face_subscription_key = "<tu-clave-face>"
     face_endpoint = "https://<tu-endpoint-face>.cognitiveservices.azure.com/"
     ocr_url = cv_endpoint + "vision/v3.2/ocr"
     analyze_url = cv_endpoint + "vision/v3.2/analyze?visualFeatures=Description,Tags"
     face_url = face_endpoint + "face/v1.0/detect?returnFaceAttributes=age,gender,emotion"

     def analizar_imagen(image_url):
         headers = {
             "Ocp-Apim-Subscription-Key": cv_subscription_key,
             "Content-Type": "application/json"
         }
         data = {"url": image_url}
         # Análisis general
         res1 = requests.post(analyze_url, headers=headers, json=data).json()
         # OCR
         res2 = requests.post(ocr_url, headers=headers, json=data).json()
         # Face detection
         headers_face = {
             "Ocp-Apim-Subscription-Key": face_subscription_key,
             "Content-Type": "application/json"
         }
         res3 = requests.post(face_url, headers=headers_face, json=data).json()
         return res1, res2, res3

     def seleccionar_imagen():
         file_path = filedialog.askopenfilename()
         if file_path:
             # Convertir la imagen a un objeto Tkinter
             img = Image.open(file_path)
             img.thumbnail((400, 400))
             img_tk = ImageTk.PhotoImage(img)
             label_img.config(image=img_tk)
             label_img.image = img_tk
             # Para esta práctica, se debe subir la imagen a un servidor público o usar un servicio de alojamiento temporal.
             # Aquí se asume que se tiene una URL; de lo contrario, se puede implementar la carga a Azure Blob Storage.
             image_url = "https://tu-servidor-publico.com/ruta_de_imagen.jpg"
             result = analizar_imagen(image_url)
             output_text = "Análisis General:\n" + json.dumps(result[0], indent=2) + "\n\nOCR:\n" + json.dumps(result[1], indent=2) + "\n\nReconocimiento Facial:\n" + json.dumps(result[2], indent=2)
             text_output.config(text=output_text)

     root = tk.Tk()
     root.title("Aplicación de Computer Vision")
     btn = Button(root, text="Seleccionar Imagen", command=seleccionar_imagen)
     btn.pack(pady=10)
     label_img = Label(root)
     label_img.pack(pady=10)
     text_output = Label(root, text="", justify="left", wraplength=600)
     text_output.pack(pady=10)
     root.mainloop()
     ```
3. **Ejecutar y probar:**
   - Ejecuta el script:
     ```bash
     python vision_app.py
     ```
   - Selecciona una imagen local. (Nota: para que las APIs funcionen, la imagen debe estar alojada en una URL accesible públicamente. En un entorno real se integraría un método de carga a Azure Blob Storage.)
   - Observa la salida que integra el análisis general, OCR y reconocimiento facial.