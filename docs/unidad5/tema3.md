# Tema Complementario 3: Integración de Modelos Generativos en Aplicaciones Empresariales

### Descripción  
Este tema explora cómo integrar de manera efectiva los modelos generativos en aplicaciones reales, abarcando desde la arquitectura hasta la orquestación de servicios. Se enfoca en casos de uso prácticos y la integración con otros servicios de Azure.

### Aspectos Clave

1. **Diseño de Arquitecturas Integradas:**
   - **Componentes Clave:** Interfaz de usuario, API de generación, procesamiento post-generación y almacenamiento.
   - **Flujo de Datos:** Desde la recepción del prompt hasta la entrega del contenido generado, integrando validación y filtros.

2. **Uso de Azure AI Studio y Azure Functions:**
   - **Azure AI Studio:** Para prototipar y ajustar el modelo generativo.
   - **Azure Functions:** Para implementar lógica de negocio y orquestar la llamada a la API de generación.
   - **Ejemplo de Arquitectura:**  
     - Un usuario envía un prompt a una aplicación web.
     - Azure Functions procesa el prompt, llama a Azure OpenAI Service y aplica filtros.
     - El resultado se almacena en Azure Cosmos DB y se muestra en un dashboard.

3. **Ejemplo Práctico: Integración Básica con Azure Functions (Pseudocódigo)**
   - **Código de Ejemplo:**
     ```python
     import azure.functions as func
     import requests, json

     def main(req: func.HttpRequest) -> func.HttpResponse:
         prompt = req.params.get('prompt')
         if not prompt:
             return func.HttpResponse("Falta el prompt", status_code=400)

         # Llamada a Azure OpenAI Service
         subscription_key = "<tu-clave>"
         endpoint = "https://<tu-endpoint>.openai.azure.com/"
         deployment_id = "<tu-deployment-id>"
         url = f"{endpoint}openai/deployments/{deployment_id}/completions?api-version=2022-12-01"
         data = {"prompt": prompt, "max_tokens": 150, "temperature": 0.7}
         headers = {"Content-Type": "application/json", "api-key": subscription_key}
         response = requests.post(url, headers=headers, json=data)
         result = response.json()
         texto_generado = result.get("choices", [{}])[0].get("text", "")

         # Aplicar post-procesamiento (filtros, validación, etc.)
         # Aquí se podría llamar a una función de filtrado

         # Retornar la respuesta generada
         return func.HttpResponse(json.dumps({"respuesta": texto_generado}), mimetype="application/json", status_code=200)
     ```
   - **Explicación:**  
     Se ejemplifica cómo se puede construir una Azure Function que orquesta la generación de texto, integrándola en un flujo empresarial.

### Beneficios  
Comprender la integración en aplicaciones permite trasladar la capacidad de generación a soluciones reales, potenciando la innovación y la automatización en procesos empresariales.