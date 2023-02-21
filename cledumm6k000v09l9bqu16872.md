# Django basics

Django is a popular open-source web framework written in Python. It follows the Model-View-Controller (MVC) architectural pattern and is designed to make web development faster and easier. With Django, you can quickly build complex web applications with little effort. In this article, we'll cover the basics of Django.

Installation To use Django, you first need to install it. The easiest way to do this is by using pip, the package installer for Python. Open a terminal and run the following command:

```bash
pip install django
```

This will install the latest stable version of Django. Once the installation is complete, you can verify that Django is installed by running the following command:

```bash
django-admin --version
```

This should display the version number of Django that you just installed.

Creating a Django Project Now that Django is installed, you can create a new project. A project in Django is a collection of settings, configurations, and apps that make up a web application. To create a new project, navigate to the directory where you want to store your project and run the following command:

```bash
django-admin startproject projectname
```

Replace `projectname` with the name of your project. This will create a new directory with the same name as your project, which contains the basic structure of a Django project.

```bash
codeprojectname/
    manage.py
    projectname/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```

The [`manage.py`](http://manage.py) file is a command-line utility that lets you interact with your Django project. The `projectname` directory contains the main settings file, [`settings.py`](http://settings.py), which includes the configuration for your project. The [`urls.py`](http://urls.py) file contains the URL patterns for your project, while the [`asgi.py`](http://asgi.py) and [`wsgi.py`](http://wsgi.py) files are used for running your project as a web application.

Creating a Django App In Django, an app is a self-contained module that provides a specific functionality within your project. To create a new app, navigate to your project directory and run the following command:

```bash
python manage.py startapp appname
```

Replace `appname` with the name of your app. This will create a new directory with the same name as your app, which contains the basic structure of a Django app.

```bash
appname/
    __init__.py
    admin.py
    apps.py
    models.py
    tests.py
    views.py
```

The [`models.py`](http://models.py) file is where you define the data models for your app, while the [`views.py`](http://views.py) file contains the logic for handling HTTP requests and rendering responses. The [`admin.py`](http://admin.py) file is used to customize the Django admin interface for your app, while the [`tests.py`](http://tests.py) file is used for testing your app.

Running the Development Server Now that you have created a project and an app, you can start the development server and see your app in action. To do this, navigate to your project directory and run the following command:

```bash
python manage.py runserver
```

This will start the development server on [`http://127.0.0.1:8000/`](http://127.0.0.1:8000/). You can open this URL in a web browser to see the default Django welcome page.

Conclusion In this article, we covered the basics of Django, including installation, creating a project and app, and running the development server. While this is just the beginning of what Django can do, it provides a solid foundation for building complex web applications. With the help of Django's powerful features and community-driven packages, you can quickly build robust web applications that meet your specific needs.