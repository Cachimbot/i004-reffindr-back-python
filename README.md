# 🏡 Reffindr Backend Python : API y ETL 

[![Python](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)  [![Flask](https://img.shields.io/badge/Flask-v2.0.3-orange)](https://flask.palletsprojects.com/)  [![AWS RDS](https://img.shields.io/badge/AWS-RDS-green)](https://aws.amazon.com/rds/)  


<div style="text-align: center; padding: 20px;">
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" style="margin: 10px;">
  <img src="https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white" alt="Postman" style="margin: 10px;">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" style="margin: 10px;">
  <img src="https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black" alt="Swagger" style="margin: 10px;">
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white" alt="GitHub Actions" style="margin: 10px;">
</div>


Este repositorio contiene los scripts y recursos creados por el equipo de **Data** para el proyecto **Reffindr**, enfocándose en la extracción, transformación y carga (ETL) de datos inmobiliarios, así como la creación de una API REST con Flask.

---

## 🌟 Funcionalidades Principales

- **Web scraping con Flask API**: Extrae datos de propiedades inmobiliarias desde [Argenprop](https://www.argenprop.com/).
- **ETL automatizado**: Procesa los datos extraídos desde la API, los transforma y los carga en una base de datos AWS RDS.
- **Modelo de datos**: Estructura optimizada y documentada en un diagrama de relación (ER Diagram).

---

## 📂 Estructura del Proyecto

```plaintext
i004-reffindr-back-python/
├── app.py                   # API desarrollada con Flask para scraping
├── etl.py                   # codigo del ETL
├── etl.ipynb                # Notebook de ETL: extracción, transformación y carga
├── functions/               # Funciones del ETL reutilizables
├── scrapper/                # Código específico para scraping
├── static/                  # Código de swagger para la API
├── Data_ficticia/           # Datos ficticios creado por IA para llenar el ERD
├── Dockerfile               # Configuración de Docker para contenedores
├── requirements.txt         # Dependencias necesarias para ejecutar el proyecto
├── ERD DIAGRAM ... .pdf     # Modelo de base de datos ERD
├── README.md                # Documentanción del repositorio 
└── compose.yaml             # Configuración de Docker Compose
```
---

## 🚀 Cómo Empezar

### 1️⃣ Clonar el Repositorio
Primero, clona este repositorio en tu máquina local:

```bash
git clone https://github.com/igrowker/i004-reffindr-back-python.git
cd i004-reffindr-back-python
```
---
### 2️⃣ Crear un Entorno Virtual
Crea y activa un entorno virtual para mantener las dependencias aisladas:
```plaintext
python -m venv .venv  # Crea el entorno virtual
.venv\Scripts\activate # Lo activa
```
--- 

### 3️⃣ Instalar Dependencias
Asegúrate de tener Python 3.9+ instalado. Luego, ejecuta:

```plaintext
pip install -r requirements.txt
```
--- 

### 4️⃣ 🖥️ Uso de la API
Ejecutar la API Localmente
Inicia el servidor Flask localmente con:

```plaintext
python app.py
```
## Endpoints Disponibles

Este proyecto expone los siguientes endpoints para interactuar con la API:

### `/swagger`
- **Método:** `GET`
- **Descripción:** Proporciona documentación interactiva generada automáticamente con [Swagger](https://swagger.io/) para explorar y probar la API.

### `/argenprop`
- **Método:** `GET`
- **Descripción:** Realiza scraping de propiedades en Argenprop basadas en los parámetros proporcionados.
- **Parámetros:**
  - `pais`: Especifica el país de las propiedades a obtener (por ejemplo, "argentina").
  - `limite`: Establece el número máximo de propiedades a obtener (por ejemplo, "10").
  
- **Ejemplo de solicitud:**
http://127.0.0.1:5000/argenprop?pais=argentina&limite=10 <---- Puedes usar postman para testear la API

Nota: Puedes utilizar estas plataformas para subir la API utilizando la imagen de Docker y este de forma online: [Render](https://render.com/), [Azure App Service](https://azure.microsoft.com/es-es) o [AWS](https://aws.amazon.com/es/) como se realizo en este proyecto.

--- 
## 🚀 Ejecución del ETL

### 🛠️ Proceso ETL (Extract, Transform, Load)

Este repositorio incluye un proceso ETL automatizado que realiza las siguientes tareas:

1. **Extracción**: Obtiene datos desde la API alojada en AWS.
2. **Transformación**: Procesa y limpia los datos utilizando el archivo `etl.py`.
3. **Carga**: Envía los datos transformados a una base de datos, utilizando credenciales almacenadas en variables de entorno.

### 🔑 Configurar Variables de Entorno

El proyecto utiliza una base de datos alojada en **AWS RDS** pero puedes configurar tu propia base de datos con tus credenciales. Para esto, asegúrate de definir las siguientes variables en un archivo `.env` . Ejemplo:

```plaintext
API_URL                   # Url de la API 
DB_USER=tu_usuario        # Usuario de la base de datos
DB_PASSWORD=tu_contraseña # Contraseña de la base de datos
DB_HOST=tu_host           # Dirección del host (ejemplo: localhost o una URL de RDS)
DB_NAME=tu_basededatos    # Nombre de tu base de datos
DB_SCHEMA=tu_esquema      # Nombre del esquema
```
--- 
## 🗂️ Modelo de Base de Datos
El archivo [ERD DIAGRAM REFFINDR TEAM DATA.pdf](https://github.com/igrowker/i004-reffindr-back-python/blob/develop/ERD%20DIAGRAM%20REFFINDR%20TEAM%20DATA.pdf) contiene el diseño del modelo relacional, incluye todas las tablas principales para enriquecer la base de datos.

---
## 🛠️ Tecnologías Utilizadas

- **Lenguaje:** Python
- **Framework API:** Flask
- **Base de Datos:** AWS RDS
- **Web Scraping:** BeautifulSoup, Requests
- **Manejo de Datos:** Numpy, Pandas
- **Libreria Python - Base de Datos:** SQLAlchemy, psycopg2-binary
- **Otros:** Flask-Swagger-UI para la documentación de la API
