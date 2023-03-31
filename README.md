# Python Starter
A template for django apps with dev containers and docker compoase

## Setup
1. Copy `.env.template` to `.env` and update any setting you choose. If you do change those `.env` values, make sure the `.vscode/settings.json` is also updated.

**Notice:** The `.env` file is ignored by git. 

2. Reload the folder in a container. 
3. If there is no bash terminal, you can add one by clicking the `+` button. Then run the *django-admin start project* command. You can replace `app` with your project name if you choose
```bash
    django-admin startproject app 
```
4. In `app/settings.py` (replace app with your project name), update the DATABASES property to the following:
```python

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ.get('POSTGRES_NAME'),
        'USER': os.environ.get('POSTGRES_USER'),
        'PASSWORD': os.environ.get('POSTGRES_PASSWORD'),
        'HOST': os.environ.get('POSTGRES_HOST'),
        'PORT': 5432,
    }
}
``` 
5. Also in `app/settings.py`, update the `ALLOWED_HOTS` property to: 
```python
ALLOWED_HOSTS = os.environ.get('DJANGO_ALLOWED_HOSTS').split(' ')
```
5. Un comment the following line in the `.devcontainer/devcontainer.json` file, if you want the server to start automatically when the devcontainer is built.
```
	//"postCreateCommand": "python manage.py runserver 0.0.0.0:8000"
```
