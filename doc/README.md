Generate documentation for CHAMEO
=================================
This directory contains the needed templates, introductory text and
figures for generating the full EMMO documentation using `ontodoc`.
Since the introduction is written in markdown, pandoc is required for
both pdf and html generation.

For a standalone html documentation including all inferred relations,
enter this directory and run

    ontodoc --template=chameo.md --format=html ../chameo.ttl chameo.html

Pandoc options may be adjusted with the files
[pandoc-args.yaml](pandoc-args.yaml) and
[pandoc-html-args.yaml](pandoc-html-args.yaml).

Similarly, for generating pdf documentation, enter this directory and run

    ontodoc --template=chameo.md --format=pdf ../chameo.ttl chameo.pdf

By default, we have configured pandoc to use xelatex for better unicode
support.  It is possible to change these settings in
[pandoc-args.yaml](pandoc-args.yaml) and
[pandoc-pdf-args.yaml](pandoc-pdf-args.yaml).




Using this example as a starting point for documenting your own ontology
------------------------------------------------------------------------
For simple html documentation, you can skip all input files and simply
run `ontodoc` as

    ontodoc --format=simple-html YOUR_ONTO.owl YOUR_ONTO.html

It is also possible to include ontodoc templates using the --template
option for adding additional information and structure the document.
In this case the template may only contain `ontodoc` pre-processer
directives and inline html, but not markdown.

In order to produce output in pdf (or any other output format supported
by pandoc), you can write your `ontodoc` template in markdown (with
`ontodoc` pre-processer directives) and follow these steps to get started:

  * Copy all the files starting with `pandoc-` to a new directory.
  * Create a metadata yaml file for your ontology. You can use
    [emmodoc-meta.yaml](emmodoc-meta.yaml) as a template.
  * Update [pandoc-args.yaml](pandoc-args.yaml).  Especially change:
      - `input-files` to the name of your new yaml metadata file
      - `logo` to the path of your logo (or remove it)
      - `titlegraphic` to the path of your title figure (or remove it)
  * Optionally add `ontodoc` template files with additional information
    about your ontology and document layout.

That should be it.  Good luck!
