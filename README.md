# Tienda de Videojuegos Django

Proyecto de e-commerce para tienda de videojuegos desarrollado con Django 5.2.9

## Requisitos Previos

- Python 3.10 o superior
- pip (gestor de paquetes de Python)
- virtualenv (recomendado) o venv
- Git (opcional)

## Instalación

### 1. Clonar el Repositorio (si aplica)

```bash
git clone <url-del-repositorio>
cd Tienda_Videojuegos
```

### 2. Crear y Activar Entorno Virtual

**Windows (Git Bash/PowerShell):**

```bash
# Crear entorno virtual
python -m venv venv

# Activar entorno virtual
venv\Scripts\activate
```

**Linux/Mac:**

```bash
# Crear entorno virtual
python3 -m venv venv

# Activar entorno virtual
source venv/bin/activate
```

**Alternativa con virtualenvwrapper (Windows):**

```bash
# Crear entorno virtual
mkvirtualenv dj_gamestore

# Activar (si ya existe)
workon dj_gamestore
```

### 3. Instalar Dependencias

```bash
pip install -r requirements.txt
```

**Nota:** Si estás usando virtualenvwrapper, asegúrate de que el entorno esté activado antes de instalar las dependencias.

### 4. Migraciones de Base de Datos

El servidor te avisará si hay migraciones pendientes. Para aplicarlas:

```bash
python manage.py migrate
```

### 5. Crear Superusuario (Opcional)

Si deseas acceder al panel de administración de Django:

```bash
python manage.py createsuperuser
```

Sigue las instrucciones para crear tu usuario y contraseña.

### 6. Ejecutar el Servidor de Desarrollo

```bash
python manage.py runserver
```

El servidor estará disponible en: **http://127.0.0.1:8000/**

## Estructura del Proyecto

```
Tienda_Videojuegos/
├── tienda_videojuegos/          # Directorio principal del proyecto
│   ├── settings.py              # Configuración del proyecto
│   ├── urls.py                  # URLs principales
│   └── wsgi.py                  # Configuración WSGI
├── catalogo/                     # App de catálogo de productos
│   ├── models.py                # Modelos de datos
│   ├── views.py                 # Vistas
│   ├── urls.py                  # URLs de catálogo
│   └── templates/               # Plantillas específicas
├── home/                         # App de página principal
│   ├── views.py                 # Vistas principales
│   ├── urls.py                  # URLs de home
│   └── templates/               # Plantillas de home
├── static/                       # Archivos estáticos (CSS, JS, imágenes)
│   ├── css/
│   │   └── style.css
│   └── js/
│       └── script.js
├── templates/                    # Plantillas globales
│   └── base.html                # Plantilla base
├── db.sqlite3                    # Base de datos SQLite (por defecto)
├── manage.py                     # Script de gestión de Django
├── requirements.txt              # Dependencias del proyecto
└── README.md                     # Este archivo
```

## Aplicaciones Incluidas

- **home**: Página principal de la tienda
- **catalogo**: Gestión y visualización de catálogo de videojuegos
- **admin**: Panel de administración de Django

## Comandos Útiles

```bash
# Ejecutar servidor de desarrollo
python manage.py runserver

# Aplicar migraciones
python manage.py migrate

# Crear nuevas migraciones después de cambiar modelos
python manage.py makemigrations

# Recolectar archivos estáticos (para producción)
python manage.py collectstatic

# Crear superusuario
python manage.py createsuperuser

# Abrir shell de Django
python manage.py shell

# Verificar proyectos
python manage.py check
```

## Configuración

### Base de Datos

Por defecto, el proyecto usa SQLite. Para cambiar a PostgreSQL o MySQL:

Edita `tienda_videojuegos/settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',  # o mysql
        'NAME': 'nombre_db',
        'USER': 'usuario',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### Variables de Entorno (Recomendado para Producción)

Crea un archivo `.env` en la raíz del proyecto:

```env
SECRET_KEY=tu-clave-secreta-aqui
DEBUG=False
ALLOWED_HOSTS=tu-dominio.com
DATABASE_URL=postgresql://usuario:password@localhost:5432/nombre_db
```

## Solución de Problemas

### Error: "No module named 'django'"

Asegúrate de haber activado el entorno virtual e instalado las dependencias:

```bash
workon dj_gamestore  # o source venv/bin/activate
pip install -r requirements.txt
```

### Migraciones No Aplicadas

Si ves el mensaje "You have X unapplied migration(s)", ejecuta:

```bash
python manage.py migrate
```

### Puerto 8000 en Uso

Usa un puerto diferente:

```bash
python manage.py runserver 8001
```

## Deploy en Producción

**IMPORTANTE:** Este servidor de desarrollo NO es adecuado para producción.

Para producción, usa:

- **Gunicorn** + **Nginx** (Linux)
- **Waitress** (Windows)
- **uWSGI**

Consulte la [documentación oficial de Django sobre deployment](https://docs.djangoproject.com/en/5.2/howto/deployment/)

## Recursos

- [Documentación de Django 5.2](https://docs.djangoproject.com/en/5.2/)
- [Tutorial de Django](https://docs.djangoproject.com/en/5.2/intro/tutorial01/)
- [Django Girls Tutorial](https://tutorial.djangogirls.org/)

## Notas

- El proyecto usa SQLite por defecto, ideal para desarrollo
- Para producción, usar PostgreSQL o MySQL
- Configurar `DEBUG=False` y `ALLOWED_HOSTS` en producción
- Nunca compartir el `SECRET_KEY` en repositorios públicos

## Autor

DairXP

## Licencia

Este proyecto está bajo la Licencia MIT
