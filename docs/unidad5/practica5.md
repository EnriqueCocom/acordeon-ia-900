# Práctica 5: Creación de un Pipeline End-to-End en Azure AI Studio para Generación de Contenido

**Objetivo:**  
Construir un pipeline completo en Azure AI Studio que permita recibir un prompt, generar contenido con Azure OpenAI Service, aplicar filtros de seguridad y almacenar el resultado en una base de datos o dashboard para su posterior consulta.

### Paso a Paso:

1. **Diseño del Pipeline en Azure AI Studio:**
   - Inicia sesión en Azure AI Studio y crea un nuevo proyecto.
   - Define el flujo de trabajo:
     - **Entrada:** Recepción del prompt del usuario a través de una interfaz (por ejemplo, una aplicación web o un formulario).
     - **Procesamiento:** Envío del prompt a Azure OpenAI Service para generar contenido.
     - **Post-procesamiento:** Aplicación de filtros de seguridad (utilizando una función personalizada, como en la Práctica 3).
     - **Almacenamiento:** Guardar el contenido generado en una base de datos (por ejemplo, Azure Cosmos DB o Azure SQL) o en un dashboard personalizado.

2. **Configuración de la Interfaz de Usuario:**
   - Utiliza herramientas como Power Apps o desarrolla una sencilla aplicación web en HTML/JavaScript que permita al usuario ingresar el prompt.
   - Asegúrate de que la aplicación llame a una API intermedia que gestione la comunicación con Azure OpenAI Service.

3. **Implementación del Backend:**
   - Desarrolla un servicio (por ejemplo, con Azure Functions y Python) que realice las siguientes acciones:
     - Reciba el prompt.
     - Llama a Azure OpenAI Service (como en la Práctica 1) y obtiene la respuesta.
     - Pasa la respuesta por el filtro de seguridad (como en la Práctica 3).
     - Almacena el resultado en la base de datos.
   - **Ejemplo de Código en una Azure Function (pseudocódigo):**
     ```python
     import azure.functions as func
     import requests, json
     from generative_filter import filter_output  # Usar el filtro desarrollado previamente
     from azure.cosmos import CosmosClient

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

         # Aplicar filtro de seguridad
         texto_seguro = filter_output(texto_generado)

         # Almacenar el resultado en Azure Cosmos DB (ejemplo simplificado)
         cosmos_endpoint = "<tu-cosmos-endpoint>"
         cosmos_key = "<tu-cosmos-key>"
         client = CosmosClient(cosmos_endpoint, cosmos_key)
         database = client.get_database_client("GenerativeDB")
         container = database.get_container_client("Resultados")
         documento = {"id": "some_unique_id", "prompt": prompt, "respuesta": texto_seguro}
         container.create_item(documento)

         return func.HttpResponse(json.dumps(documento), mimetype="application/json", status_code=200)
     ```
   - **Explicación:**
     - La función recibe el prompt, llama a la API generativa, aplica el filtro y almacena el resultado en Cosmos DB.
     - Se utiliza una estructura básica para ejemplificar el flujo.

4. **Prueba del Pipeline:**
   - Despliega la Azure Function y la interfaz de usuario.
   - Realiza pruebas enviando diferentes prompts y verifica que los resultados sean generados, filtrados y almacenados correctamente.

5. **Monitoreo y Ajustes:**
   - Configura Application Insights para monitorizar el rendimiento y errores en el pipeline.
   - Ajusta parámetros (por ejemplo, temperatura, max_tokens) para optimizar la calidad del contenido generado.