# How to add a custom widget to django-jet admin panel with custom dashboard?

here's a step-by-step tutorial for adding a custom widget named `TotalOrders` to the Django-jet admin panel with a custom dashboard:

1. First, make sure that you have installed the Django-jet library by running `pip install django-jet`.
    
2. Next, create a Django app by running `python` [`manage.py`](http://manage.py) `startapp myapp`.
    
3. In the [`settings.py`](http://settings.py) file of your Django project, add 'jet' and 'jet. dashboard' to `INSTALLED_APPS`:
    

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
    
2. Define a custom dashboard class that inherits from `jet.dashboard.dashboard`. This class will be responsible for defining the layout and contents of the dashboard.
    

```python
from jet.dashboard.dashboard import Dashboard

class CustomIndexDashboard(Dashboard):
    pass
```

At this point, you should be able to see the custom dashboard when you log in to the Django admin panel.

1. To add a custom widget to the dashboard, define a widget class `TotalOrdersWidget` that inherits from `jet.dashboard.modules`:
    

```python
from jet.dashboard.modules import DashboardModule
from myapp.models import Order
from django.template.loader import render_to_string


class TotalOrdersWidget(DashboardModule):
    title = 'Total Orders'

    def render(self, request=None):
        total_orders = Order.objects.filter(ordered=True).count()
        context = {
            'total_orders': total_orders,
        }
        return render_to_string('widget/total_orders.html', context)
```

In this example, the widget class is named `TotalOrdersWidget`, and it has a `title` attribute that specifies the widget title, and a `template` attribute that specifies the path to the widget's template.

1. Create a new directory called `templates` inside the `myapp` directory.
    
    1. Inside the `templates` directory, create a new directory called `widget`, and inside that directory, create a new file called `total_orders.html`. This file will define the HTML and JavaScript for the custom widget.
        

```xml

<center><h1 style="margin:10px">{{ total_orders }}</h1></center>
```

In this example, the template contains some basic HTML and JavaScript for the widget.

1. Back in the [`dashboard.py`](http://dashboard.py) file, add the custom widget `TotalOrdersWidget`to the custom dashboard:
    

```python
from django.utils.translation import ugettext_lazy as _
from jet.dashboard import modules
from jet.dashboard.dashboard import Dashboard
from jet.dashboard.modules import ModelList, AppList, RecentActions

from myapp.widgets import TotalOrdersWidget


class CustomDashboard(Dashboard):
    """
    Custom dashboard for the Django Jet admin interface.
    """
    columns = 3

    def init_with_context(self, context):
        """
        Initialize the dashboard with the context.
        """
        self.available_children.append(TotalOrdersWidget)
        self.available_children.append(modules.LinkList)
        self.available_children.append(AppList)
        self.available_children.append(ModelList)
        self.available_children.append(RecentActions)

        self.children.append(TotalOrdersWidget("Total Orders"))
        self.children.append(AppList("Applications"))
        self.children.append(RecentActions("Recent Actions"))
        self.children.append(ModelList("Model List"))

        self.children.append(modules.LinkList(
            _('Support'),
            children=[
                {
                    'title': _('Django documentation'),
                    'url': 'http://docs.djangoproject.com/',
                    'external': True,
                },
                {
                    'title': _('Django "django-users" mailing list'),
                    'url': 'http://groups.google.com/group/django-users',
                    'external': True,
                },
                {
                    'title': _('Django irc channel'),
                    'url': 'irc://irc.freenode.net/django',
                    'external': True,
                },
            ],
            column=0,
            order=0
        ))
```

In this example, the `TotalOrdersWidget` is added to the `widgets` list of the `CustomIndexDashboard` class. The `draggable`, `collapsible`, and `deletable` attributes are set to `True` to allow the user to move, collapse, and delete the widget.

`ModelList`, `AppList`,`RecentActions` these modules are some predefined modules that I wanted to add to my customIndexDashboard which I imported from the class `jet.dashboard.modules`.

That's it! Now, when you log in to the Django admin panel, you should see the custom widget on the custom dashboard. You can modify the widget's HTML and JavaScript in the `total_orders.html` file, and you can customize the widget's behavior by modifying the `TotalOrdersWidget` class in the [`widgets.py`](http://widgets.py) file.

After all this our admin panel will something like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677434636059/16da23f3-837c-4459-b032-aada47784002.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677434678294/3a1fd656-36d3-4c50-9026-b24a139a0874.png align="center")