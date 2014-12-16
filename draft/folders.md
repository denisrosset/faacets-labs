---
layout: page
title: Compendium structure
parent: Draft pages
---

A *compendium* is a collection of Bell expressions, represented as a
structure of folders containing subfolders and expressions in Faacets.
Paths in this structure are written using the `/` separator, without
extensions.

On disk, this structure is represented using directories and files,
which matches the structure of folders and expressions, with a few
exceptions.

At the first level, the expressions are classified in three folders,
corresponding to directories on disk:

-   *canonical* expressions are stored in a folder named `canonical`
    represented on disk by a directory of the same name, all together,
    without any further refinement. The $n$ canonical expressions have
    their keys are numbered from 1 to $n$ without gaps. When the
    collection of canonical expressions gets large, it is stored on disk
    using a special *linear folder* structure described below.
-   *internal* expressions are stored in a folder named `internal`
    represented on disk by a directory of the same name. These
    expressions are stored as are canonical expressions, but starting
    the numbering from one billion 1'000'000'000.
-   *published* expressions are in subfolders of a folder named `pubs`.
    The subfolder's name is made from the publication author list
    followed by the year of publication written using 4 digits. We
    suggest to use either the publication first authors (i.e.
    `Acin2004`) or the acronym made of the author names (i.e. `CHSH1969`
    or `CGLMP04`), guided by the way the work is already cited in the
    literature. Example: the CHSH expression has path
    `pubs/CHSH1969/chsh.yaml`
-   *solved* expressions are obtained by completely solving polytopes of
    interest, and are contained in a folder name `solved`. Those
    expressions are stored in subfolders of `solved`, whose path
    structure is made from the parties followed by name of the polytope.
    Each party is written down by the number of outcomes corresponding
    to each setting, separated by hyphens `-`. The polytope name `local`
    is reserved. Example: the Yaml file path corresponding to the $k$-th
    facet of the CHSH polytope is `solved/2-2/2-2/local/k.yaml`.

File and folder names
---------------------

A file or folder name can either be:

-   a non-negative integer key, with no leading zeros,
-   a string key, starting with a lowercase or uppercase letter,
    followed by letters `[a-zA-z]`, digits `[0-9]` or hypen `-`.

An exception to this rule is described below for *linear folders*.

The standard file extension for expressions is `.yaml`. The `.vertesi`
extension is partially supported by Faacets for the files provided by T.
Vértesi on his website.

Folders normally have no extension, except for special folders described
below.

Linear folders
--------------

Linear folders contains only expressions with integer keys numbered from
either 0 or 1, without gaps and without further refinement. To work
around OS performance issues due to the number of files in a single
directory, these files are binned in OS subfolders.

The linear folder name is made of the folder name, followed by a dot `.`
and a power-of-ten integer giving the bin size $n$.

On disk, expressions from $0$ or $1$ to $n-1$ are in the bin 0, the next
n expressions in the bin 1, and so on.

To help the OS display the bins in the proper order, the bin name are
padded with leading zeros. Each bin has the same number of digits.

For example, suppose the *canonical* folder contains 250'000
expressions, with bin size 10'000, padding the bin number to three
digits. The directory structure on disk is as follows:

-   `canonical.10000`

    -   `000`

        -   `0.yaml`
        -   `1.yaml`
        -   ...
        -   `9999.yaml`

    -   `001`

        -   `10000.yaml`
        -   ...
        -   `9999.yaml`

    -   `024`

        -   `240000.yaml`
        -   ...
        -   `249999.yaml`

Reader folders
--------------

A few other extensions are recognized by Faacets and can be processed
using *Folder readers*. These folders are not represented on disk by
directories, but by text files containing a collection of expressions.
The contained expressions will be read and numbered starting from 1:

-   the `.ito` extension is used for the files provided on T. Ito's
    website,
-   the `.bancal` extension is used for the files provided by J.D Bancal
    as supplemental material to the publication *Looking for Bell
    inequalities*.

