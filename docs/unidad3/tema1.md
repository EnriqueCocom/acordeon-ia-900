# Tema Complementario 1: Preprocesamiento y Limpieza Avanzada de Datos Textuales

### Descripción  
El preprocesamiento es fundamental para mejorar la calidad de los datos que se envían a las APIs de NLP. Un procesamiento adecuado reduce el ruido, mejora la consistencia y facilita la extracción de información. Esto incluye la normalización del texto, tokenización, eliminación de stopwords, lematización y corrección ortográfica.

### Aspectos Clave y Pasos a Seguir

1. **Tokenización y Normalización:**  
   - **Definición:** La tokenización divide el texto en palabras, frases u oraciones; la normalización consiste en transformar el texto a un formato estándar (minúsculas, eliminación de puntuación, etc.).
   - **Herramientas:** Librerías como NLTK o spaCy en Python.
   - **Ejemplo con NLTK:**
     ```python
     import nltk
     from nltk.tokenize import word_tokenize
     import string

     nltk.download('punkt')  # Descargar el modelo de tokenización

     texto = "¡Hola! Este es un ejemplo de preprocesamiento de texto para NLP."
     # Convertir a minúsculas y eliminar puntuación
     texto_normalizado = texto.lower().translate(str.maketrans('', '', string.punctuation))
     tokens = word_tokenize(texto_normalizado)
     print("Tokens:", tokens)
     ```
   - **Explicación:**  
     - Se convierte el texto a minúsculas para uniformizarlo.  
     - Se eliminan los signos de puntuación.  
     - La función `word_tokenize` divide el texto en palabras.

2. **Eliminación de Stopwords:**  
   - **Definición:** Se trata de remover palabras comunes (como “el”, “de”, “y”) que no aportan significado relevante para el análisis.
   - **Ejemplo con NLTK:**
     ```python
     from nltk.corpus import stopwords
     nltk.download('stopwords')

     stop_words = set(stopwords.words('spanish'))
     tokens_filtrados = [word for word in tokens if word not in stop_words]
     print("Tokens sin stopwords:", tokens_filtrados)
     ```
   - **Explicación:**  
     - Se utiliza el conjunto de stopwords en español y se filtran de la lista de tokens.

3. **Lematización:**  
   - **Definición:** Consiste en reducir las palabras a su forma base o “lema”.
   - **Herramientas:** spaCy es muy eficaz para esta tarea.
   - **Ejemplo con spaCy:**
     ```python
     import spacy

     # Descargar el modelo en español (si es necesario)
     # python -m spacy download es_core_news_sm
     nlp = spacy.load("es_core_news_sm")
     doc = nlp("Los gatos están corriendo y los perros estaban ladrando")
     lemas = [token.lemma_ for token in doc]
     print("Lemas:", lemas)
     ```
   - **Explicación:**  
     - Se carga el modelo en español de spaCy.  
     - Se procesa el texto para extraer la forma base de cada palabra.

4. **Corrección Ortográfica (Opcional):**  
   - **Definición:** Detectar y corregir errores ortográficos para mejorar la calidad del texto.
   - **Herramientas:** Librerías como TextBlob o pyspellchecker.
   - **Ejemplo con pyspellchecker:**
     ```python
     from spellchecker import SpellChecker

     spell = SpellChecker(language='es')
     palabras = ["exelente", "servcio", "rápido"]
     correcciones = {word: spell.correction(word) for word in palabras}
     print("Correcciones:", correcciones)
     ```
   - **Explicación:**  
     - Se utiliza pyspellchecker para sugerir la corrección de palabras mal escritas.

### Beneficios  
Un preprocesamiento robusto mejora la precisión en la detección de sentimiento, extracción de entidades y demás tareas de NLP, asegurando que el texto se encuentra en la mejor forma posible para ser analizado por los servicios de Azure.