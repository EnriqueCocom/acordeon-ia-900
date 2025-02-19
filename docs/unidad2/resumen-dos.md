# 2. Aspectos básicos de Microsoft Azure AI: Computer Vision

A continuación se presenta un resumen detallado y enfocado en los **Aspectos básicos de Microsoft Azure AI: Computer Vision** según el contenido de Microsoft Learn para la certificación AI‑900.

## 1. Aspectos básicos de Computer Vision

**Computer Vision** es la disciplina que permite a las máquinas interpretar y comprender el contenido visual de imágenes y vídeos. En el contexto de Azure, se utilizan servicios que facilitan la integración de capacidades de análisis de imágenes en aplicaciones sin necesidad de construir modelos desde cero.

### Conceptos Clave

- **Análisis de Imágenes:**  
  Se refiere a la capacidad de extraer información significativa de imágenes. Esto incluye identificar objetos, describir escenas y clasificar imágenes en categorías (por ejemplo, identificar si una imagen contiene una playa, un edificio, o un vehículo).

- **Características Principales:**  
  - **Clasificación de Imágenes:** Permite asignar etiquetas a una imagen basándose en su contenido.  
  - **Detección de Objetos:** Identifica y localiza objetos específicos dentro de una imagen, dibujando “cajas” alrededor de ellos.  
  - **Extracción de Características Visuales:** Extrae atributos y metadatos relevantes (por ejemplo, colores dominantes, patrones o formas).

### Ejemplo de Aplicación  
Una aplicación que analiza imágenes de redes sociales puede usar Computer Vision para etiquetar automáticamente las fotos (por ejemplo, “naturaleza”, “ciudad”, “persona”) y ayudar a organizar y buscar imágenes de manera más eficiente.

---

## 2. Aspectos básicos del reconocimiento facial

El reconocimiento facial es una subárea de Computer Vision que se especializa en identificar y analizar rostros humanos en imágenes y vídeos.

### Conceptos Clave

- **Detección de Rostros:**  
  Identifica la ubicación de los rostros en una imagen. El servicio detecta las coordenadas (por ejemplo, la posición y el tamaño de cada cara) sin necesariamente identificar a la persona.

- **Reconocimiento y Verificación:**  
  Permite comparar rostros para determinar si dos imágenes pertenecen a la misma persona. Se utilizan algoritmos que extraen “huellas digitales” (features faciales) que se pueden comparar entre sí.

- **Análisis de Atributos Faciales:**  
  Además de detectar y reconocer, el servicio puede analizar características del rostro, tales como:
  - **Edad estimada**  
  - **Género**  
  - **Emociones predominantes (por ejemplo, felicidad, tristeza, sorpresa)**

### Ejemplo de Aplicación  
Un sistema de seguridad que utilice reconocimiento facial puede verificar la identidad de una persona al comparar su rostro con una base de datos almacenada. Asimismo, aplicaciones de marketing pueden analizar las emociones en tiempo real para adaptar experiencias personalizadas.

---

## 3. Aspectos básicos del reconocimiento óptico de caracteres (OCR)

El reconocimiento óptico de caracteres (OCR) es la tecnología que permite extraer texto de imágenes y documentos escaneados, convirtiendo contenido visual en información legible y procesable por máquinas.

### Conceptos Clave

- **Extracción de Texto:**  
  OCR identifica y convierte letras, números y símbolos presentes en una imagen en datos de texto. Esto permite, por ejemplo, digitalizar documentos impresos o extraer información de señales y placas.

- **Procesamiento de Imágenes para OCR:**  
  Los algoritmos detectan zonas de texto en la imagen, segmentan las letras y luego utilizan modelos entrenados para reconocer cada carácter. Es fundamental en escenarios en los que se necesita automatizar la lectura de facturas, recibos o formularios.

- **Formatos y Lenguajes:**  
  Los servicios de OCR de Azure son capaces de trabajar con múltiples idiomas y diversos tipos de formatos de documentos, ofreciendo resultados en un formato estructurado que facilita su posterior análisis o almacenamiento.

### Ejemplo de Aplicación  
Un sistema de gestión documental en una empresa puede usar OCR para convertir archivos escaneados en texto editable y buscable, lo que agiliza la indexación y recuperación de información.
