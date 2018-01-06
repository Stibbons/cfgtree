===============================
cfgtree
===============================

.. image:: https://travis-ci.org/Stibbons/cfgtree.svg?branch=master
    :target: https://travis-ci.org/Stibbons/cfgtree
.. image:: https://readthedocs.org/projects/cfgtree/badge/?version=latest
   :target: http://cfgtree.readthedocs.io/en/latest/?badge=latest
   :alt: Documentation Status
.. image:: https://coveralls.io/repos/github/Stibbons/cfgtree/badge.svg
   :target: https://coveralls.io/github/Stibbons/cfgtree
.. image:: https://badge.fury.io/py/cfgtree.svg
   :target: https://pypi.python.org/pypi/cfgtree/
   :alt: Pypi package
.. image:: https://img.shields.io/badge/license-MIT-blue.svg
   :target: ./LICENSE
   :alt: MIT licensed

Automatic configuration file, command line, environment variable parser

* Free software: MIT
* Documentation: https://cfgtree.readthedocs.org/en/latest/
* Source: https://github.com/Stibbons/cfgtree

Features
--------

* TODO

Usage
-----

* TODO


Note: See `pipenv documentation <https://github.com/kennethreitz/pipenv>`_ for Pipfile
specification.

Contributing
------------

Setup for development:

    .. code-block:: bash

        $ make dev

Activate the virtualenv:

    .. code-block:: bash

        $ make shell  # equivalent to `pipenv shell`

Execute unit tests:

    .. code-block:: bash

        $ make test-unit


Build source package:

    Use it for most package without low level system dependencies.

    .. code-block:: bash

        make sdist

Build binary package:

    Needed for package with a C or other low level source code.

    .. code-block:: bash

        make bdist

Build Wheel package:

    Always provide a wheel package.

    .. code-block:: bash

        make wheel

To register Pipy deployment:

- commit your work!
- enable your project on Travis
- execute ``pipenv run python travis_pypi_setup.py``
- the ``.travis.yml`` is rewritten, you may want to restore its formatting.

Create a release:

    .. code-block:: bash

        make release
        git tag 1.2.3
        make push

On successful travis build on the Tag branch, your Pypi package will be updated automatically.

Configuration
-------------

You will need to configure `.travis.yml` to enable automatic PyPi deployment, or use the provided
`travis_pypi_setup.py` script. Beware your Yaml file will be overwritten, you will have to set the
format back manually.
