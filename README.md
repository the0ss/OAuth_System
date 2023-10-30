# Microsoft Outlook OAuth System

### Setting up the Project(Windows)
-   Install Python
-   It is suggested to have a dedicated virtual environment for each Django project, and one way to manage a virtual environment is venv, which is included in Python.
    ```py -m venv env```
-   Enter in virutal environment
    ``env\Scripts\activate.bat``
-   Remember to install Djnago in your virtual environment
    ``(env) C:\Users\Your Name>py -m pip install Django``
-   Then, clone this repo into the env
    ``git clone 'repo_url'``
-   Install required apps
    ``pip install django-allauth``
    ``pip install django-crispy-forms``
    ``pip install crispy-bootstrap5``
-   Now you can run the server using
    ``python manage.py runserver``

### Already Included in code(Only for understanding)

-   For Django-allauth, refer [here](https://docs.allauth.org/en/latest/installation/quickstart.html), all the text to be added respectively.
-   And in settings.py
    ```
    INSTALLED_APPS = [
        ...,
        'crispy_forms',
        'crispy_bootstrap5',
    ]
    ```
-   And then at the bottom of the page of settings.py
    ```
    CRISPY_ALLOWED_TEMPLATE_PACKS = "bootstrap5"
    CRISPY_TEMPLATE_PACK = "bootstrap5"
    ```
-   For Outlook OAuth, used Microsoft Graph 
    ```
    INSTALLED_APPS = [
    ...
    'allauth.socialaccount.providers.microsoft',
    ...
    ]
    ```
    ```
    SOCIALACCOUNT_PROVIDERS = {
    "microsoft": {
        'AUTH_PARAM':{'prompt':'consent','display':'popup'},
        'SCOPE':['User.Read'],
        'AUTH_PARAM':{'prompt':'consent'},
        }
    }
    ```
-   For login and logout redirect in ``setting.py``
    ```
    LOGIN_REDIRECT_URL='home'
    ACCOUNT_LOGOUT_REDIRECT_URL='account_login'
    ```

### For OAuth to handle we have to Configure the Azure ADD Registered Application
-   Login to Microsoft Azure and create your own app.
-   Configure all the redirects and API permissions.