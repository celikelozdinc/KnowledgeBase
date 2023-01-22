Linux Cheat Sheet
=================

.. _linux:

1.Last Boot Time
--------------
.. code-block:: sh

   who -b

2.Shutdown with options
---------------------
.. code-block:: sh

   # shutdown [OPTIONS...] [TIME] [WALL...]
   sudo shutdown 19:05 "Rebooting for ..."

3.Secure Copy
------------
.. code-block:: sh

   scp -r <source> <destination> # for transferring "directories"
   scp -r -C <source> <destination> # compress
   scp -r -c bluefish <source> <destination> # compression algorithm

4.grep
----
.. code-block:: sh

   find . -name "*.txt" -exec grep -i --color "RRC" {} \;
   find . -name "*.txt" -exec grep -i --color "SGNB_RELEASE_INITIATED_BY_SN" {} \;
   cat <file> | grep -i "pattern" | head -1 # Search for **first** occurrence
   cat <file> | grep -i "pattern" | tail -1 # Search for **last** occurrence

5.jq
--
.. code-block:: sh

   jq . --indent 4 File.json

6.Enable timestamp in history command
-----------------------------------
`From Linux Handbook <https://linuxhandbook.com/history-command-timestamp/?ref=lhb-linux-digest-newsletter>`_

.. code-block:: sh

   export HISTTIMEFORMAT="%F %T "

7.Search processes
----------------
.. code-block:: sh

   pgrep testmac
   ps aux | grep -i "testmac"

8.Redirect to different terminals
-------------------------------
.. code-block:: sh

   tty # which terminal
   python --version > /dev/pts/0
   node --version > /dev/pts/1

9.Create subshells
----------------
.. code-block:: sh

   # goto build directory
   (cd bin; ./ULAKDU --gtest_filter="")

.. autosummary::
   :toctree: generated