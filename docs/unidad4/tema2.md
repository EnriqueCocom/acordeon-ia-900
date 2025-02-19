# Tema Complementario 2: Integración con Azure Cognitive Search para Indexación y Búsqueda Avanzada

### Descripción  
La integración de la inteligencia de documentos con Azure Cognitive Search permite transformar grandes volúmenes de información extraída en índices de búsqueda enriquecidos. Esto facilita la consulta y recuperación rápida de datos relevantes.

### Puntos Clave

1. **Diseño del Índice:**
   - **Definición de campos:** Determinar qué datos extraídos se indexarán (por ejemplo, fecha, monto, proveedor, contenido textual, etiquetas, etc.).
   - **Configuración de esquemas y sugerencias:** Configurar los tipos de datos y optimizar para búsquedas y filtros.

2. **Automatización del Flujo de Datos:**
   - **Pipeline de integración:** Uso de Azure Logic Apps o Azure Functions para orquestar la extracción (por ejemplo, con Form Recognizer) y su envío a Cognitive Search.
   - **Actualización periódica y reindexación:** Mantener el índice actualizado conforme se añaden nuevos documentos.

3. **Ejemplo Práctico:**
   - **Código en Python para indexar documentos:**  
     ```python
     import requests
     import json

     # Configuración de Azure Cognitive Search
     search_service = "<tu-nombre-de-servicio>"
     index_name = "<tu-indice>"
     api_key_search = "<tu-api-key-search>"
     url = f"https://{search_service}.search.windows.net/indexes/{index_name}/docs/index?api-version=2020-06-30"

     headers = {
         "Content-Type": "application/json",
         "api-key": api_key_search
     }

     # Documento extraído de un análisis (ejemplo)
     documento = {
         "value": [
             {
                 "id": "doc1",
                 "fecha": "2023-10-01",
                 "monto": 2500.00,
                 "proveedor": "Proveedor ABC",
                 "contenido": "Detalle del documento extraído y procesado."
             }
         ]
     }

     response = requests.post(url, headers=headers, json=documento)
     print("Respuesta de indexación:", json.dumps(response.json(), indent=2, ensure_ascii=False))
     ```
   - **Explicación:**  
     Se crea un documento JSON con campos estructurados y se envía a Cognitive Search para que quede indexado y pueda ser consultado mediante búsquedas avanzadas.

### Beneficios  
Integrar con Azure Cognitive Search permite transformar la información extraída en un repositorio consultable, mejorando la eficiencia y la accesibilidad de la información para la toma de decisiones.