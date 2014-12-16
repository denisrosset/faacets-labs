---
layout: page
title: Faacets file format (beta 2)
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
