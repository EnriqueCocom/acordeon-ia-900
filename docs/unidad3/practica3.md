# Práctica 3: Construcción de una Base de Conocimiento para Respuesta a Preguntas (QnA Maker)

**Objetivo:** Crear y consultar una base de conocimientos que responda preguntas frecuentes usando el servicio QnA Maker.

### Paso 1: Crear la Base de Conocimiento  
1. Ve a [QnA Maker](https://www.qnamaker.ai/) e inicia sesión con tu cuenta de Microsoft.  
2. Crea un nuevo servicio QnA siguiendo el asistente:
   - Define un nombre para la base de conocimientos.
   - Ingresa algunas preguntas y respuestas (por ejemplo, "¿Cuál es el horario de atención?" → "Nuestro horario es de 9 AM a 5 PM").
   - Publica la base de conocimientos.

### Paso 2: Probar la Base de Conocimiento  
1. Una vez publicada, utiliza el portal de QnA Maker para probar ingresando preguntas y verificando las respuestas.

### Paso 3: Consultar la Base de Conocimiento con Postman o Python  
#### Con Postman:  
- Método: **POST**  
- URL (basada en la URL del endpoint proporcionado en QnA Maker):  
  ```
  https://<tu-endpoint>/qnamaker/knowledgebases/<tu-kb-id>/generateAnswer
  ```
- Headers:
  - `Authorization: EndpointKey <tu-endpoint-key>`
  - `Content-Type: application/json`
- Body:
  ```json
  {
    "question": "¿Cuál es el horario de atención?"
  }
  ```
- Envía la solicitud y verifica que la respuesta contenga la respuesta configurada.

#### Con Python:  
1. Crea un archivo llamado `qna_query.py`:
   ```python
   import requests
   import json

   endpoint = "https://<tu-endpoint>/qnamaker/knowledgebases/<tu-kb-id>/generateAnswer"
   headers = {
       "Authorization": "EndpointKey <tu-endpoint-key>",
       "Content-Type": "application/json"
   }
   data = {
       "question": "¿Cuál es el horario de atención?"
   }

   response = requests.post(endpoint, headers=headers, json=data)
   result = response.json()

   print(json.dumps(result, indent=2, ensure_ascii=False))
   ```
2. Ejecuta el script:
   ```bash
   python qna_query.py
   ```
3. Verifica que el resultado contenga la respuesta configurada en la base de conocimientos.