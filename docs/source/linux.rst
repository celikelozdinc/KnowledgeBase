Linux Cheat Sheet
=====

.. _linux:

Last Boot Time
------------
.. code:: bash
    who -b

Shutdown with options
------------
.. code:: bash
    shutdown [OPTIONS...] [TIME] [WALL...]
    sudo shutdown 19:05 "Rebooting for ..."

Secure Copy
------------
.. code:: bash
    scp -r <source> <destination> #for transferring "directories"
    scp -r -C <source> <destination> #compress
    scp -r -c bluefish <source> <destination> #compression algorithm

New Header
------------
$ cat file.txt

.. autosummary::
   :toctree: generated