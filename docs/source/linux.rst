Linux Cheat Sheet
=================

.. _linux:

Last Boot Time
--------------
.. code-block:: sh

   shell$who -b

Shutdown with options
---------------------
.. code-block:: sh

   shell$shutdown [OPTIONS...] [TIME] [WALL...]
   shell$sudo shutdown 19:05 "Rebooting for ..."

Secure Copy
------------
.. code-block:: sh

   shell$scp -r <source> <destination> #for transferring "directories"
   shell$scp -r -C <source> <destination> #compress
   shell$scp -r -c bluefish <source> <destination> #compression algorithm

.. autosummary::
   :toctree: generated