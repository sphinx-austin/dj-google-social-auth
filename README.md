# Getting started

## How to set up Google authentication to Django project

Here, we are using the module; django-allauth

## Set up
1. Create your project
   ```sh
   django-admin startproject <projectname>
   ```
2. Create and activate virtual environment
   ```
   py -3 -m venv venv
   venv\Scripts\activate.bat
   ```
3. Intsall dependencies
   ```
   pip install django django-allauth
   ```

4. Inside the ```settings.py``` add the following
   
4.1 Inside installed APPS
   ```
   INSTALLED_APPS = [
    ...
    # The following apps are required:
    'django.contrib.auth',
    'django.contrib.messages',
    'django.contrib.sites',

    'allauth',
    'allauth.account',
    'allauth.socialaccount',
    # ... include the providers you want to enable:
   'allauth.socialaccount.providers.google'
   ```

4.2 Add site ID below ```INSTALLED_APPS```
   ```
   # add site ID
   SITE_ID = 1
   ```

4.3 Inside ```urls.py``` add:
   ```
   urlpatterns = [
       ...
       path('accounts/', include('allauth.urls')),
       ...
   ]
   ```

5. Run:
   ```
   python manage.py migrate
   ```
6. Create super user:
   ```
   python manage.py createsuperuser
   ```
7. Navigate to ```http://localhost:8000/admin``` 
