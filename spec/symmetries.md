---
layout: page
title: Bell expression symmetries
---

Information about the symmetry group of an expression can be optionally
written down in the YAML file under the optional `symmetries` key. The
Faacets command line tool can also compute this information from
scratch.

When `symmetries` is provided, the following properties are required:

numberOfRepresentatives
:   An integer giving the number of representative of the Bell
    expression under relabelings. The order of the symmetry group of the
    Bell expression can be then computed using Lemma 1 of
    [arXiv](http://www.arxiv.org).

remarkableGenerators
:   This section list a set of generators for the symmetry group of the
    Bell expression. Generators are grouped according to the remarkable
    subgroups they are part of, according to the following sequence of
    subgroups:

    -   *liftings*: relabelings involving outcomes of a single setting
        of a single party
    -   *outputPermsPerParty*: relabelings involving outcomes of a
        single party
    -   *outputPerms*: general outcomes relabelings
    -   *inputPermsPerParty*: relabelings involving settings of a single
        party
    -   *outputInputPermsPerParty*: relabelings involving settings and
        outcomes of a single party
    -   *outputInputPerms*: relabelings involving settings and outcomes
    -   *partyPerms*: relabelings involving parties only
    -   *rest*: additional generators

As an example, here is the symmetry information for the CHSH expression.

~~~~ {.sourceCode .yaml}
symmetries:
  numberOfRepresentatives: 8
  remarkableGenerators:
    outputPerms: ['A1(1,2) A2(1,2) B1(1,2) B2(1,2)']
    outputInputPerms: ['A2(1,2) B(1,2)', 'B1(1,2) A(1,2)']
    rest: ['A(1,2) B(1,2) (A,B)']
~~~~
