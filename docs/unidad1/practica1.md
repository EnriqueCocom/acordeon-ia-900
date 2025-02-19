# Práctica 1: Consumir la API de Computer Vision con Postman  
**Objetivo:** Realizar una llamada a la API de Computer Vision para analizar una imagen y extraer su descripción.

## Paso a Paso:

1. **Crear el recurso en Azure:**
   - Inicia sesión en [Azure Portal](https://portal.azure.com).
   - Navega a “Crear un recurso” y busca “Cognitive Services” o “Computer Vision”.
   - Selecciona la opción adecuada, elige la suscripción, grupo de recursos, región y crea el recurso.
   - Una vez creado, copia la *clave de suscripción* y el *endpoint* que se muestran en la sección de “Claves y Endpoint”.

2. **Configurar Postman:**
   - Abre Postman y crea una nueva **Request**.
   - Selecciona el método **POST**.
   - En la URL ingresa el endpoint con el siguiente formato:  
     ```
     https://<tu-endpoint>/vision/v3.2/analyze?visualFeatures=Description
     ```
   - En la pestaña **Headers** agrega:
     - `Ocp-Apim-Subscription-Key: <tu-clave-de-suscripción>`
     - `Content-Type: application/json`
   - En la pestaña **Body**, selecciona **raw** y usa el siguiente JSON (reemplaza la URL de la imagen por una de tu elección):
     ```json
     {
       "url": "https://ejemplo.com/imagen.jpg"
     }
     ```
3. **Enviar la solicitud:**
   - Haz clic en “Send” y revisa la respuesta. Deberías ver un objeto JSON con la descripción de la imagen, etiquetas y detalles adicionales.
   - Analiza cómo el servicio interpreta la imagen y extrae información (esto te ayudará a comprender el concepto de “Computer Vision” dentro de Azure AI).
