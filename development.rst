Development process
===================

The source code and data files are hosted on Github in several repositories. We are migrating these repositories to the branching model proposed in SuccessfulGitBranchingModel_.

.. _SuccessfulGitBranchingModel: http://nvie.com/posts/a-successful-git-branching-model/

Starting from March 24, the ``master`` branch contains the releases, we use release branches for bugfixes, and a development branch + feature branches during the development. The plan for different beta releases is detailed in :doc:`roadmap`. Four main repositories can be accessed:

- faacets_ can be used to compile the JAR library and command-line tool,
- faacets-play_ (private) implements the Faacets website interface,
- faacets-data_ contains the YAML data files for the currently referenced Bell expressions,
- faacets-docs_ contains the source code for this documentation (generated using Sphinx).

.. _faacets: https://github.com/denisrosset/faacets
.. _faacets-data: https://github.com/denisrosset/faacets-data
.. _faacets-play: https://github.com/denisrosset/faacets-play
.. _faacets-docs: https://github.com/denisrosset/faacets-docs

In addition, we developed two stand-alone libraries:

- the alasc_ library implements computational group theory algorithms such as Schreier-Sims,
- the polyta_ library performs bare-bones rational linear algebra and interfaces a few polytope solvers.

.. _alasc: https://github.com/denisrosset/alasc
.. _polyta: https://github.com/denisrosset/polyta
