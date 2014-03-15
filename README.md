annot
=====

Annotate Source Code.

Annotations are saved into single sqlite files.

(I wonder if this project name is proper)

Synopsis
--------

    $ annot [<option> ...] <command> [<args>]


Available commands are:

    add a query q database d


Some "global" options are available:

* `-d|--database <file>` : Path for database file
* `-t|--table <table>` : Table name


Add
---

Add/update annotations.

    $ annot a[dd] <file> [-l|--line <num>] [<text>]

Options:

* `<file>` : (Mandatory) File path of annotation
* `-l|--line <num>` : Line number for annotation. If omitted or `0` is given,
the annotation is considered to be for the file as a whole
* `<text>` : Annotation body. If omitted or `-` is given, text is read from
stdin

When a annotation for same file and line already exits it will be overwritten
by new text. Give empty text as annotation text to remove annotation.


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
