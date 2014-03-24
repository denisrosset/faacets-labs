Decompositions
==============

The operations that relate a Bell expression to its canonical form are stored in a YAML file to avoid expensive recomputations. The motivation for these operations is described in FaacetsPaper_.

.. _FaacetsPaper: http://www.arxiv.org


AffineTransform
---------------

This describes the transformation of a Bell expression by first multiplying its coefficients by a factor, and then adding a normalization constant. The AffineTransform object has the ``of`` key describing the transformed expression, and an ``affine`` key containing a string of the form ``factor x +/- constant``.

Example (taken from Sliwa's second inequality):

.. code-block:: yaml

   decomposition:
       type: RepresentationTransform
       representation: Non-signaling Correlators
       of:
           type: AffineTransform
	   affine: x + 2
	   of: {type: CanonicalExpression, index: 6}

Example (taken from Sliwa's tenth inequality):

.. code-block:: yaml

   decomposition:
       type: RepresentationTransform
       representation: Non-signaling Correlators
       of:
           type: PermutationTransform
	   permutation: B2(1,2) C2(1,2) (B,C)
	   of:
	       type: AffineTransform
	       affine: 1/2 * x + 4
	       of:
	           type: OppositeTransform
		   of:
		       type: PermutationTransform
		       permutation: A2(1,2) B2(1,2) C1(1,2) C2(1,2) (A,B,C)
		       of: {type: CanonicalExpression, index: 13}

BellExpressionProduct
---------------------

A ``BellExpressionProduct`` describes a composition of Bell expressions. It contains a single key ``of``, composed of a sequence of decomposed Bell expressions. The composition is done by attributing the first :math:`l` parties to the first component of the product, the next :math:`m` parties to the second component, the next :math:`n` parties to the third component and so on.

An example of the decomposition of the positivity in the scenario ``[(2) (2)]``:

.. code-block:: yaml

   type: BellExpressionProduct
   of:
       - type: AffineTransform
         affine: x + 1
         of:
	     type: BellExpression
             scenario: '[(2)]'
             representation: Non-signaling Probabilities
             coefficients: [-1, 1]
       - type: AffineTransform
         affine: x - 1
         of:
             type: BellExpression
             scenario: '[(2)]'
             representation: Non-signaling Probabilities
             coefficients: [-1, 1]

LiftingTransform
----------------

A ``LiftingTransform`` describes the addition of measurement settings/inputs or measurement outcomes/outputs, as described in LiftingPironio_ and FaacetsPaper_. The ``LiftingTransform`` contains an ``of`` key describing the expression to be transformed, and a ``lifting`` key containing a string representing the lifting.

Additional outcomes are always grouped with the outcome they are lifting, and additional settings are always added at the end of measurement settings list.

The syntax for lifting strings is similar to the one for scenarios (see :doc:`/concepts/scenario`). Additional settings/inputs are described by a ``+(n1 n2 ...)`` component after the party description, where ``n1``, ``n2``, ... are the number of outcomes for each additional measurement setting.

Example: the CHSH inequality lifted in the scenario ``[(2 2 2) (2 2 2)]``

.. code-block:: yaml

    type: LiftingTransform
    lifting: Lifting([(2 2)+(2) (2 2)+(2)])
    of:
        type: BellExpression
        scenario: '[(2 2) (2 2)]'
        representation: Non-signaling Probabilities
        coefficients: [-1, 1, -1, 1, 1, -1, 1, -1, -1, 1, 1, -1, 1, -1, -1, 1]


Additional outcomes are described by a ``+(m1 m2 ... mn)`` right after a measurement setting description, and``n`` is the number of measurement outcomes. The numbers ``mj`` prescribe the number of additional outcomes attached to each original measurement outcome.

Example: the CHSH inequality lifted in the scenario ``[(3 3) (3 3)]```

.. code-block:: yaml

   type: LiftingTransform
   lifting: Lifting([(2+(0 1) 2+(1 0)) (2+(1 0) 2+(1 0))])
   of:
       type: BellExpression
       scenario: '[(2 2) (2 2)]'
       representation: Non-signaling Probabilities
       coefficients: [-1, 1, -1, 1, 1, -1, 1, -1, -1, 1, 1, -1, 1, -1, -1, 1]

.. _LiftingPironio: http://dx.doi.org/10.1063/1.1928727
.. _FaacetsPaper: http://www.arxiv.org

OppositeTransform
-----------------

PermutationTransform
--------------------

RedundantTransform
------------------

RepresentationTransform
-----------------------

RepresentativeTransform
-----------------------

