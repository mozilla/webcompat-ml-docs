*******
Models
*******

``needsdiagnosis``
==================

Given a set of webcompat issues, this model classifies if an untriaged issues needs to be diagnosed.

Usage
-----

.. code-block:: console

   $ Usage: webcompat-ml-needsdiagnosis [OPTIONS] COMMAND [ARGS]...

   Options:
     --help  Show this message and exit.

   Commands:
     evaluate
     predict
     train

Classify issue
--------------

.. code-block:: console

   Usage: webcompat-ml-needsdiagnosis predict [OPTIONS]

   Options:
     --data TEXT    Path to input CSV
     --model TEXT   Path to binary model
     --output TEXT  Predictions output
     --help         Show this message and exit.

Train model
-----------

.. code-block:: console

   Usage: webcompat-ml-needsdiagnosis train [OPTIONS]

   Options:
     --data TEXT    Path to dataset CSV
     --output TEXT  Path to model binary path
     --help         Show this message and exit.

Evaluate model
--------------

.. code-block:: console

   Usage: webcompat-ml-needsdiagnosis evaluate [OPTIONS]

   Options:
     --data TEXT  Path to input CSV
     --help       Show this message and exit.
