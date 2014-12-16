---
layout: page
title: Faacets file format (beta 2)
children:
  - spec/minimal.md
  - spec/bounds.md
  - spec/keywords.md
  - spec/decomposition.md
  - spec/transform.md
  - spec/symmetries.md
  - spec/metadata.md
  - spec/canonical.md
---

> **note**
>
> The current version (beta 1) of the
> [FaacetsWebsite](http://www.faacets.com) uses an older file format
> which is not documented.

The Faacet interchange file format is used to exchange information about
Bell expressions, oriented Bell expressions and Bell and Bell-like
inequalities. It could be extended in the future to describe
correlations, for example to classify non-signaling boxes.

The format is based on the YAML file format version 1.2 (see
[YAMLSpec](http://www.yaml.org/spec/1.2/spec.html)), a human-readable
file format which can be parsed in all major programming languages. Its
information is thus organized in a hierarchy of keys, lists, mappings,
etc.

<br>

 - [Minimal keys for Bell Expressions](minimal.html)
 - [Lower and upper bounds](bounds.html)
 - [Keywords](keywords.html)
 - [Decomposition and remarkable forms](decomposition.html)
   - Bell Expressions placeholders
 - [Transforms](transform.html)
   - AffineTransform
   - BellExpressionProduct
   - LiftingTransform
   - OppositeTransform
   - PermutationTransform
   - RedundantTransform
   - ReorderingTransform
   - RepresentationTransform
   - RepresentativeTransform
 - [Bell expression symmetries](symmetries.html)
 - [File Metadata](metadata.html)
 - [Canonical Bell Expressions](canonical.html)


