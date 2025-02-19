# Práctica 3: Implementación de Filtros de Seguridad para Salidas Generativas

**Objetivo:**  
Diseñar e implementar un mecanismo de post-procesamiento que filtre y valide las salidas generadas por el modelo, asegurando que cumplan con criterios éticos y de contenido responsable.

### Paso a Paso:

1. **Definir Criterios de Filtro:**
   - Establece una lista de palabras o frases que sean inaceptables o sensibles.
   - Define reglas de validación (por ejemplo, longitud mínima/máxima, evitar contenido ofensivo).

2. **Implementar el Filtro en Python:**
   - Crea un archivo llamado `generative_filter.py` con el siguiente ejemplo:
     ```python
     import re

     # Lista de palabras prohibidas
     banned_words = ["ofensivo", "inapropiado", "peligroso"]

     def filter_output(text):
         # Verificar si alguna palabra prohibida está presente
         for word in banned_words:
             if re.search(r'\b' + re.escape(word) + r'\b', text, re.IGNORECASE):
                 return "El contenido generado ha sido filtrado por contener términos sensibles."
         # Validar longitud (ejemplo: mínimo 20 caracteres)
         if len(text) < 20:
             return "El contenido generado es demasiado corto."
         return text

     # Ejemplo de uso
     salida_generada = "Este es un ejemplo de texto ofensivo que puede ser inadecuado."
     salida_filtrada = filter_output(salida_generada)
     print("Salida filtrada:")
     print(salida_filtrada)
     ```
   - **Explicación:**
     - Se utiliza una expresión regular para buscar palabras prohibidas.
     - Se verifica la longitud mínima.
     - Si se detecta algún criterio de rechazo, se devuelve un mensaje indicando que la salida ha sido filtrada.

3. **Integración en el Pipeline de Generación:**
   - Modifica el script de la Práctica 1 para que, después de recibir la salida generada, se pase por el filtro:
     ```python
     # ... Código previo de generación de texto ...

     texto_generado = result.get("choices", [{}])[0].get("text", "")
     from generative_filter import filter_output
     texto_seguro = filter_output(texto_generado)
     print("Texto Generado y Filtrado:")
     print(texto_seguro)
     ```

4. **Prueba y Validación:**
   - Ejecuta el script y prueba con diferentes prompts que puedan generar contenido sensible.
   - Ajusta la lista de palabras y los criterios según sea necesario.