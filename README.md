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
7. Navigate to ```http://localhost:8000/admin```, and login using the creadentials created in the previous step. Under SOCIAL ACCOUNTS, ADD new social application. Select Google as the provider. Input dummy secret key and Id, and select example.com as the sites. The SAVE.

8. At the SITES, edit the existing site domain name to 'site name' for your demo account.

9. Go to ```https://console.cloud.google.com/apis/dashboard``` create GMAIL APIS. Create Credentials. Create URIs and copy&paste the CLIENT ID and SECRET KEY to the django admin, under the SOCIAL APPLICATION created in step 7 above.

- NOTE: Authorized redirect URIs is ```http://127.0.0.1:8000/accounts/google/login/callback/```

10. To test your authentication, logout as admin, and try signing in using Google.
