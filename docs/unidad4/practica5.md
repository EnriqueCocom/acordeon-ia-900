# Práctica 5: Evaluación y Análisis de la Precisión de la Minería de Conocimiento

**Objetivo:**  
Implementar un sistema de evaluación para medir la precisión y efectividad de la extracción de datos e indexación en documentos. Esto es especialmente útil para afinar el modelo y mejorar el rendimiento en producción.

### Pasos:

1. **Definir un Conjunto de Datos de Validación:**  
   - Prepara un conjunto de documentos de prueba con datos etiquetados manualmente (por ejemplo, valores esperados para campos como “fecha”, “monto”, etc.).

2. **Extraer Datos de los Documentos:**
   - Utiliza el servicio de Form Recognizer (o el pipeline que creaste) para procesar cada documento y extraer sus campos.
   - Guarda los resultados en un formato estructurado (por ejemplo, CSV o JSON).

3. **Comparar Resultados con los Valores Esperados:**
   - Escribe un script en Python que lea los resultados extraídos y los compare con las etiquetas manuales.
   - Calcula métricas como la precisión, el recall y el F1-score para cada campo.
   
   **Ejemplo de Código:**
   ```python
   import pandas as pd
   from sklearn.metrics import precision_score, recall_score, f1_score

   # Supón que tienes un CSV con columnas: 'id', 'campo', 'valor_esperado', 'valor_extraido'
   df = pd.read_csv("resultados_validacion.csv")

   # Función para calcular métricas para un campo específico
   def evaluar_campo(campo):
       df_campo = df[df['campo'] == campo]
       y_true = df_campo['valor_esperado']
       y_pred = df_campo['valor_extraido']
       precision = precision_score(y_true, y_pred, average='micro')
       recall = recall_score(y_true, y_pred, average='micro')
       f1 = f1_score(y_true, y_pred, average='micro')
       return precision, recall, f1

   campos = df['campo'].unique()
   for campo in campos:
       prec, rec, f1 = evaluar_campo(campo)
       print(f"Campo: {campo}")
       print(f"  Precisión: {prec:.2f}")
       print(f"  Recall: {rec:.2f}")
       print(f"  F1-Score: {f1:.2f}\n")
   ```
   - **Explicación:**  
     - Se asume que se dispone de un conjunto de validación etiquetado.  
     - Se calculan métricas para evaluar el desempeño de la extracción de cada campo.
   
4. **Iteración y Mejoras:**
   - Utiliza los resultados para identificar áreas de mejora en el modelo (por ejemplo, campos con baja precisión).
   - Ajusta el preprocesamiento o entrena modelos personalizados en Form Recognizer según sea necesario.