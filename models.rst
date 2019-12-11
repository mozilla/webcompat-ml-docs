*******
Models
*******

``needsdiagnosis``
==================

Given a set of webcompat issues, this model classifies if an untriaged issues needs to be diagnosed.

Metrics
-------

Report
^^^^^^^^

.. code-block::

                 precision    recall  f1-score   support
          False       0.90      0.99      0.94     11174
           True       0.70      0.24      0.36      1537

       accuracy                           0.90     12711
      macro avg       0.80      0.61      0.65     12711
   weighted avg       0.88      0.90      0.87     12711

Confusion matrix
^^^^^^^^^^^^^^^^^

.. code-block::

   [[11010   164]
    [ 1162   375]]

Usage
------

.. code-block:: console

   $ Usage: webcompat-ml-needsdiagnosis [OPTIONS] COMMAND [ARGS]...

   Options:
     --help  Show this message and exit.

   Commands:
     evaluate
     predict
     train

Classify issue
^^^^^^^^^^^^^^^

.. code-block:: console

   Usage: webcompat-ml-needsdiagnosis predict [OPTIONS]

   Options:
     --data TEXT    Path to input CSV
     --model TEXT   Path to binary model
     --output TEXT  Predictions output
     --help         Show this message and exit.

Train model
^^^^^^^^^^^^

.. code-block:: console

   Usage: webcompat-ml-needsdiagnosis train [OPTIONS]

   Options:
     --data TEXT    Path to dataset CSV
     --output TEXT  Path to model binary path
     --help         Show this message and exit.

Evaluate model
^^^^^^^^^^^^^^

.. code-block:: console

   Usage: webcompat-ml-needsdiagnosis evaluate [OPTIONS]

   Options:
     --data TEXT  Path to input CSV
     --help       Show this message and exit.
