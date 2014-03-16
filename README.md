annot
=====

Annotate Source Code.

Annotations are saved into single sqlite files.

(I wonder if this project name is proper)

Synopsis
--------

    $ annot [<option> ...] <command> [<args>]


Available commands are:

    add a query q database d ls mv


Some "global" options are available:

* `-d|--database <file>` : Path for database file
* `-t|--table <table>` : Table name
* `-n|-r|--[no-]resolve-path` : Decide if paths should be resolved (see below)



Resolving Path and Database Path
--------------------------------


...


Add
---

Add/update annotations.

    $ annot a[dd] <file> [-l|--line <num>] [-a|--append|-u|--update][<text>]

Options:

* `<file>` : (Mandatory) File path of annotation
* `-l|--line <num>` : Line number for annotation. If omitted or `0` is given,
the annotation is considered to be for the file as a whole
* `-a|--append|-u|--update` : This options change behaviors when a annotations
already exist for specified file and line. If `-a` or `--append` is given,
text is appended to the existing annotation (this is default). If `-u|--update`
is given, the annotation is overwritten by new text. In this case, give
empty text to delete the annotation for the file and line.
* `<text>` : Annotation body. If omitted or `-` is given, text is read from
stdin



Query
-----

Query stored annotations.

    $ annot q[uery] [-f|--file <file>] [-l|--line <num>] [-s|--search <text>]
                  [-1|--oneline] [-f|--format <format>]

Options:

* Querying:
    * `-f|--file <file>` : File path to query
    * `-l|--line <num>` : Line number to query
    * `-s|--search <text>` : Search text from annotations
* Printing:
    * `-1|--oneline` : Show only first line of annotations
    * `-f|--format` : Print result in given format like `{file}|{line}|{text}`
    (this is used by default)


Database
--------

Managing database file.

    $ annot d[ateabase] [-i|--init]
    $ annot d[ateabase] [-f|--find]
    $ annot d[ateabase] [-d|--find-dir]

* `-i|--init` : Initialize database file
* `-f|--find` : Find and return the path to database file that will be used
* `-d|--find-dir` : Find and return the directory that have database file


LS
---

List files whose annotations are stored in the database.


MV
---

Change file path for annotations (not database itself, just rewrite paths
related to stored annotations).

    $ annot mv <old> <new>
