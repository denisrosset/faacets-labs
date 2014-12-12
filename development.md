---
layout: page
title: Development process
---

Development process
===================

The source code and data files are hosted on Github in several
repositories. We are migrating these repositories to the branching model
proposed in
[SuccessfulGitBranchingModel](http://nvie.com/posts/a-successful-git-branching-model/).

Starting from March 24, the `master` branch contains the releases, we
use release branches for bugfixes, and a development branch + feature
branches during the development. The plan for different beta releases is
detailed in roadmap. Four main repositories can be accessed:

-   [faacets](https://github.com/denisrosset/faacets) can be used to
    compile the JAR library and command-line tool,
-   [faacetspplay](https://github.com/denisrosset/faacets-play)
    (private) implements the Faacets website interface,
-   [faacetsddata](https://github.com/denisrosset/faacets-data) contains
    the YAML data files for the currently referenced Bell expressions,
-   [faacetsddocs](https://github.com/denisrosset/faacets-docs) contains
    the source code for this documentation (generated using Sphinx).

In addition, we developed two stand-alone libraries:

-   the [alasc](https://github.com/denisrosset/alasc) library implements
    computational group theory algorithms such as Schreier-Sims,
-   the [polyta](https://github.com/denisrosset/polyta) library performs
    bare-bones rational linear algebra and interfaces a few polytope
    solvers.

