# Práctica 1: Análisis de Imágenes con la API de Computer Vision usando Postman

**Objetivo:**  
Consumir la API de Computer Vision de Azure para obtener una descripción y etiquetas de una imagen.

**Pasos:**

1. **Crear el recurso en Azure:**
   - Inicia sesión en [Azure Portal](https://portal.azure.com).
   - Selecciona “Crear un recurso” y busca “Computer Vision”.
   - Configura el recurso (elige suscripción, grupo de recursos y región) y crea el servicio.
   - Una vez creado, accede a la sección “Claves y Endpoint” y copia ambos valores.

2. **Configurar Postman:**
   - Abre Postman y crea una nueva **Request**.
   - Selecciona el método **POST**.
   - En la URL, ingresa el endpoint con la ruta de análisis, por ejemplo:  
     ```
     https://<tu-endpoint>/vision/v3.2/analyze?visualFeatures=Description,Tags
     ```
   - En la pestaña **Headers** añade:
     - `Ocp-Apim-Subscription-Key: <tu-clave-de-suscripción>`
     - `Content-Type: application/json`
   - En la pestaña **Body**, selecciona **raw** y pega el siguiente JSON (reemplaza la URL de la imagen por una de tu elección):
     ```json
     {
       "url": "https://ejemplo.com/imagen.jpg"
     }
     ```
3. **Ejecutar y analizar:**
   - Haz clic en **Send**.
   - Revisa la respuesta JSON, que incluirá la descripción, etiquetas y otros metadatos extraídos de la imagen.
   - Analiza cómo la API identifica los elementos y clasifica el contenido visual.