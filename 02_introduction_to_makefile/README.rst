02_Introduction_to_Make_files
=============================

In this chapter, will discuss a simple makefile that decribes
how to compile and link a text editor which consists of
eight C source files and three header files.

If a header file has changed, each C source file that includes the header file must be recompiled to be safe.
So, if any source file has been recompiled, all object files, whether newly make or saved from previous compilations,
must be linked together to produce the new executable editor.


02-1_What_a_Rule_Looks_Like
---------------------------

.. code-block:: make

   target ... :  prerequisites ...
       recipe
       ...

   .PHONY: somerule
   somerule: ...
       ...

Simple makefile consists of rules with the follwoing shape

   - A target is executable or object files.
   - A prerequsite is a file that is used as input to create the target.
   - A recipe is an cation that make carries out.
   - A rule, expains how and when to remake certain files which are targets of the particular rule.
   make carries out the recipe on the prerequisites to create or update the target.
   A rule can also expain how and when to carry out an action.

.. note::

   recipe prefix with <TAB> but can be subsitute it, use ``.RECIPEPREFIX`` variable to an alternative.

02-2_A_Simple_Makefile
----------------------


This is `straightforward_makefile`
   - NAME:      ``edit``
   - Objects:   8 files (all c file includes ``def.h``)
   - headers:   3 files


_straightforward_makefile: src/02-2_simple_makefile

