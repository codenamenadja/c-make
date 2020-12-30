03_Writing_Makefiles
====================

tell ``make`` how to recompile a system comes from
reading a database, called the ``makefile`` .

03-1_What_Makefiles_contain?
----------------------------

**5 Components in makefile**::

   - explicit rules: when and how to remake one or more files(targets).
   - implicit rules: when and how to remake a class of files based on their names.
   - variable definitions
   - directives: instruction for ``make`` to do something special.
      - Reading another makefile
      - Deciding whether to use or ignore a part of the makefile
      - Defining a variable from a string-line(s).

   - comments: ``#`` starts comment.

03-2 What Name to Give your Makefile
------------------------------------

when make looks for the makefile, tries the following names.

   1. GNUmakefile (Specific to GNU version make)
   #. makefile
   #. Makefile

Recommend ``Makefile`` because,
it appears prominently near the beginning of a directory listing.
right near other important file such as ``README`` .

If none of upper shows by program, it will not run.
``make --file=unusual`` will run the make by specified file name.
multiple option for ``-f 1 -f 2 -f 3`` will run make in order.

03-3 Including Other Makefiles
------------------------------

``include`` directive tells ``make`` to suspend reading the
current makefile and read one or more other makefile,
before continues it.

The directive is a line in makefile that loooks like this::

   include filename...

white space is required between all of them.
if filename contain any variable or function reference,
they are expanded.

When to use include directive?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. when several programs, handled by individual makefiles in variouse directories,
   need to use a common set of variable definitions or pattern rules.

2. when you want to generate prerequisites from source files automatically::

   The prerequisites can be put in a file that is included by the main makefile.

This practice is generally cleaner than that of somehow appeding the
prerequisiites to the end of the main makefile as has been traditionally done
with other versions of make.

``make --include-dir=../makefiles`` will connect the ``include`` directives.

03-4 ENV variable MAKEFILES
---------------------------

The main use of ``MAKEFILES`` is in **communication between recursive invocations of make.**
   if you are running make without a specific makefile,
   a makefile in ``MAKEFILES`` can do useful things to help the
   built-in implicit rules work better, such as defining search paths.

Some users are tempted to set ``MAKEFILES`` in the enviroment automatically on login,
and programs makefiles to expect this to be done.

This is very bad idea.
because such makefiles will fail to work if run by anyone else.
It is much better to write explicit ``include`` directive in the makefiles.

03-5 HOW Makefiles Are Remade
-----------------------------

Sometime makefiles can be remade from other files, such as RCS or SCCS files.
if it was, you probably want make to get an up-to-date version of the makefile to read in.


