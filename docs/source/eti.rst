Estructura
=====

.. Estructura:

ETI
------------

**hw-monitor** consta de dos archivos de R shiny (server.R y ui.R). En ellos se define la apariencia y distribucion de algunos textos dentro de la aplicacion. Los textos mas largos se encuentran en un directorio **docs/** que ademas de tener estos archivos de texto, tiene algunas imagenes usadas como ejemplos. El directorio **www/** tiene linkeados los repositorios externos, ademas de otras imagenes y logos usados en la applicacion.

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']
