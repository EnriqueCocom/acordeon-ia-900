# Práctica 4: Fine-tuning Simulado con Datos Personalizados (Ejercicio Conceptual)

**Objetivo:**  
Aunque AI‑900 no requiere que entrenes modelos desde cero, este ejercicio avanzado simula el proceso de fine-tuning (ajuste fino) de un modelo generativo con datos personalizados para mejorar la relevancia en un dominio específico.

### Paso a Paso:

1. **Recolección de Datos:**
   - Reúne un conjunto de ejemplos de texto que sean representativos del dominio deseado (por ejemplo, descripciones de productos tecnológicos).

2. **Preparación de Datos:**
   - Limpia y formatea los textos para que sean consistentes.
   - Crea un archivo JSON con ejemplos de prompt-respuesta que representen el comportamiento deseado.

3. **Simulación de Fine-Tuning (Ejercicio Conceptual):**
   - Dado que el fine-tuning real en Azure OpenAI Service requiere permisos y recursos avanzados, simula el proceso utilizando un script que ajuste el prompt basado en ejemplos.
   - **Ejemplo de Script de Simulación:**
     ```python
     import json

     # Ejemplos personalizados (simulados)
     ejemplos = [
         {"prompt": "Describe las características de un smartphone moderno.", "respuesta": "Un smartphone moderno cuenta con pantalla AMOLED, múltiples cámaras y conectividad 5G."},
         {"prompt": "Explica la importancia de la batería en un dispositivo móvil.", "respuesta": "La batería determina la duración y eficiencia del dispositivo, siendo crucial para un uso prolongado."}
     ]

     # Función para seleccionar un ejemplo basado en similitud simple (basada en coincidencia de palabras clave)
     def seleccionar_ejemplo(prompt):
         for ejemplo in ejemplos:
             if any(palabra in prompt.lower() for palabra in ejemplo["prompt"].lower().split()):
                 return ejemplo["respuesta"]
         return "Lo siento, no tengo información específica sobre ese tema."

     # Ejemplo de uso
     prompt_usuario = "Cuéntame sobre las características de un smartphone."
     respuesta_simulada = seleccionar_ejemplo(prompt_usuario)
     print("Respuesta Simulada Fine-Tuning:")
     print(respuesta_simulada)
     ```
   - **Explicación:**
     - Se utiliza una lista de ejemplos como guía.
     - La función intenta encontrar similitudes simples para devolver una respuesta "ajustada" según los datos personalizados.

4. **Discusión y Evaluación:**
   - Aunque este ejercicio es conceptual, discute cómo el fine-tuning real implicaría entrenar un modelo con estos ejemplos, ajustando pesos y parámetros para mejorar la salida en un dominio específico.