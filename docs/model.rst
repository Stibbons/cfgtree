Model
=====

The configuration tree model is a Python dictionary that describes the hierarchical organization of
your settings.

For example, if I want to organize my settings into two groups, one "general" and one "others",
I would place the descriptions in a model such as:

.. code-block:: Python

    model = {
        "general" {
            # ...
        },
        "others": {
            # ...
        },
    }
