---
layout: page
title: Relabelings/permutations
---

Relabelings/permutations
========================

Permutations are specified by a string composed of relabelings of
measurement outcomes, measurement settings and party permutations, in
that order, separated by single spaces. Note that permutations acts as a
right action on Bell expressions (see the Appendix of
[FaacetsPaper](http://www.arxiv.org)).

A relabeling of measurement outcomes is specified by writing the party
and measurement setting affected first, using a letter and a number
respectively, and then the permutation of outcomes itself using the
cycle notation.

For example, the permutation of outcomes 1 and 2 for the third
measurement setting of Alice is written `A3(1,2)`.

A relabeling of measurement settings is specified by writing first the
party letter and then permutation of settings in the cycle notation. The
cyclic permutation of the three measurement settings of Alice is written
`A(1,2,3)`.

Permutation of parties is written in the cycle notation, using letters.
For example, the permutation of Alice and Bob is written `(A, B)`.

As an example, the generators of the symmetry group of the original CHSH
inequality can be written as:

-   `A1(1,2) A2(1,2) B1(1,2) B2(1,2)` (permuting outcomes for all
    settings)
-   `A2(1,2) B(1,2)`, `B1(1,2) A(1,2)` (permuting outcomes and settings
    at the same time)
-   `A(1,2) B(1,2) (A,B)` (permuting parties and settings).

