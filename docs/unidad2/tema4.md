# Tema Complementario 4: Seguridad y Privacidad en el Uso de Servicios de Computer Vision

### Descripción  
La seguridad y privacidad son cruciales al trabajar con datos visuales, especialmente cuando las imágenes pueden contener información sensible o personal. Es vital implementar medidas para proteger las claves de acceso, controlar quién puede acceder a los datos y cumplir con normativas como GDPR.

### Aspectos Clave

1. **Configuración de Autenticación y Uso de Azure Key Vault:**  
   - **Azure Key Vault:** Es una herramienta que permite almacenar y gestionar claves, secretos y certificados de forma segura.  
   - **Implementación:** Integrar Key Vault en la aplicación para que las claves de la API no estén codificadas en el código fuente.

2. **Políticas de Acceso y Control de Datos Sensibles:**  
   - Definir roles y permisos (RBAC) para limitar el acceso a recursos de Computer Vision.  
   - Configurar políticas de acceso basadas en IP y habilitar la autenticación multifactor (MFA) para accesos críticos.

3. **Recomendaciones para Cumplir Normativas (GDPR, etc.):**  
   - Garantizar que los datos personales se procesen de acuerdo con las normativas de privacidad.  
   - Implementar medidas de encriptación y procedimientos para la eliminación segura de datos cuando ya no sean necesarios.

### Ejemplo de Uso de Azure Key Vault en Python

#### Paso 1: Instalación del SDK de Azure Key Vault
```bash
pip install azure-identity azure-keyvault-secrets
```

#### Paso 2: Código para Acceder a un Secreto Almacenado en Key Vault
```python
from azure.identity import DefaultAzureCredential
from azure.keyvault.secrets import SecretClient

# Configuración del Key Vault
key_vault_url = "https://<tu-key-vault>.vault.azure.net/"
credential = DefaultAzureCredential()
client = SecretClient(vault_url=key_vault_url, credential=credential)

# Obtener el secreto (por ejemplo, la clave de Computer Vision)
secret_name = "ComputerVisionApiKey"
retrieved_secret = client.get_secret(secret_name)
print("Clave obtenida:", retrieved_secret.value)
```

#### Explicación del Código  
- **DefaultAzureCredential:**  
  Proporciona un método unificado de autenticación en Azure, que se adapta al entorno (local, nube, etc.).  
- **SecretClient:**  
  Se utiliza para interactuar con el Key Vault y recuperar secretos de forma segura.