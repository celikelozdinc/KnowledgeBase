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
   gg          # Move to start of the first line in the file
   <number> G  # Move to start of the specific line
   0           # Move to start of the current line
   G           # Move to start of the last line in the file
   A <text>    # Append text after the end of the current line
   a <txt>     # Append text after the cursor
   wq <filename> # Saves current file with name
   !ls # Executes bash command inside vim

.. image:: docs/img/move.jpg
  :width: 400
  :alt: Move commands


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

