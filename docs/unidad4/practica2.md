# Práctica 2: Creación de un Pipeline de Indexación y Búsqueda con Azure Cognitive Search

**Objetivo:**  
Construir un pipeline que combine la extracción de información de documentos (por ejemplo, mediante Form Recognizer) y la indexación de esos datos en Azure Cognitive Search para consultas avanzadas.

### Pasos:

1. **Configurar Azure Cognitive Search:**
   - En [Azure Portal](https://portal.azure.com), crea un recurso de Azure Cognitive Search.
   - Define un índice con campos que correspondan a los datos extraídos (por ejemplo, `id`, `fecha`, `monto`, `proveedor`, etc.).
   - Anota el nombre del servicio, la clave y el nombre del índice.

2. **Integrar los resultados de Form Recognizer con Cognitive Search:**
   - Utiliza el ejercicio anterior para extraer los datos del documento.
   - Crea un script para indexar los resultados en Cognitive Search.

3. **Implementación en Python:**
   - Instala la librería `requests` si no la tienes:
     ```bash
     pip install requests
     ```
   - Crea un archivo llamado `index_documents.py`:
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

     # Supón que este es el documento extraído de Form Recognizer (puedes combinar con los resultados del ejercicio 1)
     documento = {
         "value": [
             {
                 "id": "factura001",
                 "fecha": "2023-09-15",
                 "monto": 1500.75,
                 "proveedor": "Empresa XYZ",
                 "detalles": "Factura por servicios de consultoría"
             }
         ]
     }

     response = requests.post(url, headers=headers, json=documento)
     print("Respuesta de indexación:")
     print(json.dumps(response.json(), indent=2, ensure_ascii=False))
     ```
   - **Explicación:**  
     - Se construye un documento JSON con la estructura del índice.  
     - Se envía mediante una solicitud POST al endpoint de indexación de Cognitive Search.

4. **Ejecutar el script:**
   ```bash
   python index_documents.py
   ```
   - Verifica en el portal de Cognitive Search o mediante consultas que el documento se indexó correctamente.