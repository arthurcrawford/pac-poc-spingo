
Initially the directory structure looks like this::

    ├── README.rst
    ├── build.sh
    ├── greeter
    │   ├── __init__.py
    │   └── hello.py
    └── setup.py

The following then creates a source distribution::

    python setup.py sdist

Following which the directory structure looks like this::

    ├── README.rst
    ├── build.sh
    ├── dist                     << Source dist
    │   └── greeter-1.0.tar.gz
    ├── greeter
    │   ├── __init__.py
    │   └── hello.py
    ├── greeter.egg-info         << Egg info
    │   ├── PKG-INFO
    │   ├── SOURCES.txt
    │   ├── dependency_links.txt
    │   ├── not-zip-safe
    │   └── top_level.txt
    └── setup.py

And the command below will install the built distribution directly from the dist directory without referring to PyPI::

    pip install --no-index --find-links=./dist greeter
