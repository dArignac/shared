django-shared
=============

|Downloads| |Version| |Wheel| |Egg| |Format| |License|

.. |Downloads| image:: https://img.shields.io/pypi/dm/django-shared.svg
    :target: https://pypi.python.org/pypi/django-shared/
    :alt: Downloads
.. |Version| image:: https://img.shields.io/pypi/v/django-shared.svg
    :target: https://pypi.python.org/pypi/django-shared/
    :alt: Latest Version
.. |Wheel| image:: https://img.shields.io/pypi/wheel/django-shared.svg
    :target: https://pypi.python.org/pypi/django-shared/
    :alt: Wheel Status
.. |Egg| image:: https://pypip.in/egg/django-shared/badge.png
    :target: https://pypi.python.org/pypi/django-shared/
    :alt: Egg Status
.. |Format| image:: https://img.shields.io/pypi/format/django-shared.svg
    :target: https://pypi.python.org/pypi/django-shared/
    :alt: Download format
.. |License| image:: https://img.shields.io/pypi/l/django-shared.svg
    :target: https://pypi.python.org/pypi/django-shared/
    :alt: License

.. contents:: Table of Contents

This reusable app contains functionality I use across my projects. Feel free to use and expand.

The package is also on PyPI: `https://pypi.python.org/pypi/django-shared/ <https://pypi.python.org/pypi/django-shared/>`_

Changelog
---------

* 0.0.1
    * initial release

Usage
-----

Add to your ``INSTALLED_APPS`` setting:

.. code-block:: python

    INSTALLED_APPS = [
        ...
        'shared',
    ]


Contents
--------

Utils for django-configurations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``shared.configurations.ExternalCredentials``

Mixin for a Configuration class of django-configurations. Enables one to load specific variables from <myproject>/configs/<DJANGO_CONFIGURATION>.py.
Good to separate critical information from the settings itself. *Usually you do not check the configs into your code versioning system!*

Usage example:

.. code-block:: python

    # in settings.py (following the default django-configurations setup)
    class Common(Configurations):
        DATABASES = {
            'default': ExternalCredentials.get_credentials_module().DATABASE,
        }
    
    # in <myproject>/configs/<DJANGO_CONFIGURATION>.py; e.g. sampleproject/configs/Dev.py
    DATABASE = {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'db_name',
        'USER': 'db_user',
        'PASSWORD': 'db_password',
    }


Module utils
~~~~~~~~~~~~

``function list_remove_duplicates(seq, idfun=None)``

Removes duplicates from a list. To preserve the list order, specify a function for the list ids as ``idfun``.

Management Commands
~~~~~~~~~~~~~~~~~~~

``python manage.py settings <SOMESETTING>``

Print the given setting value using ``pprint``.


Template Tags
~~~~~~~~~~~~~

**copyrights**

contains

- ``copyright_years``
    - displays are year span from ``settings.COPYRIGHT_YEAR_START`` (default: 2012) until now, e.g. ``2012 - 2014``
