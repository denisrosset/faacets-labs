Representations
===============

The concept of representations is used in several places in Faacets. It tells you two things about geometrical objects:

- if the object represents or applies to correlations, strategy weights,
  or (in the future) single party marginals,
- if the object is represented in the complete signaling space, or if it is projected/represented 
  only in the non-signaling space,
- in which basis the object is represented.

As of now, there are eight representations, which are described below.

Correlation representations
---------------------------

- the `P` Probability representation, where all coefficients P(ab...|xy...) are enumerated
- the `G` Collins-Gisin representation (see Collins&Gisin, doi:10.1088/0305-4470/37/5/021)
- the `C` correlators representation (see e.g. Sliwa, doi:10.1016/S0375-9601(03)01115-0)

These are prefixed either with `S` if the representation is fully dimensional and includes
the signaling and normalization degrees of freedom, or with `N` if the representation
represents the non-signaling subspace.

For any object, conversion between any two of NPRepr, NGRepr, NCRepr should be bijective,
the same for the conversion between any two of SPRepr, SGRepr, SCRepr, the same for the
conversion between TRepr and WRepr.

When conversion between two representations is bijective (i.e. without loss of information),
we say that these representations are *compatible*.

Strategy weights representations
--------------------------------

- the `W` representation of the decomposition of a local point
  over deterministic strategies, with weights `q`
  (see Branciard et al. doi:10.1103/PhysRevA.85.032119)
- the `T` representation of `strategy correlators`
  (see the definition of e_ijk in Branciard et al. doi:10.1103/PhysRevA.85.032119)

All the `Representation` values defined here correspond to `Repr` inner objects in either
`Party` or `Scenario` which describe the characteristics of the given representation for the
party or scenario enclosing them.
