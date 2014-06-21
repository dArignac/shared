.. contents:: Table of Contents

This reusable app contains functionality I use across my projects. Feel free to use and expand.

The package is also on PyPI: `https://pypi.python.org/pypi/django-shared/ <https://pypi.python.org/pypi/django-shared/>`_

Module utils
------------

``function list_remove_duplicates(seq, idfun=None)``

Removes duplicates from a list. To preserve the list order, specify a function for the list ids as ``idfun``.

Management Commands
-------------------

``python manage.py settings <SOMESETTING>``

Print the given setting value using ``pprint``.


Template Tags
-------------

**copyrights**

contains

- ``copyright_years``
    - displays are year span from ``settings.COPYRIGHT_YEAR_START`` (default: 2012) until now, e.g. ``2012 - 2014``
