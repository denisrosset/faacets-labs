Faacets Roadmap
===============

This document presents the developement steps that will lead the Faacets platform to its first release. The goal of the first release is to incorporate support for most of the Bell expressions families presented in the recent review on Bell nonlocality BellReview_. This includes most inequalities published in the litterature, i.e. nearly 300'000 expressions.

.. _BellReview: http://arxiv.org/abs/1303.2849

Each milestone focuses on one part of the software, and is completed when the points contained have been discussed, coded, tested and documented.

The following artifacts are updated at the end of a Beta cycle:

- WEB: the Faacets website FaacetsWebsite_
- DATA: the Faacets compendium data files FaacetsData_
- CLI: the Faacets command line tool
- API: the Faacets Java library
- DOC: the Faacets documentation FaacetsDocs_

.. _FaacetsWebsite: http://www.faacets.com
.. _FaacetsData: https://github.com/denisrosset/faacets-data
.. _FaacetsDocs: http://docs.faacets.com


Beta 1
------

Release date: February 2014

The current proof-of-concept prototype running FaacetsWebsite_, launched during QIP 2014.

Some of the terminology is outdated compared to the more recent preprint (to appear on the arXiv).

.. todo: Add link to preprint on arXiv

Beta 2
------

Focus: file format specification and terminology

Points covered:

- the YAML file format for basic expression properties (scenario, representations, coefficients, decomposition, sources, names)
- organization and numbering of expressions in the compendium

At the end, the following parts of Faacets will be updated:

- WEB: display of expressions
- DATA: release of < 100 expressions in the stabilized format
- DOC: the YAML file format specification
- CLI: option to compute the decomposition of a YAML file and to compute automatically generated properties

Beta 3
------

Focus: how to add/manage expressions ?

Points covered:

- compendium management: structure of files/folders
- command-line tools to manage, check, curate the compendium
- Java library to read/write YAML files from e.g. Matlab
- contribution process

Updates:

- DATA: completion of the compendium with 1'000 of new expressions
- WEB: move to a virtual server
- DOC: Quick start guide "How to contribute"
- CLI: tools for compendium handling

Beta 4
------

Focus: browsing the compendium

Points covered:

- Website user interface
- Java API interface (access from e.g. Matlab)

 
Beta 5
------

Focus: scaling to 100'000 expressions

Points covered:

- H2 database index
- stress testing
- compendium consultation

Release Candidate
-----------------


First release
-------------
