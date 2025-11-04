# M7_AE6_Grupal: Plataforma de Gestión de Voluntarios y Eventos (Django CRUD)
Por Cristian Aranda, Alicia Contreras, Álvaro Ortega

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg?style=flat-square)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-4.x%2B-green.svg?style=flat-square)](https://www.djangoproject.com/)

## 📝 Descripción del Proyecto

Este repositorio contiene el desarrollo de una aplicación web construida con **Django**, cuyo objetivo principal es implementar un sistema **CRUD** (Crear, Leer, Actualizar y Eliminar) completo para la gestión de **Voluntarios** y **Eventos** de una organización sin fines de lucro.

La aplicación permite a la ONG registrar nuevos voluntarios, organizar y asignarles actividades a través de la administración de eventos comunitarios.

---

## 🎯 Contexto y Requerimientos

El proyecto fue desarrollado como ejercicio grupal para demostrar la comprensión e implementación de los siguientes conceptos clave de Django:

### Modelos Principales
El corazón de la base de datos se basa en dos entidades:
1.  **`Voluntario`**: Almacena la información de las personas registradas para colaborar.
2.  **`Evento`**: Almacena las actividades organizadas por la ONG.

### Funcionalidades y Requerimientos Específicos

| Requisito | Descripción |
| :--- | :--- |
| **CRUD Completo** (Ej. 7, 8, 9) | Implementación de vistas y formularios para **Crear**, **Modificar** y **Eliminar** registros de `Voluntario` y `Evento`. |
| **Selección de Registros** (Ej. 6) | Vistas que utilizan el **Django ORM** (`.objects.all()`) para recuperar y listar todos los voluntarios y eventos. |
| **Enrutamiento Dinámico** (Ej. 5) | Definición de rutas en `urls.py` que reciben parámetros (ID) para acciones específicas como la modificación y eliminación (`Voluntario.objects.get(id=id)`). |
| **Seguridad CSRF** (Ej. 3) | Inclusión obligatoria de `{% csrf_token %}` en todos los formularios para prevenir ataques de falsificación de peticiones en sitios cruzados. |
| **Administración** (Ej. 1) | Configuración de la aplicación y registro de los modelos en `admin.py` para facilitar la gestión inicial de datos. |

---

## 🚀 Tecnologías Utilizadas

* **Backend Framework:** Django
* **Lenguaje:** Python
* **Base de Datos:** SQLite (por defecto en Django, configurable a PostgreSQL/MySQL)
* **Frontend:** HTML, CSS y Jinja (Plantillas de Django)

---

## ⚙️ Instalación del Proyecto

Sigue estos pasos para configurar y ejecutar el proyecto localmente.

### 1. Clonar el Repositorio

```bash
git clone https://github.com/carandab/M7_AE6_Grupal.git
cd M7_AE6_Grupal
```

### 2. Crear y Activar Entorno Virtual
Se recomienda usar un entorno virtual para aislar las dependencias:

```bash
# Crear entorno virtual
python3 -m venv venv

# Activar entorno (Linux/macOS)
source venv/bin/activate

# Activar entorno (Windows)
.env\Scriptsctivate
```

### 3. Instalar Dependencias
Instala el framework Django:

```bash
pip install django
```

### 4. Configurar la Base de Datos
Ejecuta las migraciones para crear las tablas de los modelos Voluntario y Evento:

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Crear un Superusuario (Opcional, pero recomendado)
Necesario para acceder al panel de administración de Django (/admin):

```bash
python manage.py createsuperuser
```

### 6. Ejecutar el Servidor
Inicia el servidor de desarrollo local:

```bash
python manage.py runserver
```

La aplicación estará disponible en: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

---

## 🗺️ Rutas (URLs) Principales

Las rutas están definidas en `urls.py` de la aplicación principal, permitiendo el acceso a todas las funcionalidades del CRUD.  
Los parámetros dinámicos (`<int:pk>`) se utilizan para identificar registros específicos.

| Ruta (Path) | Nombre (name=) | Descripción | Funcionalidad CRUD |
| :--- | :--- | :--- | :--- |
| `/voluntarios/lista_voluntarios` | `lista_voluntarios` | Lista completa de voluntarios. | Read (Listado) |
| `/voluntarios/crear/` | `crear_voluntario` | Formulario para registrar un nuevo voluntario. | Create |
| `/voluntarios/<int:pk>/` | `detalle_voluntario` | Vista detallada de un voluntario específico. | Read (Detalle) |
| `/voluntarios/<int:pk>/actualizar/` | `actualizar_voluntario` | Formulario para editar la información del voluntario. | Update |
| `/voluntarios/<int:pk>/eliminar/` | `confirmar_eliminar_voluntario` | Vista de confirmación y eliminación del voluntario. | Delete |
| `/eventos/lista_eventos` | `lista_eventos` | Lista completa de eventos organizados. | Read (Listado) |
| `/eventos/crear/` | `crear_evento` | Formulario para programar un nuevo evento. | Create |
| `/eventos/<int:pk>/` | `detalle_evento` | Vista detallada de un evento específico. | Read (Detalle) |
| `/eventos/<int:pk>/actualizar/` | `actualizar_evento` | Formulario para editar la información del evento. | Update |
| `/eventos/<int:pk>/eliminar/` | `confirmar_eliminar_evento` | Vista de confirmación y eliminación del evento. | Delete |
| `/admin/` | `-` | Panel de administración de Django. | - |
