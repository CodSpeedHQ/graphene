|Graphene Logo| `Graphene <http://graphene-python.org>`__ |Build Status| |PyPI version| |Coverage Status|
=========================================================================================================

`💬 Join the community on
Slack <https://join.slack.com/t/graphenetools/shared_invite/enQtOTE2MDQ1NTg4MDM1LTA4Nzk0MGU0NGEwNzUxZGNjNDQ4ZjAwNDJjMjY0OGE1ZDgxZTg4YjM2ZTc4MjE2ZTAzZjE2ZThhZTQzZTkyMmM>`__

**We are looking for contributors**! Please check the
`ROADMAP <https://github.com/graphql-python/graphene/blob/master/ROADMAP.md>`__
to see how you can help ❤️

Introduction
------------

`Graphene <http://graphene-python.org>`__ is an opinionated Python
library for building GraphQL schemas/types fast and easily.

-  **Easy to use:** Graphene helps you use GraphQL in Python without
   effort.
-  **Relay:** Graphene has builtin support for Relay.
-  **Data agnostic:** Graphene supports any kind of data source: SQL
   (Django, SQLAlchemy), NoSQL, custom Python objects, etc. We believe
   that by providing a complete API you could plug Graphene anywhere
   your data lives and make your data available through GraphQL.

Integrations
------------

Graphene has multiple integrations with different frameworks:

+-------------------+-------------------------------------------------+
| integration       | Package                                         |
+===================+=================================================+
| Django            | `graphene-django <https:/                       |
|                   | /github.com/graphql-python/graphene-django/>`__ |
+-------------------+-------------------------------------------------+
| SQLAlchemy        | `graphene-sqlalchemy <https://git               |
|                   | hub.com/graphql-python/graphene-sqlalchemy/>`__ |
+-------------------+-------------------------------------------------+

Also, Graphene is fully compatible with the GraphQL spec, working
seamlessly with all GraphQL clients, such as
`Relay <https://github.com/facebook/relay>`__,
`Apollo <https://github.com/apollographql/apollo-client>`__ and
`gql <https://github.com/graphql-python/gql>`__.

Installation
------------

To install `graphene`, just run this command in your shell

.. code:: bash

   pip install "graphene>=3.0"

Examples
--------

Here is one example for you to get started:

.. code:: python

   import graphene

   class Query(graphene.ObjectType):
       hello = graphene.String(description='A typical hello world')

       def resolve_hello(self, info):
           return 'World'

   schema = graphene.Schema(query=Query)

Then Querying ``graphene.Schema`` is as simple as:

.. code:: python

   query = '''
       query SayHello {
         hello
       }
   '''
   result = schema.execute(query)

If you want to learn even more, you can also check the following
`examples <examples/>`__:

-  **Basic Schema**: `Starwars example <examples/starwars>`__
-  **Relay Schema**: `Starwars Relay
   example <examples/starwars_relay>`__

Documentation
-------------

Documentation and links to additional resources are available at
https://docs.graphene-python.org/en/latest/

Contributing
------------

After cloning this repo, create a
`virtualenv <https://virtualenv.pypa.io/en/stable/>`__ and ensure
dependencies are installed by running:

.. code:: sh

   virtualenv venv
   source venv/bin/activate
   pip install -e ".[test]"

Well-written tests and maintaining good test coverage is important to
this project. While developing, run new and existing tests with:

.. code:: sh

   py.test graphene/relay/tests/test_node.py # Single file
   py.test graphene/relay # All tests in directory

Add the ``-s`` flag if you have introduced breakpoints into the code for
debugging. Add the ``-v`` (“verbose”) flag to get more detailed test
output. For even more detailed output, use ``-vv``. Check out the
`pytest documentation <https://docs.pytest.org/en/latest/>`__ for more
options and test running controls.

You can also run the benchmarks with:

.. code:: sh

   py.test graphene --benchmark-only

Graphene supports several versions of Python. To make sure that changes
do not break compatibility with any of those versions, we use ``tox`` to
create virtualenvs for each Python version and run tests with that
version. To run against all Python versions defined in the ``tox.ini``
config file, just run:

.. code:: sh

   tox

If you wish to run against a specific version defined in the ``tox.ini``
file:

.. code:: sh

   tox -e py10

Tox can only use whatever versions of Python are installed on your
system. When you create a pull request, Travis will also be running the
same tests and report the results, so there is no need for potential
contributors to try to install every single version of Python on their
own system ahead of time. We appreciate opening issues and pull requests
to make graphene even more stable & useful!

Building Documentation
~~~~~~~~~~~~~~~~~~~~~~

The documentation is generated using the excellent
`Sphinx <http://www.sphinx-doc.org/>`__ and a custom theme.

An HTML version of the documentation is produced by running:

.. code:: sh

   make docs

.. |Graphene Logo| image:: http://graphene-python.org/favicon.png
.. |Build Status| image:: https://travis-ci.org/graphql-python/graphene.svg?branch=master
   :target: https://travis-ci.org/graphql-python/graphene
.. |PyPI version| image:: https://badge.fury.io/py/graphene.svg
   :target: https://badge.fury.io/py/graphene
.. |Coverage Status| image:: https://coveralls.io/repos/graphql-python/graphene/badge.svg?branch=master&service=github
   :target: https://coveralls.io/github/graphql-python/graphene?branch=master
