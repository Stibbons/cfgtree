
Overview
========

Configuration Tree Description
------------------------------

Configuration hierarchy is to be described in a ``cfgtree.ConfigBaseModel`` inherited instance,
inside the member ``.model``, using helper classes such as ``StringCfg``, ``IntCfg``, ``IPCfg``
or ``PasswordCfg``. Each setting can be set by environment variable, command line parameter or by
the storage file(s) itself.

Let's take an example of an item defined at the first level of the hierarchy. It is defined as a
``IntCfg`` with name ``count``. User can set this setting by:

- environment variable ``APPLICATIONNAME_COUNT`` (where ``APPLICATIONNAME`` is an optional,
  developer-defined prefix added to every environment variable of the application to avoid
  conflicts)
- command line argument ``--count``
- item `count` at the first level of a json file

Hierarchical structure is reflected in these different ways, to avoid conflicts. Now, let's imagine
the 'count' setting is set in a group called 'general':

- environment variable is: ``APPLICATIONNAME_GENERAL_COUNT``
- command line argument is: ``--general-count``
- Json has a first level named ``general``, and inside one of the items is called ``count``:

  .. code-block:: javascript

      {
          "general": {
              "count": 1
          }
      }

Configuration Storage
---------------------

The trivial storage is a simple json file. The complete settings are placed inside it, such as:

.. code-block:: javascript

    {
        "group1": {
            "string_opt": "a string",
            "int_opt": 123,
            "float_opt": 2.0,
            "bool_opt": true
        }
    }

cfgtree allows complete customization of the file storage, developers can even develop their own.

Current Support:

- single Json file
- Anyconfig supported file type (yaml, toml, json,...)

Future support:

- Multiple file example
- Configuration server

Access to settings
------------------

In your application, an xpath-like syntax allows you to reach any item of the configuration, using a
xpath-like syntax ``<key1>.<key2>.<key3>.<item>``, for example:

.. code-block:: python

    cfg = AnyConfigModel(model={
        "group1": {
            "string_opt": StringCfg(
                short_param='-s',
                long_param="--string-opt",
                summary='Help msg string'),
            "int_opt": IntCfg(
                short_param='-i',
                long_param="--int-opt",
                summary='Help msg int'),
            "float_opt": FloatCfg(
                short_param='-f',
                long_param="--float-opt",
                summary='Help msg float'),
            "bool_opt": BoolCfg(
                short_param='-b',
                long_param="--bool-opt",
                summary='Help msg bool'),
    })

Setting values can be done by:

.. code-block:: python

    cfg.set_cfg_value("group1.float_opt", 2.0)
