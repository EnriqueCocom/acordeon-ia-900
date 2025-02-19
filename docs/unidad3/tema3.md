# Tema Complementario 3: Integración de Servicios de NLP con Azure Cognitive Search y Otros Componentes

### Descripción  
Integrar los resultados del análisis de texto con otros servicios de Azure permite crear soluciones más robustas. Por ejemplo, combinar la salida de Text Analytics con Azure Cognitive Search para indexar y buscar información en grandes volúmenes de texto.

### Aspectos Clave y Pasos a Seguir

1. **Diseño de la Arquitectura Integrada:**  
   - **Flujo de Datos:**  
     - Procesar texto con Text Analytics para extraer metadatos (sentimiento, entidades, frases clave).  
     - Enviar los resultados a Azure Cognitive Search para indexarlos y permitir búsquedas avanzadas.
   - **Herramientas de Orquestación:**  
     - Utilizar Azure Logic Apps o Azure Functions para automatizar el flujo de trabajo.

2. **Ejemplo Práctico: Integración con Azure Cognitive Search**  
   - **Paso 1: Configurar Azure Cognitive Search:**  
     - En Azure Portal, crea un recurso de Cognitive Search.  
     - Define un índice que contenga campos para texto, etiquetas, entidades, etc.
   - **Paso 2: Enviar Datos al Índice:**  
     - Utiliza un script en Python para enviar la salida de Text Analytics al índice.
     ```python
     import requests
     import json

     search_service = "<nombre-de-tu-servicio>"
     api_key_search = "<tu-api-key-search>"
     index_name = "<nombre-del-índice>"
     url = f"https://{search_service}.search.windows.net/indexes/{index_name}/docs/index?api-version=2020-06-30"

     headers = {
         "Content-Type": "application/json",
         "api-key": api_key_search
     }

     # Ejemplo de documento a indexar
     documento = {
         "value": [
             {
                 "id": "1",
                 "textoOriginal": "Estoy muy contento con el servicio.",
                 "sentimiento": "positivo",
                 "entidades": ["servicio"]
             }
         ]
     }

     response = requests.post(url, headers=headers, json=documento)
     print(response.json())
     ```
   - **Explicación:**  
     - Se construye un documento JSON con la información procesada y se envía a Cognitive Search para indexarlo.

### Beneficios  
La integración permite búsquedas enriquecidas, análisis combinados y una mayor capacidad para extraer insights de grandes volúmenes de datos textuales.