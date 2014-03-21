Faacets Roadmap
===============

For the first release, our goal is to include the main Bell expression families from the literature, including the data files from Avis, Bancal and Vertesi, thus growing the compendium to nearly 300'000 expressions.

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


Beta 0
------

Release date: February 2014

The current proof-of-concept prototype running FaacetsWebsite_, launched during QIP 2014.

Some of the terminology is outdated compared to our more recent preprint (to appear on the arXiv).

.. todo: Add link to preprint on arXiv

Beta 1
------

Focus point: file format specification and terminology

- the YAML file format for basic expression properties (scenario, representations, coefficients, decomposition, sources, names)
- organization and numbering of expressions in the compendium

At the end, the following parts of Faacets will be updated:

- WEB: display of expressions
- DATA: release of < 100 expressions in the stabilized format
- DOC: the YAML file format specification
- CLI: option to compute the decomposition of a YAML file and to compute automatically generated properties

Beta 2
------

Focus point: how to add/manage expressions ?

- compendium management: structure of files/folders
- command-line tools to manage, check, curate the compendium
- Java library to read/write YAML files from e.g. Matlab
- contribution process

Updates:

- DATA: completion of the compendium with 1'000 of new expressions
- WEB: move to a virtual server
- DOC: Quick start guide "How to contribute"
- CLI: tools for compendium handling

Beta 3
------

Focus point: browsing the compendium

- Website user interface
- Java API interface (access from e.g. Matlab)

 
Beta 4
------

Focus point: scaling to 100'000 expressions

- H2 database index
- stress testing
- compendium consultation

Release Candidate
-----------------


First release
-------------
