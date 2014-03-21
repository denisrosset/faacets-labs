Faacets file format
===================

The Faacet interchange file format is used to exchange information about Bell expressions, oriented Bell expressions and Bell and Bell-like inequalities. It could be extended in the future to describe correlations, for example to classify non-signaling boxes.

The format is based on the YAML file format version 1.2 (see YAMLSpec_), a human-readable file format which can be parsed in all major programming languages. Its information is thus organized in a hierarchy of keys, lists, mappings, etc.

.. _YAMLSpec: http://www.yaml.org/spec/1.2/spec.html


File Metadata
----------
 
The faacet file format does not use YAML tags to denote the types of objects. Instead, the type of an object is given by a  required ``type`` key at the base level, associated with a string value. 

For now, only Bell expressions and their derivatives can be described, so the only valid ``type`` at the root node is ``BellExpression``.

Additional metadata can be specified through the following optional keys:

sources
  This section can list references for the information listed in the file. It contains a mapping between properties contained in the file and their source.
  
  Each mapping key should correspond to the sequence of keys to traverse to obtain the property in question, such as ``lower.bounds.no-signaling`` or ``upper.facetOf.local``.
  
  The mapping values are sequences of identifiers who link resources such as publications or preprints. The following identifiers are supported:

  - *DOI identifiers* starting with ``doi:`` ,
  - *arXiv identifiers* starting with ``arXiv:``,
  - *URLs* starting with ``http:`` or ``https:``.

  Here is an example of valid sources section:

.. code-block:: yaml

    sources:
      upper.bounds.local: ['doi:10.1007/BF02903286']
      upper.bounds.quantum: ['doi:10.1103/PhysRevA.82.022116', 'arXiv:1006.3032']
    
shortName
  A short name for the object in the current file can be described by a short string (3-10 characters). This key is only used for objects who have a clear and widely used name, such as ``CHSH`` or ``I3322``. Most objects in the database do not have a short name.

  Example:
  
.. code-block:: yaml

    shortName: CHSH

names
  One or several names used in the litterature for the object in the current file, as a YAML sequence of strings.

  Example:

.. code-block:: yaml

    names: [Clauser-Horne-Shimony-Holt inequality, Clauser-Horne inequality]


Bell Expression
------------

Required properties
~~~~~~~~~~~~~~~

The simplest Bell expression is described by the following YAML fragment:

.. code-block:: yaml

    type: BellExpression
    scenario: '[(2 2) (2 2)]'
    representation: Non-signaling Correlators
    coefficients: [0, 0, 0, 0, 1, -1, 0, 1, 1]
      
The following properties are always required:

type
  The type of a Bell expression is always a string equal to ``BellExpression``.

scenario
  The String describing the scenario in which the expression is defined. The format of scenarios is detailed in Appendix A of arXiv_.

.. _arXiv: http://www.arxiv.org

  For example, a scenario with two parties, two settings and two outcomes is specified by:

.. code-block:: yaml

    scenario: [(2 2) (2 2)]

representation
  This key specifies the parametrization used for the Bell expression coefficients. The supported representations, detailed in [add citation] are:
  
  - ``Non-signaling Probabilities``
  - ``Non-signaling Correlators``
  - ``Non-signaling Collins-Gisin``

.. todo: [pas sure de tous ces noms, et on pourrait aussi ajouter les versions signaling...]

coefficients
  Vector of integer or rational coefficients describing the Bell expression.
  In the case of integer coefficients, the value associated to the ``coefficients`` key is a YAML sequence
  of integers. In the case of rational coefficients, the value associated to the ``coefficients`` key is a mapping
  with ``numerator`` and ``denominator`` keys. The value associated to the  ``numerator`` key is a sequence
  of integer, and ``denominator`` is a single integer acting as the common denominator of the coefficients.


Here are several examples of valid Bell expression specification:

.. code-block:: yaml

    type: BellExpression
    scenario: '[(2 2) (2 2)]'
    representation: Non-signaling Collins-Gisin
    coefficients: [0, -1, 0, -1, 1, 1, 0, 1, -1]
    
.. code-block:: yaml

    type: BellExpression
    scenario: '[(2 2) (2 2)]'
    representation: Non-signaling Collins-Gisin
    coefficients: [0, -1, 0, -1, 1, 1, 0, 1, -1]


Symmetry group
~~~~~~~~~~~~~

Information about the symmetry group of an expression can be optionally written down in the YAML file under the ``symmetryInfo`` key. The Faacets command line tool can also compute this information from scratch.

When ``symmetryInfo`` is provided, the following properties are required:

numberOfRepresentatives
  An integer giving the number of representative of the Bell expression under relabelings. The order of the
  symmetry group of the Bell expression can be then computed using Lemma 1 of arXiv_.
  
.. _arXiv: http://www.arxiv.org

remarkableGenerators
  This section list a set of generators for the symmetry group of the Bell expression. Generators are grouped according
  to the remarkable subgroups they are part of, according to the following sequence of subgroups:

  - *liftings*: relabelings involving outcomes of a single setting of a single party
  - *outputPermsPerParty*: relabelings involving outcomes of a single party
  - *outputPerms*: general outcomes relabelings
  - *inputPermsPerParty*: relabelings involving settings of a single party
  - *outputInputPermsPerParty*: relabelings involving settings and outcomes of a single party
  - *outputInputPerms*: relabelings involving settings and outcomes
  - *partyPerms*: relabelings involving parties only
  - *rest*: additional generators

