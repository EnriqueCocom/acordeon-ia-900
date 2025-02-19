# Tema Complementario 3: Integración de Resultados de Computer Vision con Otras Soluciones de Azure

### Descripción  
La integración de resultados de Computer Vision con otros servicios de Azure permite construir soluciones completas que combinan análisis visual y textual. Por ejemplo, se puede extraer texto con OCR y luego realizar análisis de sentimiento o integrar la información en Azure Cognitive Search para mejorar la búsqueda y organización de datos.

### Aspectos Clave

1. **Diseño de Flujos de Trabajo Multiservicio:**  
   - Orquestar varios servicios mediante Azure Logic Apps o Azure Functions para procesar datos en serie.
   - Diseñar pipelines que tomen la salida de Computer Vision (por ejemplo, etiquetas y descripciones) y la combinen con resultados de OCR y análisis de sentimiento.

2. **Ejemplos de Arquitecturas Híbridas:**  
   - Una solución de gestión documental que utiliza OCR para digitalizar documentos y Computer Vision para categorizar imágenes, integrándose luego en una base de datos y en Azure Cognitive Search para indexación.

3. **Mejores Prácticas para Integración y Almacenamiento:**  
   - Estandarizar el formato de salida (por ejemplo, JSON) para facilitar la integración.
   - Utilizar Azure Storage y bases de datos como Cosmos DB para almacenar resultados.

### Ejemplo de Flujo Integrado (Conceptual)

- **Paso 1:** La aplicación envía una imagen a la API de Computer Vision para obtener etiquetas y descripciones.  
- **Paso 2:** Se usa OCR para extraer cualquier texto presente.  
- **Paso 3:** Los resultados se envían a un servicio de análisis de sentimiento (por ejemplo, Azure Text Analytics) para interpretar el contexto del texto extraído.  
- **Paso 4:** Todos los datos se integran en un sistema central (como Azure Cosmos DB) y se indexan mediante Azure Cognitive Search, facilitando la búsqueda y recuperación.

Aunque este flujo puede variar según la solución, la integración se puede implementar con Azure Functions, orquestadas mediante Logic Apps, lo que permite la automatización completa del proceso.