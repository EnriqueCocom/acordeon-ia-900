# Práctica 1: Extracción Avanzada de Datos de Formularios con Azure Form Recognizer

**Objetivo:**  
Extraer información estructurada de documentos complejos (por ejemplo, facturas o formularios) utilizando Azure Form Recognizer y procesar los resultados para integrarlos en un sistema de gestión.

### Pasos:

1. **Crear el recurso de Form Recognizer:**
   - Inicia sesión en [Azure Portal](https://portal.azure.com) y crea un recurso “Form Recognizer”.
   - Anota la clave de suscripción y el endpoint.

2. **Subir un documento de ejemplo:**
   - Prepara un PDF o imagen de un formulario (por ejemplo, una factura) y súbelo a un almacenamiento accesible (puede ser Azure Blob Storage o una URL pública).

3. **Entrenar un modelo personalizado (si es necesario):**
   - Si el documento tiene un formato específico, utiliza el portal de Form Recognizer Studio para etiquetar y entrenar un modelo personalizado.
   - Sigue el asistente para cargar documentos, etiquetar campos (como fecha, número de factura, monto, etc.) y entrenar el modelo.
   - Una vez entrenado, obtén el modelo ID.

4. **Implementar la llamada a la API desde Python:**
   - Instala el paquete `azure-ai-formrecognizer`:
     ```bash
     pip install azure-ai-formrecognizer
     ```
   - Crea un archivo llamado `form_extraction.py` y añade el siguiente código:
     ```python
     from azure.ai.formrecognizer import DocumentAnalysisClient
     from azure.core.credentials import AzureKeyCredential
     import json

     # Configuración: reemplaza con tu endpoint, clave y modelo (si es personalizado)
     endpoint = "https://<tu-endpoint>.cognitiveservices.azure.com/"
     key = "<tu-clave>"
     model_id = "<tu-modelo-personalizado>"  # O usa "prebuilt-invoice" para facturas

     document_url = "https://tu-dominio.com/tu_documento.pdf"

     client = DocumentAnalysisClient(endpoint=endpoint, credential=AzureKeyCredential(key))
     poller = client.begin_analyze_document_from_url(model_id, document_url)
     result = poller.result()

     # Procesamiento de resultados: extraer campos relevantes
     for document in result.documents:
         print("Documento:")
         for name, field in document.fields.items():
             print(f"  {name}: {field.value} (confianza: {field.confidence})")

     # Opcional: imprimir resultados completos en JSON
     print("\nResultado completo:")
     print(json.dumps(result.to_dict(), indent=2, ensure_ascii=False))
     ```
   - **Explicación:**  
     - Se configura el cliente con el endpoint y clave.  
     - Se envía una solicitud para analizar el documento a partir de una URL.  
     - Se recorren los campos extraídos y se muestran con sus valores y niveles de confianza.

5. **Ejecutar el script:**
   ```bash
   python form_extraction.py
   ```
   - Revisa la salida para confirmar que se han extraído correctamente los campos del documento.