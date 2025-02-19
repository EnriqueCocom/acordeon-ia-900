# Práctica 3: Desarrollo de un Custom Skill para Enriquecer Documentos

**Objetivo:**  
Implementar una función personalizada (Custom Skill) que se integre en un pipeline de Azure Cognitive Search para enriquecer la información extraída de documentos, por ejemplo, agregando análisis semántico o categorización avanzada.

### Pasos:

1. **Conceptualización del Custom Skill:**  
   - Un Custom Skill es una función que toma como entrada datos extraídos y devuelve información adicional.  
   - Ejemplo: Recibir el contenido de un documento y devolver una categoría basada en palabras clave.

2. **Implementación con Azure Functions:**  
   - Crea una Azure Function en Python que actúe como Custom Skill.
   - En [Azure Portal](https://portal.azure.com), crea un recurso de Azure Functions y configura un plan de consumo.
   - Descarga y configura la herramienta [Azure Functions Core Tools](https://docs.microsoft.com/azure/azure-functions/functions-run-local).

3. **Código de la Azure Function:**
   - Crea un nuevo proyecto de Azure Functions en Python.
   - Añade una función HTTP Trigger, por ejemplo, `customSkill.py`:
     ```python
     import logging
     import azure.functions as func
     import json

     def main(req: func.HttpRequest) -> func.HttpResponse:
         logging.info('Custom Skill function processed a request.')
         try:
             req_body = req.get_json()
         except ValueError:
             return func.HttpResponse("Invalid JSON", status_code=400)

         # Supongamos que el input contiene un campo "text" con el contenido del documento
         text = req_body.get("text", "")
         # Ejemplo de categorización simple basada en palabras clave
         if "factura" in text.lower():
             category = "Factura"
         elif "contrato" in text.lower():
             category = "Contrato"
         else:
             category = "Otro"

         # Devolver el resultado en el formato esperado por Cognitive Search
         result = {
             "values": [
                 {
                     "recordId": req_body.get("recordId", "0"),
                     "data": {
                         "category": category
                     }
                 }
             ]
         }
         return func.HttpResponse(json.dumps(result), mimetype="application/json", status_code=200)
     ```
   - **Explicación:**  
     - La función recibe una solicitud JSON, procesa el campo "text" y determina una categoría basada en reglas simples.  
     - Devuelve la salida en el formato requerido para Custom Skills en Cognitive Search.

4. **Desplegar y Probar la Azure Function:**  
   - Sigue la documentación para desplegar la función en Azure.  
   - Prueba la función utilizando Postman o la herramienta integrada en el portal, enviando un JSON con un campo "text".