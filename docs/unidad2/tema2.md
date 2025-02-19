# Tema Complementario 2: Optimización del Consumo de la API y Manejo de Límite de Solicitudes

### Descripción  
Dado que las APIs de Azure Computer Vision tienen límites de uso y costos asociados, es crucial implementar estrategias para optimizar su consumo. Esto implica gestionar errores, evitar solicitudes redundantes y aplicar técnicas de reintentos que respeten los límites.

### Aspectos Clave

1. **Manejo de Errores y Reintentos:**  
   - Capturar respuestas de error (por ejemplo, códigos HTTP 429 o 500).
   - Implementar lógica para reintentar solicitudes fallidas utilizando técnicas como backoff exponencial.

2. **Uso de Colas o Caché:**  
   - Implementar sistemas de caché para almacenar resultados de solicitudes frecuentes y reducir llamadas a la API.
   - Usar colas para organizar solicitudes cuando se presentan picos de tráfico.

3. **Implementación de Backoff Exponencial:**  
   - Técnica que aumenta el tiempo de espera entre reintentos tras un error, reduciendo la presión sobre la API.

### Ejemplo de Código en Python con Reintentos y Backoff

#### Paso 1: Instalar la Librería 'requests' (si no está instalada)
```bash
pip install requests
```

#### Paso 2: Código de Ejemplo con Backoff Exponencial
```python
import requests
import time

subscription_key = "<tu-clave>"
endpoint = "https://<tu-endpoint>.cognitiveservices.azure.com/vision/v3.2/analyze?visualFeatures=Description,Tags"
headers = {
    "Ocp-Apim-Subscription-Key": subscription_key,
    "Content-Type": "application/json"
}
data = {"url": "https://ejemplo.com/imagen.jpg"}

def request_with_backoff(url, headers, data, max_retries=5, initial_wait=1):
    retries = 0
    wait_time = initial_wait
    while retries < max_retries:
        response = requests.post(url, headers=headers, json=data)
        if response.status_code == 200:
            return response.json()
        elif response.status_code in [429, 500, 503]:
            print(f"Error {response.status_code}: reintentando en {wait_time} segundos...")
            time.sleep(wait_time)
            wait_time *= 2  # Incrementa el tiempo de espera exponencialmente
            retries += 1
        else:
            response.raise_for_status()
    raise Exception("Máximo de reintentos alcanzado.")

result = request_with_backoff(endpoint, headers, data)
print(result)
```

#### Explicación del Código  
- **Función `request_with_backoff`:**  
  - Intenta enviar la solicitud y, si se recibe un error temporal (como 429, 500 o 503), espera un tiempo que se duplica en cada reintento.
  - Si se alcanza el máximo de reintentos, se lanza una excepción.
- **Aplicación Práctica:**  
  - Esta estrategia evita saturar la API y ayuda a gestionar picos de tráfico y limitaciones de cuota, optimizando el consumo y reduciendo costos.