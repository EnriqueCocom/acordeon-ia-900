# Tema Complementario 4: Seguridad, Privacidad y Autenticación en Azure AI

### Descripción  
Garantizar la seguridad de los datos y de las aplicaciones es fundamental en cualquier solución de IA. Este tema profundiza en cómo proteger el acceso a los servicios de Azure AI y cómo cumplir con normativas internacionales.

### Aspectos Clave

1. **Gestión de Claves y Endpoints:**  
   - **Configuración y Rotación:**  
     Explicar cómo obtener y almacenar de forma segura las claves de suscripción y endpoints desde el Azure Portal.  
     - **Procedimiento Paso a Paso:**  
       1. Acceder a “Claves y Endpoint” en el recurso de Azure AI.  
       2. Copiar las claves y almacenarlas en un entorno seguro (por ejemplo, Azure Key Vault).  
       3. Configurar políticas de rotación periódica para minimizar riesgos en caso de exposición.
   - **Uso de Azure Key Vault:**  
     Implementar Key Vault en tus aplicaciones para centralizar y proteger las credenciales.

2. **Prácticas de Seguridad:**  
   - **Control de Acceso y Roles:**  
     - Definir roles y permisos (RBAC) para que solo usuarios y aplicaciones autorizadas accedan a los recursos.  
     - Configurar autenticación multifactor (MFA) para accesos críticos.
   - **Políticas de Red y Seguridad:**  
     - Implementar firewalls, redes virtuales (VNets) y reglas de acceso IP para limitar el tráfico.
   - **Ejercicio Práctico:**  
     - Configurar un Azure Key Vault y actualizar un script de Python para leer la clave desde Key Vault en lugar de estar codificada en el código.

3. **Cumplimiento y Normativas:**  
   - **Regulaciones:**  
     - Abordar normativas como GDPR, HIPAA y otras, que regulan el tratamiento de datos sensibles.  
     - Configurar políticas de retención y eliminación de datos en Azure Storage.
   - **Auditoría y Reportes:**  
     - Utilizar herramientas de auditoría de Azure para monitorear el acceso a recursos y generar reportes de conformidad.