As an example, here is the symmetry information for the CHSH expression.

.. code-block:: yaml

    symmetryInfo:
      numberOfRepresentatives: 8
      remarkableGenerators:
        outputPerms: ['A1(1,2) A2(1,2) B1(1,2) B2(1,2)']
        outputInputPerms: ['A2(1,2) B(1,2)', 'B1(1,2) A(1,2)']
        rest: ['A(1,2) B(1,2) (A,B)']

.. todo:: Add link to our paper, to the Faacets command line tool documentation

Keywords
~~~~~~~~

This section allows for the specification of properties satisfied by a Bell expression. Keywords can consist of alphanumerical characters plus the ``-`` and underscore ``_``. They are specified as a sequence of strings:

.. code-block:: yaml

    keywords: ['minimal', 'not-io-lifted']

The following keywords are reserved, and can be computed automatically using the ``Faacets`` command-line tool:

minimal
  The Bell expression is the minimal lexicographic representative of its equivalence class under relabelings.

not-minimal
  The Bell expression is known not to be minimal.

io-lifted
  The Bell expression is known to be a lifting of settings and/or outcomes.

not-io-lifted
  The Bell expression is known not to be a lifting of settings and/or outcomes.

composite
  The Bell expression is known to be a composition of simpler Bell expressions, in the sense of the Section of our paper.

not-composite
  The Bell expression is known not to be composite.

selfOpposite
  The Bell expression is equivalent under relabelings to its negative value.

canonical
  The Bell expression is known to be ``minimal``,  ``not-io-lifted``, ``not-composite``. In addition, the scenario itself is ordered canonically, and the bound has been extracted from the coefficients, who themselves are written down using integers with GCD = 1.

.. todo:: Add link to our paper, to the Faacets command line tool documentation

Decomposition
~~~~~~~~~~~~~

The operations that relate a Bell expression to its canonical form can be stored in a YAML file to avoid expensive recomputations. They consist of [...]

.. todo:: Describe decompositions

Oriented Bell Expression
------------------------

Oriented Bell expressions are described by a Bell expression along with a direction ``<=`` or ``>=``. Data about an oriented Bell expression is written using a ``BellExpression`` along with additional data in the special properties ``lower`` or ``upper``, describing knowledge about the ``expr >= bound`` and ``expr <= bound`` directions respectively.

Each direction ``lower`` and ``upper`` can have the following properties:

bounds
  Bounds corresponding to different sets of interest can be listed here through a mapping list. The mapping keys ``local``, ``quantum`` and ``no-signaling`` are reserved for the usual accordingly named sets. The mapping values are given by a string expression made of:

  - integers,
  - infinity written ``inf``,
  - rational numbers written down using the format ``numerator/denominator``,
  - decimal numbers written using ``digits.digits``,
  - arithmetic operators ``+``, ``-``, ``*``, ``/``,
  - parenthesis,
  - intervals written down as ``[lb, ub]``, where ``lb``, ``ub`` are expressions.


  Here is an example of section specifying several bounds:
  
.. code-block:: yaml

    bounds:
      local: 2
      quantum: [-inf, 2.828427124746191]
      nosignaling: x <= 4

Here, the ``[-inf, 2.828427124746191]`` interval expression for the quantum bound interval signifies that we have obtained an approximation for the quantum bound through relaxations, so that the real upper bound is below ``2.828427124746191``. The ``-inf`` side of the interval could be replaced by providing a state and measurements that achieve a quantum value.

keywords
  Keywords can also be associated to an oriented Bell expression. For now, no keywords are reserved, nor is any keywords automatically computed for *oriented* expressions. Keywords here respect the same syntax as the ones for Bell expressions mentioned above. 

  Special keywords specify if a bound corresponds to a facet of some polytope. The keywords ``facet-polytope`` and ``not-facet-polytope`` can be used for that effect, where ``polytope`` corresponds to the name of a bound. The keywords ``(not-)facet-local`` and ``(not-)facet-no-signaling`` are reserved. If the facet-defining property is not known, the corresponding keyword is not present.

  The following is a valid ``keywords'' section:

.. code-block:: yaml

   keywords: [facet-local]

Two orientations of a Bell expression can be specified in a single file by incorporating both a ``lower`` and an ``upper`` section in the file. This can provide a full decription of the bounds satisfied by a given Bell expression.



Canonical Bell Expression
-------------------------

To consider a Bell expression for inclusion in the ``Faacets`` database, the Bell expression should be ``canonical`` (see the this keyword description). In addition, the file should not provide lower bounds, as only upper bounds are allowed.

The canonical objects are stored in the ``canonical`` folder, have only integer file names starting from ``0``.  For Bell expressions stored in the ``canonical`` folder, a single additional property ``oppositeIndex`` can be required, giving the index the canonical form of the opposite Bell expression if it is also present in the database. If the canonical form of the opposite Bell expression is not present in the database, the property is omitted.

.. note:: the opposite expression can always be found by flipping the sign of the coefficients, then looking for the minimal lexicographic representative. No other canonicalization step is affected by the sign flip; in particular the no-signaling parametrization is invariant under sign change.

.. todo:: add links
