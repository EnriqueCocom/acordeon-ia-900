# Tema Complementario 1: Preprocesamiento de Imágenes para Mejorar el Rendimiento de Computer Vision

### Descripción  
El preprocesamiento de imágenes es fundamental para mejorar la precisión y eficiencia de los modelos de Computer Vision. Transformar y limpiar las imágenes (por ejemplo, redimensionar, normalizar y ajustar el contraste) reduce el ruido y los detalles irrelevantes, lo que facilita que los algoritmos extraigan características importantes.

### Aspectos Clave

1. **Técnicas de Normalización y Escalado:**  
   - **Redimensionado:** Ajustar el tamaño de la imagen a dimensiones fijas para estandarizar la entrada a los modelos.  
   - **Normalización:** Escalar los valores de píxeles (por ejemplo, de 0 a 1) para que las diferencias de iluminación o saturación no afecten el análisis.  
   - **Ajuste de Contraste y Brillo:** Mejorar la visibilidad de los detalles importantes.

2. **Uso de Bibliotecas: OpenCV y Pillow:**  
   - **OpenCV:** Potente librería de visión por computadora que permite aplicar filtros, detectar bordes, y realizar transformaciones geométricas.  
   - **Pillow:** Biblioteca de Python para procesamiento de imágenes, útil para tareas de apertura, conversión y guardado de imágenes en diferentes formatos.

3. **Ejemplo Práctico: Convertir una Imagen a Escala de Grises para Optimizar la Detección de Bordes**  
   La conversión a escala de grises elimina la información de color, reduciendo la complejidad de la imagen y haciendo que la detección de bordes sea más robusta.

### Ejemplo de Código con OpenCV y Pillow

#### Paso 1: Instalación de las Librerías

En tu terminal, instala OpenCV y Pillow:
```bash
pip install opencv-python pillow
```

#### Paso 2: Código para Preprocesamiento de la Imagen
```python
import cv2
from PIL import Image
import numpy as np

# Cargar imagen usando Pillow
ruta_imagen = "ruta/a/tu/imagen.jpg"
imagen_pil = Image.open(ruta_imagen)

# Convertir a escala de grises con Pillow
imagen_gris_pil = imagen_pil.convert("L")
imagen_gris_pil.save("imagen_gris_pil.jpg")

# También se puede utilizar OpenCV para convertir a escala de grises
imagen_cv = cv2.imread(ruta_imagen)
imagen_gris_cv = cv2.cvtColor(imagen_cv, cv2.COLOR_BGR2GRAY)
cv2.imwrite("imagen_gris_cv.jpg", imagen_gris_cv)

# Mostrar ambas imágenes para comparación
cv2.imshow("Imagen en Escala de Grises (OpenCV)", imagen_gris_cv)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

#### Explicación del Código  
- **Carga y Conversión:**  
  - Se carga la imagen con Pillow y se convierte a escala de grises usando el método `convert("L")`.
  - Con OpenCV, se utiliza `cv2.cvtColor` para transformar la imagen de BGR (formato por defecto en OpenCV) a escala de grises.
- **Guardado y Visualización:**  
  - Se guardan ambas versiones para su análisis.
  - Se utiliza `cv2.imshow` para mostrar la imagen procesada con OpenCV, permitiendo verificar visualmente la eliminación de la información de color y la mejora en la detección de bordes.