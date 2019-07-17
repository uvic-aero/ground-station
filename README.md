# Ground Station
HTTP Server to store and serve data collected in flight. 

## Install
```sh
pip3 install Django
```

## Running Server
From the project root dir
```sh
python3 manage.py runserver
```

## Creating a New Application
1. Create the application directory
```sh
django-admin startapp [newappname]
```
2. Create views for application 
```python
# newappname/views.py

from django.shortcuts import render
from django.http import HttpResponse

# Create your views here.
def index(response):
    return HttpResponse("Hello, world. You're at the newapp index.")
```
3. Create url endpoints for new views 
```python
# newappname/urls.py
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```
4. Import url's into project 
```python
# groundstation/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('newappname/', include('newappname.urls')),    
]
```

