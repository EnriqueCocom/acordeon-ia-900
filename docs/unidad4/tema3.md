# Tema Complementario 3: Desarrollo de Modelos Personalizados para Reconocimiento de Formularios

### Descripción  
Aunque Azure ofrece modelos preentrenados para la extracción de datos de documentos, en algunos casos se requiere entrenar modelos personalizados que se adapten a formatos específicos de documentos (por ejemplo, formularios o facturas únicos).

### Puntos Clave

1. **Recolección y Etiquetado de Datos:**
   - **Selección de documentos representativos:** Recopilar una muestra diversa que refleje la variabilidad de los documentos.
   - **Etiquetado manual:** Usar herramientas como Form Recognizer Studio para marcar campos importantes (fecha, número de factura, total, etc.).

2. **Entrenamiento del Modelo:**
   - **Uso de Form Recognizer Studio:** Configurar y entrenar el modelo con la muestra etiquetada.
   - **Evaluación y ajuste:** Revisar la precisión del modelo y realizar iteraciones de entrenamiento ajustando los parámetros y ampliando la muestra de entrenamiento.

3. **Ejemplo Práctico:**
   - **Flujo en Form Recognizer Studio:**  
     1. Sube un conjunto de documentos a la herramienta.
     2. Etiqueta cada campo manualmente.
     3. Inicia el entrenamiento y evalúa los resultados.
     4. Publica el modelo y obtén el modelo ID.
   - **Integración en código (similar a Práctica 1):** Utilizar el modelo personalizado para analizar nuevos documentos y extraer datos con mayor precisión.

### Beneficios  
Desarrollar modelos personalizados permite optimizar la extracción de datos para formatos específicos, lo que mejora significativamente la precisión y confiabilidad en entornos empresariales con documentos complejos.