# Práctica 2: Desarrollo de un Chatbot Generativo con Azure AI Studio y OpenAI

**Objetivo:**  
Construir un chatbot básico que utilice Azure AI Studio para configurar la interacción y Azure OpenAI Service para generar respuestas en lenguaje natural.

### Paso a Paso:

1. **Acceder a Azure AI Studio:**
   - Inicia sesión en [Azure AI Studio](https://studio.azure.com) y crea un nuevo proyecto de chatbot.
   - Selecciona la opción para integrar un modelo generativo (por ejemplo, utilizando Azure OpenAI Service como backend).

2. **Configurar el Chatbot en Azure AI Studio:**
   - Diseña la interfaz conversacional utilizando el diseñador visual que ofrece la plataforma.
   - Define intents básicos y flujos de diálogo, dejando que la parte generativa se encargue de la respuesta final.

3. **Integrar el Modelo Generativo:**
   - En la configuración del chatbot, especifica el endpoint y la clave de Azure OpenAI Service (como en la práctica 1).
   - Configura el flujo para que, ante una consulta del usuario, se envíe un prompt al modelo y se reciba la respuesta.

4. **Ejemplo de Flujo:**
   - Usuario: "¿Cuál es el futuro de la inteligencia artificial?"
   - Chatbot: Envía el prompt "Responde de manera creativa: ¿Cuál es el futuro de la inteligencia artificial?" al modelo de OpenAI y devuelve la respuesta generada.

5. **Prueba y Ajuste:**
   - Prueba el chatbot en el entorno de pruebas integrado en Azure AI Studio.
   - Ajusta parámetros y el flujo de diálogo según las respuestas obtenidas.

6. **Documentación y Despliegue:**
   - Una vez satisfecho, publica el chatbot en un entorno de pruebas o integración para que pueda ser utilizado en una web o aplicación.
