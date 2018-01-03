# mz-django

# Para iniciar un proyecto en Django
	>> django-admin startproject "nombre del proyecto"

# Arrancar el servidor Django. Dentro de la carpeta que crea startproject
	>> python manage.py runserver 

# Creación de un proyecto
	
	1. Crear una carpeta para contener el proyecto
	2. Dentro de esta carpeta ejecutar:
		>> django-admin startproject 'nombre proyecto'

		Esto crea una estructura de carpetas:
			nombreProyecto
				manage.py
				nombreProyecto
					settings.py
					urls.py
					wsgi.py

		- La subcarpeta 'nombreProyecto' es el punto de entrada al sitio web
	    - settings.py: contiene todos los ajustes del sitio. Es donde registramos todas las aplicaciones que creamos,
	     			   la localización de nuestros ficheros estáticos, los detalles de configuración de la base de datos, etc.
	    - urls.py: define los mapeos url-vistas. A pesar de que éste podría contener todo el código del mapeo url, es más común
	    		   delegar algo del mapeo a las propias aplicaciones.
    	- wsgi.py: se usa para ayudar a la aplicación Django a comunicarse con el servidor web.
    	- El script manage.py se usa para crear aplicaciones, trabajar con bases de datos y empezar el desarrollo del servidor web.
	
# Creación de una aplicación

	>> python manage.py startapp 'nombre aplicación'
		
		Crea un directorio y lo rellena con ficheros:

			nombreProyecto
				manage.py
				nombreProyecto
				nombreAplicacion
					admin.py
					apps.py
					models.py
					tests.py
					views.py
					__init__.py
					migrations/

		- views.py: para las vistas
		- models.py: para los modelos
		- tests.py: para las pruebas
		- admin.py: para la configuración del sitio de administración
		- apps.py: para el registro de aplicaciones
		- migrations/ : contiene ficheros que permite actualizar la base de datos a medida que se modifican los modelos
		- __init__.py: fichero vacio para que reconozca la carpeta como un paquete python

# Registrar las aplicaciones:
	
	Se debe registrar la aplicación de forma que sea incluida cuando cualquiera de las herramientas se ejecute. Las aplicaciones
	se registran añadiendolas a la lista de INSTALLED_APPS en el archivo settings.py del proyecto, añadiendo una linea al final:

		INSTALLED_APPS = [
    		'django.contrib.admin',
    		'django.contrib.auth',
    		'django.contrib.contenttypes',
    		'django.contrib.sessions',
    		'django.contrib.messages',
    		'django.contrib.staticfiles',
    		'catalog.apps.CatalogConfig', 
    	]

	La nueva linea especifica el objeto de configuración de la aplicación (CatalogConfig) que se generó en:
	/locallibrary/catalog/apps.py cuando se creo la aplicación.

# Especificación de la base de datos

	En este punto se especifica la base de datos del proyecto. Esta se configura en settings.py. Para mas informacion: 
	https://docs.djangoproject.com/en/2.0/ref/settings/#databases
	

# Conectar el mappeador URL
	
	El sitio web se crea con un fichero mapeador de URLs (urls.py) en la carpeta del proyecto. Aunque puedes usar este fichero para
	gestionar todos tus mapeos URL, es más usual deferir los mapeos a su aplicación asociada.

# Ejecutar database migrations

	>> python manage.py makemigrations
	>> python manage.py migrate

	'makemigrations': crea (pero no aplica) las migraciones para todas las aplicaciones instaladas en su proyecto (también puede 
	especificar el nombre de la aplicación para ejecutar una migración para un solo proyecto). Esto le da la oportunidad de verificar
	el código de estas migraciones antes de que se apliquen: cuando es un experto en Django, puede optar por modificarlo ligeramente.

	'migrate': El comando migrate realmente aplica las migraciones a su base de datos (Django rastrea cuáles se han agregado a la base
	de datos actual).

	

