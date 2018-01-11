Storages
========

Cfgtree does not make any assumption of the way settings are stored, appart from the fact they are
all organized in a hierarchicla structure.

Some common storage format are provided out of the box by cfgtree, but developers can easily
implement their own configuration file format.

Single Json file
----------------

.. autoclass:: cfgtree.storages.json.JsonFileConfigStorage
    :members:
    :inherited-members:
    :undoc-members:
    :exclude-members: find_storage, get_bare_config_dict, save_bare_config_dict

Base class
----------

.. autoclass:: cfgtree.storages.ConfigBaseStorage
    :members:
    :inherited-members:
    :undoc-members:
