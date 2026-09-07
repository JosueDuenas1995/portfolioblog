# Portfolio Website Using ORACLE OCI Infraestructure

## Despliegue de Portafolio Profesional Full-Stack

### 🚀 Resumen del Proyecto
Despliegue de un portafolio web moderno, responsivo y seguro, montado sobre una arquitectura Cloud autogestionada. El sistema implementa un flujo completo de captura de datos en el frontend y procesamiento en el backend para la automatización de mensajería.

---

### 🛠️ Stack Tecnológico
* **Frontend:** HTML5, CSS3, Bootstrap 5.3.3 (Estilos adaptativos y modo oscuro dinámico).
* **Backend:** Python, FastAPI (Framework asíncrono de alto rendimiento), Pydantic (Validación de esquemas de datos).
* **Servidor y Cloud:** Oracle Cloud Infrastructure (OCI) (Instancia Compute Ubuntu Linux), Nginx (Servidor web y Proxy Inverso).
* **Automatización de Mensajería:** Protocolo SMTP integrado con `smtplib` y `email.mime`.

---

### 📝 Proceso de Desarrollo Paso a Paso

#### Paso 1: Configuración de la Infraestructura en la Nube
* Creación y aprovisionamiento de una máquina virtual Ubuntu en Oracle Cloud (OCI).
* Configuración de listas de seguridad del sistema (Firewall) abriendo puertos HTTP (`80`) y HTTPS (`443`).
* Acceso SSH cifrado mediante llaves criptográficas privadas para la gestión del servidor.

#### Paso 2: Construcción de la API en el Backend
* Desarrollo de una API REST con FastAPI implementando el endpoint seguro `POST /api/contact`.
* Definición de esquemas de datos estructurados con Pydantic Models (`ContactForm`) para garantizar la recepción estricta de tipos de datos (`EmailStr` y `str`).
* Programación del motor de mensajería asíncrona mediante un socket SMTP conectado al puerto TLS de salida.

#### Paso 3: Frontend e Integración Asíncrona (AJAX)
* Maquetación responsiva utilizando componentes interactivos de Bootstrap.
* Implementación de JavaScript moderno mediante la Fetch API (`async/await`) para transferir los datos del formulario en formato JSON nativo sin recargar la página (`e.preventDefault()`).
* Desarrollo de scripts dinámicos para la actualización automatizada del año de derechos de autor y conmutación de clases CSS para el tema visual.

#### Paso 4: Despliegue en Producción y Proxy Inverso
* Configuración de la carpeta raíz de producción en `/var/www/portfolio-frontend` para el servicio de archivos estáticos.
* Configuración de Nginx actuando como Proxy Inverso para mapear el tráfico público del dominio hacia la aplicación local de FastAPI gestionada por Uvicorn en el puerto interno `8000`.

---

### 🛡️ Protocolos de Seguridad e Infraestructura Robustecida
* **Políticas CORS (Cross-Origin Resource Sharing):** Configuración estricta de Middlewares en FastAPI para restringir los orígenes, permitiendo peticiones únicamente desde el dominio oficial en producción (`allow_origins`).
* **Aislamiento de Credenciales (Variables de Entorno):** Uso de archivos `.env` protegidos para encapsular datos críticos (servidor SMTP, contraseñas de aplicación). Ninguna credencial está expuesta directamente en el código fuente.
* **Gestión de Procesos con Systemd:** Creación de un servicio nativo de Linux (`portfolio-backend.service`) con directivas `EnvironmentFile` y políticas de resiliencia ante caídas de servicio (`Restart=always`).
* **Validación de Capas contra Inyecciones:** Sanitización y validación automática de datos de entrada mediante Pydantic en el Backend, mitigando el riesgo de payloads maliciosos.


