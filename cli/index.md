Command-line tool
=================

The Faacets command line tool can be launched using the library JAR as
follows:

> \$ java -jar Faacets-XXXX.jar --help

of course replacing `Faacets-XXXX.jar` by the name of the JAR
corresponding to the correct version.

The command-line tool provides:

-   commands to deal with individual YAML files,
-   commands to work with compendiums.

Commands for individual YAML files
----------------------------------

### Create a YAML file from a Bell expression

Use the following command:

> \$ java -jar Faacets.jar yaml create -o file.yaml -s "[(2 2) (2 2)]"
> "\<A1 B1\> + \<A1 B2\> + \<A2 B1\> - \<A2 B2\>"

If the scenario is not provided using the option `-s`, it is guessed
automatically. If an output filename is not provided using the option
`-o`, the YAML content is printed on the standard output.

Commands for compendiums
------------------------

### Create a H2 database file

To create a H2 database file in the compendium residing in the `data`
subfolder:

> \$ java -jar Faacets.jar comp create-db -f data

If the folder containing the compendium is not provided using the `-f`
option, the current directory is used instead.

If the H2 database file already exists, the software will throw an
exception.

### Index canonical expressions

Refreshes the index of canonical expressions in the existing H2 database
file. Clears the existing cross-references.

> \$ java -jar Faacets.jar comp index-canonical -f data

### Decompose expressions

Decomposes all the non-canonical expressions present in the compendium,
using the existing index of canonical expressions.

> \$ java -jar Faacets.jar comp decompose -f data

### Cross-reference expressions

Refreshes the cross-reference tables in the H2 database file.

> \$ java -jar Faacets.jar comp cross-ref -f data

### Add new canonical expressions

Adds all new canonical expressions to the canonical folder.

> \$ java -jar Faacets.jar comp new-canonical -f data
