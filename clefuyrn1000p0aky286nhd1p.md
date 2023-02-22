# How to add a custom widget to django-jet admin panel with custom dashboard?

here's a step-by-step tutorial for adding a custom widget to the Django-jet admin panel with a custom dashboard:

1. First, make sure that you have installed the Django-jet library by running `pip install django-jet`.
    
2. Next, create a Django app by running `python` [`manage.py`](http://manage.py) `startapp myapp`.
    
3. In the [`settings.py`](http://settings.py) file of your Django project, add 'jet' and 'jet.dashboard' to `INSTALLED_APPS`:
    

```python
INSTALLED_APPS = [
    # other apps
    'jet',
    'jet.dashboard',
    'myapp',
]
```

1. In the same file, add the following configuration for Django-jet:
    

```python
JET_INDEX_DASHBOARD = 'myapp.dashboard.CustomIndexDashboard'
```

This configures Django-jet to use a custom dashboard for the index page.

1. In the `myapp` directory, create a new file called [`dashboard.py`](http://dashboard.py). This file will define the custom dashboard class.
    
2. Define a custom dashboard class that inherits from `jet.dashboard.modules.Dashboard`. This class will be responsible for defining the layout and contents of the dashboard.
    

```python
from jet.dashboard.modules import Dashboard

class CustomIndexDashboard(Dashboard):
    pass
```

At this point, you should be able to see the custom dashboard when you log in to the Django admin panel.

1. To add a custom widget to the dashboard, define a widget class that inherits from `jet.dashboard.modules.Widget`:
    

```python
from jet.dashboard.modules import Widget

class CustomWidget(Widget):
    title = 'My Custom Widget'
    template = 'myapp/dashboard/custom_widget.html'
```

In this example, the widget class is named `CustomWidget`, and it has a `title` attribute that specifies the widget title, and a `template` attribute that specifies the path to the widget's template.

1. Create a new directory called `templates` inside the `myapp` directory.
    
2. Inside the `templates` directory, create a new directory called `myapp`, and inside that directory, create a new file called `custom_widget.html`. This file will define the HTML and JavaScript for the custom widget.
    

```xml
<div id="{{ widget_id }}">
    <h2>{{ widget.title }}</h2>
    <p>Here is some custom content for the widget!</p>
</div>
<script>
    $(function() {
        // Custom widget logic goes here.
    });
</script>
```

In this example, the template contains some basic HTML and JavaScript for the widget.

1. Back in the [`dashboard.py`](http://dashboard.py) file, add the custom widget to the custom dashboard:
    

```python
from jet.dashboard.modules import Dashboard
from myapp.dashboard.widgets import CustomWidget

class CustomIndexDashboard(Dashboard):
    widgets = [
        CustomWidget(
            draggable=True,
            collapsible=True,
            deletable=True,
            title='My Custom Widget',
        ),
    ]
```

In this example, the `CustomWidget` is added to the `widgets` list of the `CustomIndexDashboard` class. The `draggable`, `collapsible`, and `deletable` attributes are set to `True` to allow the user to move, collapse, and delete the widget.

That's it! Now, when you log in to the Django admin panel, you should see the custom widget on the custom dashboard. You can modify the widget's HTML and JavaScript in the `custom_widget.html` file, and you can customize the widget's behavior by modifying the `CustomWidget` class in the [`widgets.py`](http://widgets.py) file.