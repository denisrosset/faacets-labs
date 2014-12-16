How to run
----------

To create the static website, run the command
> jekyll build

To serve the website locally, run
> jekyll serve


How to modify the website
-------------------------

Directly update any markdown file.

Note that the files are processed by Liquid and Markdown. Thus, latex commands must start with `\\(` and end with `\\)`, and their underscores `_` must be specified as `\_'.

The table of content is constructed automatically from the markdown files (maximum 2 levels for now), as specified by the 'children' directive in the beginning of the .md files. The root markdown file is ./index.md. It sets the first level of the table of content.

All files which are not linked through the 'children' directive are transfered to the website, but cannot be accessed.
