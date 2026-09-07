# Barberia Alura

Este proyecto despliega un sitio web estático en **Google Cloud Storage** usando Terraform.
El objetivo es ir actualizando el sitio ahora con su **back end**

# 📂 Contenido del Sitio Web (`/website`)

La carpeta `/website` encapsula el **código fuente frontend** de la aplicación, comprising los **activos estáticos** que conforman la interfaz de usuario del sitio web. Estos archivos están diseñados para ser servidos directamente desde un **bucket de Google Cloud Storage (GCS)**, aprovechando sus capacidades de **hosting de sitios web estáticos**.

### Estructura y Componentes Clave:

-   **`index.html`**: El punto de entrada principal del sitio web, sirviendo como la página de inicio.
    
-   **`404.html`**: Una página de error personalizada, configurada para ser mostrada por GCS cuando se solicita un recurso no encontrado.
    
-   **`css/`**: Contiene hojas de estilo en cascada (`.css`) para la presentación y el diseño visual de la aplicación.
    
-   **`images/`**: Directorio para los activos gráficos (e.g., `.png`, `.jpg`, `.svg`) que se incrustan en las páginas web.
    
-   **`js/`**: Archivos JavaScript (`.js`) que proporcionan interactividad y lógica del lado del cliente.

![Imagen de infraestructura(solo Front-End por el momento)](https://i.imgur.com/ixRIjxn.png)

### Propósito y Escalabilidad:

El contenido actual en `/website` representa una **implementación mínima viable (MVP)** o una **muestra funcional** del sitio de la barbería. Su propósito es **validar el proceso de despliegue automatizado** a través de **Terraform** en **GCP**, demostrando la capacidad de servir contenido estático de manera eficiente. Esta estructura modular facilita futuras expansiones, permitiendo la integración de frameworks frontend más complejos, o la separación en un **microfrontend** si el proyecto lo requiere, sin impactar directamente la infraestructura definida en `/infra`.

### Propósito y Escalabilidad:

Se procedera a implementar un Backend en las proxima actualizaciones a fin de mostra un proyecto completo, proximo a actualizar en las siguientes semanas

![Imagen de infraestructura con Back End(aun en desarrollo)](https://i.imgur.com/oVmYeMa.png)

## 🔐 Seguridad

  

- Las credenciales de GCP se gestionan mediante la **variable de entorno** `GOOGLE_APPLICATION_CREDENTIALS`.

- El archivo `.json` de la cuenta de servicio **no se incluye en este repositorio**.

- `.gitignore` protege archivos sensibles como `*.json`, `.tfstate`, `.tfvars`.

  

## ✅ Cómo replicar esta infraestructura

  

### 1. Pre-requisitos

  

- Tener una cuenta en [Google Cloud Platform](https://cloud.google.com/)

- Instalar:

- [Terraform](https://developer.hashicorp.com/terraform/downloads)

- [Google Cloud CLI (gcloud)](https://cloud.google.com/sdk/docs/install)

  

### 2. Crear y descargar tus credenciales GCP

  

- Crea una cuenta de servicio con permisos de `Storage Admin`.

- Descarga el archivo `.json` de la clave.

- Establece la variable de entorno con la ruta del archivo:

#### En Windows (PowerShell):

```powershell
$env:GOOGLE_APPLICATION_CREDENTIALS="C:\ruta\a\tu-clave.json"

```

#### En Linux/MacOS:

```bash
export GOOGLE_APPLICATION_CREDENTIALS="/ruta/a/tu-clave.json"

```
## ✅ Inicializar y Desplegar la Arquitectura

Desde la carpeta `infra/`:

```bash
# 1. Inicializar Terraform
terraform init

# 2. Verificar los recursos a crear
terraform plan

# 3. Aplicar la infraestructura
terraform apply

```

## ✅ Verificación de la Infraestructura

Una vez que la infraestructura de tu sitio web estático haya sido desplegada exitosamente utilizando Terraform, podrás acceder a él a través de la siguiente URL:

```
https://storage.googleapis.com/NOMBRE_DEL_BUCKET/

```

**¡Importante!**

Asegúrate de reemplazar `NOMBRE_DEL_BUCKET` con el nombre exacto de tu bucket de Cloud Storage. Este es el nombre que definiste en tu archivo `terraform.tfvars` (por ejemplo, `bar