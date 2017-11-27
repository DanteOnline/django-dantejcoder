Encode settings
===============

Without settings
----------------

Model class:

.. code-block:: python
    :linenos:

    class StandardModel(models.Model):
        name = models.CharField(max_length=32, default='Standard')
        val = models.IntegerField(default=1)

Use DanteJcoder:

.. code-block:: python
    :linenos:

    result = StandardModel.objects.all()
    return JsonResponse(result, encoder=DanteJcoder)

Result:

.. code-block:: javascript
    
    {"id": 1, "name": "Standard", "val": 1}

Selected fields
---------------

To select fields use __to_json_fields__ in your model class

Model class:

.. code-block:: python
    :linenos:

    class RegionTest(models.Model):
        name = models.CharField(max_length=32)

        __to_json_fields__ = ('name',)

Result:

.. code-block:: javascript
    
    {"name": "Perm edge"}

Specific json result
--------------------

To get specific json result add __to_json_dict__ in your model class

.. code-block:: python
    :linenos:

    class CityTest(models.Model):
        name = models.CharField(max_length=32)
        region = models.ForeignKey(RegionTest)

        def __to_json_dict__(self):
            return {'name': self.name, 'region': self.region, 'test': True}

Result:

.. code-block:: javascript
    
    {"name": "Perm", "test": true, "region": {"name": "Perm edge"}}

