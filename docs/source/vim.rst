VIM Cheat Sheet
===============

.. _vim:

VIM Shortcuts
--------------

.. code-block:: sh

   ZZ  # Save current line, close it
   s   # Delete the current line, go to insert mode
   w   # Move 1 word <-
   b   # Move 1 word ->
   yyp # Duplicate current line

If you open a non-modifiable file with vim
-------------------------------------------
.. code-block:: sh

   :w !sudo tee %

Search && Replace all occurrences in a particular file
-------------------------------------------------------
.. code-block:: sh

   :%s/FileBin/FileTxt/g


.. autosummary::
   :toctree: generated

