# Tema Complementario 1: Preprocesamiento y Normalización de Documentos

### Descripción  
Antes de aplicar técnicas de minería de conocimiento e inteligencia de documentos, es esencial procesar y normalizar la información contenida en documentos no estructurados. Esto implica limpiar, convertir y estandarizar los datos para maximizar la precisión de la extracción y análisis.

### Puntos Clave

1. **Conversión y limpieza de datos:**
   - **OCR y corrección de errores:** Uso de algoritmos de reconocimiento óptico de caracteres (OCR) para transformar imágenes o PDF en texto. Se debe complementar con correctores ortográficos y de formato.
   - **Eliminación de ruido:** Remoción de caracteres extraños, espacios excesivos y marcas que no aportan información.

2. **Normalización del texto:**
   - **Tokenización y eliminación de stopwords:** Dividir el texto en unidades básicas (palabras o tokens) y eliminar palabras de uso común sin significado semántico.
   - **Lematización:** Convertir las palabras a su forma base para un análisis consistente.
   - **Conversión a un formato uniforme:** Por ejemplo, transformar todos los caracteres a minúsculas y eliminar acentos.

3. **Ejemplo Práctico con Python:**
   - Utilización de bibliotecas como **Pillow**, **OpenCV**, **NLTK** y **spaCy** para preprocesar textos extraídos.  
   - **Ejemplo de código:**
     ```python
     import cv2
     import pytesseract
     from nltk.tokenize import word_tokenize
     from nltk.corpus import stopwords
     import spacy
     import string

     # Paso 1: Convertir una imagen de documento a texto (OCR)
     imagen = cv2.imread("documento.jpg")
     texto_extraido = pytesseract.image_to_string(imagen, lang="spa")

     # Paso 2: Normalización del texto
     # Convertir a minúsculas y eliminar puntuación
     texto_normalizado = texto_extraido.lower().translate(str.maketrans('', '', string.punctuation))
     
     # Paso 3: Tokenización y eliminación de stopwords
     tokens = word_tokenize(texto_normalizado, language="spanish")
     nltk_stopwords = set(stopwords.words("spanish"))
     tokens_filtrados = [token for token in tokens if token not in nltk_stopwords]

     # Paso 4: Lematización con spaCy
     nlp = spacy.load("es_core_news_sm")
     doc = nlp(" ".join(tokens_filtrados))
     lemas = [token.lemma_ for token in doc]
     print("Texto preprocesado:", " ".join(lemas))
     ```
   - **Explicación:**  
     Se extrae texto de una imagen, se normaliza, se tokeniza y se lematiza para obtener un texto limpio y uniforme, listo para análisis avanzado.

### Beneficios  
Un preprocesamiento robusto mejora la calidad de los datos de entrada, lo que se traduce en una mayor precisión en la extracción de campos y en la minería de conocimiento.
