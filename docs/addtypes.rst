Own encoder extension
=====================

Use Inheritance to add your own types in the encoder

.. code-block:: python
    :linenos:

    class VirgilEncoder(DanteJcoder):
        def default(self, obj):
            if isinstance(obj, MyType):
                result = {'myway': 'myresult'}
                return result
            else:
                return super().default(obj)