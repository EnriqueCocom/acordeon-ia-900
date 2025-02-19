# Tema Complementario 1: Optimización y Diseño de Prompts para Modelos Generativos

### Descripción  
El rendimiento y la calidad de las salidas generadas por modelos como Azure OpenAI Service dependen en gran medida del prompt (entrada) que se les suministra. Este tema profundiza en cómo diseñar y optimizar prompts para obtener respuestas más precisas, coherentes y útiles.

### Aspectos Clave

1. **Fundamentos del Prompting:**
   - **Definición y Rol del Prompt:** El prompt es el texto de entrada que guía al modelo para generar una respuesta. Su formulación afecta la creatividad, el tono y la precisión de la salida.
   - **Elementos Clave:** Claridad, contexto y especificidad. Se deben incluir detalles relevantes y establecer límites si se requiere un formato específico.

2. **Estrategias de Optimización:**
   - **Incluir Contexto:** Proveer antecedentes o ejemplos para guiar la generación.
   - **Instrucciones Claras:** Usar indicaciones directas como “describe”, “explica” o “resume”.
   - **Ejemplos In-Context:** Incluir ejemplos de salida deseada directamente en el prompt.

3. **Ejemplo Práctico:**
   - **Código de Ejemplo en Python:**
     ```python
     import requests
     import json

     # Configuración de Azure OpenAI Service
     subscription_key = "<tu-clave>"
     endpoint = "https://<tu-endpoint>.openai.azure.com/"
     deployment_id = "<tu-deployment-id>"  # Ej: "text-davinci-003"
     url = f"{endpoint}openai/deployments/{deployment_id}/completions?api-version=2022-12-01"

     # Definir un prompt optimizado con contexto y ejemplos
     prompt = (
         "Teniendo en cuenta las tendencias actuales en inteligencia artificial, "
         "describe brevemente cómo los modelos generativos están transformando la creación de contenido. "
         "Ejemplo: Los modelos generativos pueden crear textos, imágenes y música de manera autónoma. "
         "Ahora, explica de forma clara y concisa:"
     )
     data = {
         "prompt": prompt,
         "max_tokens": 150,
         "temperature": 0.7
     }
     headers = {
         "Content-Type": "application/json",
         "api-key": subscription_key
     }

     response = requests.post(url, headers=headers, json=data)
     result = response.json()
     texto_generado = result.get("choices", [{}])[0].get("text", "")
     print("Salida Generada:")
     print(texto_generado)
     ```
   - **Explicación Paso a Paso:**
     1. Se configura la conexión con Azure OpenAI.
     2. Se diseña un prompt que incluye contexto, un ejemplo y una instrucción clara.
     3. Se realiza la solicitud y se imprime la salida.
   
### Beneficios  
Diseñar prompts efectivos mejora significativamente la relevancia y calidad de las respuestas generadas, permitiendo adaptar la IA a necesidades específicas de aplicaciones y casos de uso.
