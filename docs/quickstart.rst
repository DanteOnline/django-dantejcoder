Quickstart
==========

Installation
------------

``pip install django-dantejcoder``

Simple use
----------

#. Import DanteJcoder

.. code-block:: python

    from dantejcoder.coder import DanteJcoder

#. Get one django model or queriset (for example in result variable)

#. User DanteJcoder in JsonResponse

.. code-block:: python

    return JsonResponse(result, encoder=DanteJcoder)
    
