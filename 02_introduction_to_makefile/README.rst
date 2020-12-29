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

**This is straightforward_makefile_**
   - NAME:      ``edit``
   - Objects:   8 files (all c file includes ``def.h``)
   - headers:   3 files

**running some target on make**
   1. When target is a file? (ye)
   #. prerequisite of file change? (ye)
   #. recompile and relink!
 
.. _straightforward_makefile: src/02-2_simple_makefile
.. note::

   ``:`` means target, ``=`` means variable.

02-5_Letting_make_deduce_the_recipes
------------------------------------

Implicit rule for c in make 
   update ``.o`` file from corresponding ``.c`` file using ``cc -c`` command.

Here is ``.c`` omitted_rule_makefile_.

.. _omitted_rule_makefile: src/02-5_deduce_the_recipes_makefile

02-6_Another_style_of_makefile
------------------------------

In this another_style_of_makefile_,
you group entries by their prerequisites
instead of by their targets.

.. _another_style_of_makefile: src/02-6_shorter_makefile
