Model Recipes
=============

Anyconfig Model Recipe
----------------------

This is the easiest way of using cfgtree. Anyconfig abstract the loading of the configuration file,
handling a large variety of file format transparently.

Two variant are provided:

- ``AnyConfigModel``: that can read enviroment variables and configuration file
- ``AnyConfigCliModel``: that tries to parse the command line argument

.. autoclass:: cfgtree.models.anyconfig.AnyConfigModel
    :members:
    :inherited-members:


Base Model
----------

.. automodule:: cfgtree
    :members:
    :inherited-members:
    :undoc-members:
