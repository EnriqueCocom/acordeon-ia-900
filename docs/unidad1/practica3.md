# Práctica 3: Crear un Chatbot Básico con Azure Bot Service  
**Objetivo:** Desarrollar un chatbot sencillo que utilice capacidades de NLP de Azure, implementándolo mediante Azure Bot Service y el Bot Framework Composer.

#### Paso a Paso:

1. **Crear el recurso del Bot en Azure:**
   - Inicia sesión en [Azure Portal](https://portal.azure.com).
   - Selecciona “Crear un recurso” y busca “Azure Bot”.
   - Configura el bot (elige el tipo “Web App Bot” o “Bot Channels Registration”) y crea el recurso.
   - Una vez creado, toma nota del *App ID* y la *clave* que se usarán para la autenticación.

2. **Utilizar Bot Framework Composer:**
   - Descarga e instala [Bot Framework Composer](https://github.com/microsoft/BotFramework-Composer) en tu equipo.
   - Abre Composer y selecciona “Nuevo Bot” utilizando una plantilla básica (por ejemplo, “Echo Bot”).
   - Configura el bot agregando un trigger que responda a mensajes simples (puedes modificar la respuesta para que salude y pregunte en lenguaje natural).
   - Guarda y publica el bot siguiendo las instrucciones de Composer. Esto incluirá conectarlo al recurso de Azure Bot que creaste.

3. **Probar el Bot:**
   - Una vez publicado, accede a la sección “Test in Web Chat” en el Azure Portal o usa el simulador integrado en Composer.
   - Envía mensajes al bot y verifica que responda de acuerdo con el diálogo diseñado.
   - Si deseas ampliar las capacidades, integra la API de Text Analytics (ver Práctica 5) para analizar la intención o sentimiento del usuario.