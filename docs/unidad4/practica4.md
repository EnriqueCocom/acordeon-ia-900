# Práctica 4: Construcción de un Pipeline Automatizado con Azure Logic Apps

**Objetivo:**  
Orquestar todo el proceso de minería de conocimiento: desde la extracción de datos de documentos con Form Recognizer, pasando por el enriquecimiento mediante Custom Skills, hasta la indexación en Cognitive Search.

### Pasos:

1. **Crear un Workflow en Azure Logic Apps:**  
   - En Azure Portal, crea un recurso de **Logic App**.
   - Selecciona una plantilla en blanco y diseña un flujo de trabajo.

2. **Diseño del Pipeline:**
   - **Paso 1:** Trigger – Por ejemplo, cuando un documento es subido a Azure Blob Storage.
   - **Paso 2:** Llamar al servicio de Form Recognizer para extraer datos.
   - **Paso 3:** Llamar a la Azure Function (Custom Skill) para enriquecer los datos.
   - **Paso 4:** Enviar los datos enriquecidos a Azure Cognitive Search para indexación.

3. **Configuración Paso a Paso:**
   - Agrega un trigger “When a blob is added or modified” que escuche un contenedor de Blob Storage.
   - Añade una acción “HTTP” para llamar a la API de Form Recognizer con la URL del documento.
   - Procesa la respuesta y, mediante otra acción “HTTP”, llama a la Azure Function desarrollada en la Práctica 3.
   - Por último, añade una acción “HTTP” para enviar los datos a Cognitive Search usando el endpoint de indexación (similar al ejercicio de indexación en la Práctica 2).

4. **Validación y Monitorización:**
   - Ejecuta el workflow subiendo un documento de prueba.
   - Monitorea el flujo en el portal de Logic Apps y verifica que cada acción se ejecute sin errores.