# react-django-app-example-notes

1. create env
```
python3 -m venv env
source env/bin/activate
```

2. install requirements
```
pip install -r requirements.txt
```

## backend

1. create empty django project "backend"
```
django-admin startproject backend
```

2. create empty app "api"
```
cd backend
python3 manage.py startapp api
```

3. add django settings
```
from datetime import timedelta
from dotenv import load_dotenv
import os

load_dotenv()

ALLOWED_HOSTS = ["*"]

REST_FRAMEWORK = {
    "DEFAULT_AUTHENTICATION_CLASSES": (
        "rest_framework_simplejwt.authentication.JWTAuthentication",
    ),
    "DEFAULT_PERMISSION_CLASSES": [
        "rest_framework.permissions.IsAuthenticated",
    ],
}

SIMPLE_JWT = {
    "ACCESS_TOKEN_LIFETIME": timedelta(minutes=30),
    "REFRESH_TOKEN_LIFETIME": timedelta(days=1),
}

INSTALLED_APPS = [
    ...,
    "api",
    "rest_framework",
    "corsheaders",
]

MIDDLEWARE = [
    ...,
    "corsheaders.middleware.CorsMiddleware",
]

CORS_ALLOW_ALL_ORIGINS = True
CORS_ALLOWS_CREDENTIALS = True
```

4. make migrations
```
python3 manage.py makemigrations
python manage.py migrate 
```

5. run application
```
python3 manage.py runserver
```

## frontend

1. create empty react project
```
npm create vite@latest frontend -- --template react
cd frontend
npm install
```

2. install some packages
```
npm install axios react-router-dom jwt-decode
```

3. run application
```
npm run dev
```
