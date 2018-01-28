Model
=====

The core part of cfgtree is the definition of the model. A "model" is a Python dictionary that
describes the hierarchical organization of your settings, like JSON Schema.

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

Various setting types are provided, covering most of the data types to be stored in configuration a
file.

For example, ``StringCfg`` descrive a string value, ``IntCfg`` any integer, ``BoolCfg`` a boolean
and so on.

Each type has the same base arguments, such as:

- ``summary``: human readable short description
- ``description``: human readable long and exhauxtive description
- ``short_param``: which short command line argument to expose (ex: ``-c``)
- ``long_param``: which long command line argument to expose (ex: ``--config-file``)

Here an example of a complex model:

.. code-block:: Python

    {
        "configfile": ConfigFileCfg(
            default_filename=config,
            long_param="--config-file",
            summary="Config file"),
        "version": ConfigVersionCfg(),
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
            "list_opt": ListOfStringCfg(
                short_param='-l',
                long_param="--list-opt",
                summary='Help msg lst'),
            "dict_opt": {
                "key1": StringCfg(summary='Help msg string'),
                "key2": StringCfg(summary='Help msg string'),
            }
        }
    }

This model matches a configuration JSON file such as:

.. code-block:: javascript

    {
        "version": 1,
        "group1": {
            "string_opt": "a string",
            "int_opt": 123,
            "float_opt": 2.0,
            "bool_opt": true,
            "list_opt": [
                "a",
                "b",
                "c"
            ],
            "dict_opt": {
                "key1": "val1",
                "key2": "val2"
            }
        }
    }

Or this TOML file:

.. code-block:: ini

    version = 1

    [group1]
    string_opt = "a string"
    int_opt = 123
    float_opt = 2.0
    bool_opt = true
    list_opt = [ "a", "b", "c",]

    [group1.dict_opt]
    key1 = "val1"
    key2 = "val2"
