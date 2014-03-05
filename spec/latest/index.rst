Faacets file format, specification version 0.15
================================

The Faacet interchange file format is used to exchange information about Bell expressions, oriented Bell expressions and Bell and Bell-like inequalities. It could be extended in the future to describe correlations, for example to classify non-signaling boxes.

The format is based on the YAML file format version 1.2 (see YAMLSpec_), a human-readable file format which can be parsed in all major programming languages.

.. _YAMLSpec: http://www.yaml.org/spec/1.2/spec.html


File Metadata
----------
 
We do not use YAML tags to denote the types of our objects. Instead, the type of an object is given by a  required ``type`` key at the base level, associated with a string value. 

For now, only Bell expressions and their derivatives can be described, so the only valid ``type`` at the root node is ``BellExpression``.

Files can also contain have the following optional keys:

sources
  Contains a mapping whose keys correspond to properties contained in the files. The mapping values are
  sequences of identifiers who link resources such as publications or preprints. The following identifiers are supported:

  - *DOI identifiers* starting with ``doi:`` ,
  - *arXiv identifiers* starting with ``arXiv:``,
  - *URLs* starting with ``http:`` or ``https:``.

  Each mapping key should correspond to the sequence of keys to traverse to obtain the property in question,
  for example ``lower.bounds.no-signaling`` or ``upper.facetOf.local``.

shortName
  String describing short name (3-10 characeters) for the object in the current file. Used only for objects who have
  a clear and widely used name, such as ``CHSH`` or ``I3322``. Most objects in the database do not have a
  short name.

names
  One or several names used in the litterature for the object in the current file, as a YAML sequence of strings.

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
  Value is always a string equal to ``BellExpression``.

scenario
  String describing the scenario in which the expression is defined. Scenarios are detailled in ....

representation
  The representation used for the Bell expression coefficients. Several representations, such as probabilities,
  Collins-Gisin or correlators can be used. See ...

coefficients
  Vector of integer or rational coefficients describing the Bell expression.
  In the case of integer coefficients, the value associated to the ``coefficients`` key is a YAML sequence
  of integers. In the case of rational coefficients, the value associated to the ``coefficients`` key is a mapping
  with ``numerator`` and ``denominator`` keys. The value associated to the  ``numerator`` key is a sequence
  of integer, and ``denominator`` is a single integer acting as the common denominator of the coefficients.

Symmetry group
~~~~~~~~~~~~~

Under the ``symmetryInfo`` key, information about the symmetry group can be optionally written down in the YAML file. This information can be computed from scratch using the Faacets command line tool.

When ``symmetryInfo`` is provided, the following properties are required:

numberOfRepresentatives
  Integer giving the number of representative of the Bell expression under relabelings. The order of the
  symmetry group of the Bell expression can be then computed using Lemma XXX of our paper.

remarkableGenerators
  List of generators of the symmetry group of the Bell expression. The generators are grouped according
  to the remarkable subgroups they are part of, according to the following sequence of subgroups:

  - *liftings*: relabelings involving outcomes of a single setting of a single party
  - *outputPermsPerParty*: relabelings involving outcomes of a single party
  - *outputPerms*: general outcomes relabelings
  - *inputPermsPerParty*: relabelings involving settings of a single party
  - *outputInputPermsPerParty*: relabelings involving settings and outcomes of a single party
  - *outputInputPerms*: relabelings involving settings and outcomes
  - *partyPerms*: relabelings involving parties only
  - *rest*: additional generators

.. todo:: Add link to our paper, to the Faacets command line tool documentation

Keywords
~~~~~~~~

Keywords associated to a Bell expression. When no keywords are known, the ``keywords`` property can be omitted. Otherwise, the ``keywords`` property consists of a sequence of strings. Keywords themselves consist of alphanumerical characters plus the hyphen ``-`` and underscore ``_``.

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

canonical
  The Bell expression is known to be ``minimal``,  ``not-io-lifted``, ``not-composite``. In addition, the scenario itself is ordered canonically, and the bound has been extracted from the coefficients, who themselves are written down using integers with GCD = 1.

.. todo:: Add link to our paper, to the Faacets command line tool documentation

Decomposition
~~~~~~~~~~~~~

Additionally, the decomposition of a Bell expression can be stored in the YAML file to avoid expensive recomputations.

.. todo:: Describe decompositions

Oriented Bell Expression
-------------------~~~~~

Oriented Bell expressions are described by a Bell expression along with a direction ``<=`` or ``>=``. Data about an oriented Bell expression is written using a ``BellExpression`` along with additional data in the special properties ``lower`` and ``upper``, describing knowledge about the ``expr >= bound`` and ``expr <= bound`` directions respectively.

Each direction ``lower`` and ``upper`` can have the following properties:

bounds
  Mapping listing bounds corresponding to different sets of interest. The mapping keys ``local``, ``quantum`` and ``no-signaling`` are reserved for the usual accordingly named sets. The mapping values can be either:

  - integers,
  - plus or minus infinity, written down ``-inf`` or ``inf``,
  - rational numbers written down using a string with format ``numerator/denominator``,
  - intervals written down as ``[lb, ub]``, where ``lb``, ``ub`` can be integers, rationals or infinities.

  Decimal numbers describing floating-point values known with limited precision will be supported in a later version of this file format.

facetOf
  Mapping listing the facet-defining property for sets of interest. The mapping keys ``local`` and ``no-signaling`` are reserved, and the mapping values are the boolean ``true`` or ``false``. If the
  facet-defining property is not known, the corresponding key is simply not present.

keywords
  Keywords can be associated to an oriented Bell expression. For now, we do not have reserved keywords, nor
  do we compute keywords automatically for *oriented* expressions.

Canonical Bell Expression
-------------------------

To consider a Bell expression for inclusion in the ``Faacets`` database, the Bell expression should be ``canonical`` (see the this keyword description). In addition, the file should not provide lower bounds, as only upper bounds are allowed.

The canonical objects are stored in the ``canonical`` folder, have only integer file names starting from ``0``.  For Bell expressions stored in the ``canonical`` folder, a single additional property ``oppositeIndex`` can be required, giving the index the canonical form of the opposite Bell expression if it is also present in the database. If the canonical form of the opposite Bell expression is not present in the database, the property is omitted.

.. todo:: add links
 
