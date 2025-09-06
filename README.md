# Message Board (Tablero de Mensajes)

Este proyecto es una aplicación web desarrollada con Django que permite gestionar una lista de tareas. Incluye funcionalidades básicas para visualizar tareas almacenadas en una base de datos SQLite.

## Tabla de Contenidos
- [Descripción](#descripción)
- [Tecnologías](#tecnologías)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Instalación](#instalación)
- [Uso](#uso)
- [Modelos](#modelos)
- [Vistas y URLs](#vistas-y-urls)
- [Plantillas](#plantillas)
- [Migraciones](#migraciones)
- [Notas](#notas)

## Descripción
Esta aplicación permite visualizar una lista de tareas. Cada tarea tiene un título, una fecha de creación y una fecha de actualización. El objetivo es servir como base para un sistema de gestión de tareas o mensajes.

## Tecnologías
- Python 3
- Django 5.2.6
- Base de datos SQLite3 (por defecto)

## Estructura del Proyecto
```
django_base/         # Configuración principal del proyecto Django
    settings.py      # Configuración general
    urls.py          # Rutas principales
    ...
tasks/              # Aplicación principal de tareas
    models.py        # Definición del modelo Task
    views.py         # Vista basada en clase para listar tareas
    urls.py          # Rutas de la app tasks
    migrations/      # Migraciones de la base de datos
    ...
templates/
    tasks_list.html  # Plantilla para mostrar la lista de tareas
manage.py           # Script de gestión de Django
requirements.txt    # Dependencias del proyecto
```

## Instalación
1. **Clona el repositorio:**
   ```bash
   git clone <url-del-repositorio>
   cd message_board
   ```
2. **Crea un entorno virtual (opcional pero recomendado):**
   ```bash
   python -m venv venv
   .\venv\Scripts\activate
   ```
3. **Instala las dependencias:**
   ```bash
   pip install -r requirements.txt
   ```
4. **Aplica las migraciones:**
   ```bash
   python manage.py migrate
   ```
5. **Inicia el servidor de desarrollo:**
   ```bash
   python manage.py runserver
   ```
6. **Accede a la aplicación:**
   Abre tu navegador en [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

## Uso
- La página principal muestra la lista de tareas almacenadas en la base de datos.
- Puedes acceder al panel de administración en `/admin` para gestionar tareas si registras el modelo en `admin.py`.

## Modelos
El modelo principal es `Task`:
```python
class Task(models.Model):
    title = models.CharField(max_length=200)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```

## Vistas y URLs
- **Vista:** Se utiliza una vista basada en clase (`TaskListView`) para mostrar la lista de tareas.
- **URL principal:** La raíz del sitio (`/`) muestra la lista de tareas.

## Plantillas
La plantilla `tasks_list.html` muestra las tareas:
```html
<ul>
    {% for pendiente in task_list %}
        <li>{{ pendiente.title }} - Creada el {{ pendiente.created_at }}</li>
    {% endfor %}
</ul>
```

## Migraciones
Las migraciones iniciales ya están incluidas. Si modificas los modelos, ejecuta:
```bash
python manage.py makemigrations
python manage.py migrate
```

## Notas
- El proyecto está en modo desarrollo (`DEBUG=True`). No usar en producción sin los ajustes necesarios.
- Puedes extender la funcionalidad agregando formularios para crear, editar o eliminar tareas.
- Para acceder al panel de administración, crea un superusuario:
  ```bash
  python manage.py createsuperuser
  ```

---
Proyecto base para gestión de tareas con Django.
