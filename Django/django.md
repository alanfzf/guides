# Configure a project

## Initialize the project

```bash
# create the base project
django-admin startproject <name> .
```

```bash
# create an app
django-admin startapp app
```

## Configure the base app
We go to the `startproject` folder and we head to the `settings.py` file

```python
# BELOW THIS LINE WE ADD THE FOLLOWING
BASE_DIR = Path(__file__).resolve().parent.parent
# This lines makes the templates folder, available thought the whole project
TEMPLATES_DIR = os.path.join(BASE_DIR, 'templates')

# In the templates section we add the TEMPLATES_DIR variable
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [TEMPLATES_DIR] # HERE ....
    }
]

```

```python
# WE ADD THIS SO WE CAN CONNECT FROM ANYWHERE
ALLOWED_HOSTS = ['*']
```

```python
# Configure the static files directory, we need to add it below this
STATIC_URL = 'static/'

STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "static"),
]
```

# Add essential plugins

## Django widget tweaks

```bash
# install django-widget-tweaks
pip install django-widget-tweaks
```
```python
# we then go to app settings.py and add the following string
INSTALLED_APPS += [
    'widget_tweaks',
]
```


# Documentation

## Types of class based views
- ListView (Display all items of certain model)
- DetailView (Display details of certain model)
