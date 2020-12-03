django-pymemcache
=================

.. image:: https://travis-ci.org/django-pymemcache/django-pymemcache.svg?branch=master
   :target: https://travis-ci.org/django-pymemcache/django-pymemcache
.. image:: https://codecov.io/gh/django-pymemcache/django-pymemcache/branch/master/graph/badge.svg
   :target: https://codecov.io/gh/django-pymemcache/django-pymemcache
.. image:: https://img.shields.io/pypi/v/django-pymemcache.svg?style=flat
   :target: https://pypi.org/project/django-pymemcache/
.. image:: https://img.shields.io/pypi/djversions/django-pymemcache.svg?style=flat
.. image:: https://img.shields.io/pypi/pyversions/django-pymemcache.svg?style=flat

django-pymemcache is a Django cache backend that uses Pinterest's
pymemcache_ library as the backend.

Built-in Backend
----------------

**If you are using Django 3.2 please use the built-in backend instead.**

It is available at ``django.core.cache.backends.memcached.PyMemcacheCache``.

Note that there are a few differences to the implementation provided here. The
built-in backend passes some configuration options to the ``pymemcache`` client
by default, specifically ``allow_unicode_keys`` is set to ``True`` and
``default_noreply`` is set to ``False``. This is to ensure consistency with
other backends and expected behavior in Django's cache framework.

If you rely on the default behavior of this implementation, make sure you
adjust your configuration as required when migrating to the built-in backend.

Installation
------------

::

    pip install django-pymemcache

Usage
-----

Simply use it as any other `Cache backend <https://docs.djangoproject.com/en/stable/topics/cache/>`_, e.g.

.. code-block:: python

    CACHES = {
        'default': {
            'BACKEND': 'djpymemcache.backend.PyMemcacheCache',
            'LOCATION': [
               '127.0.0.1:11211',
            ],
            'OPTIONS': {
                'serializer': <your_serializer>,
                'deserializer': <your_deserializer>,
            },
        },
    }

Issues
------

    https://github.com/django-pymemcache/django-pymemcache/issues

.. _pymemcache: https://github.com/pinterest/pymemcache
