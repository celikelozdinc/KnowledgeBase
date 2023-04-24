Linux Cheat Sheet
=================

.. _linux:

1.Last Boot Time
-----------------
.. code-block:: sh

   who -b

2.Shutdown with options
------------------------
.. code-block:: sh

   # shutdown [OPTIONS...] [TIME] [WALL...]
   sudo shutdown 19:05 "Rebooting for ..."

3.Secure Copy
--------------
.. code-block:: sh

   scp -r <source> <destination> # for transferring "directories"
   scp -r -C <source> <destination> # compress
   scp -r -c bluefish <source> <destination> # compression algorithm

4.rsync
--------
`From <https://docs.rackspace.com/support/how-to/copy-files-with-scp-and-rsync/>`_

.. code-block:: sh

    rsync [-avz] /local/path/file_name user@IP.address:/destination/path/
    rsync -vapz 20230417-061959000.txt ozd@10.213.135.18:/home/ozd/Desktop

5.grep
-------
.. code-block:: sh

   #Use Grep to find files based on content
   find . -name "*.txt" -exec grep -i --color "RRC" {} \;
   find . -name "*.txt" -exec grep -i --color "SGNB_RELEASE_INITIATED_BY_SN" {} \;
   cat <file> | grep -i "pattern" | head -1 # Search for first occurrence
   cat <file> | grep -i "pattern" | tail -1 # Search for last occurrence

6.jq
----
.. code-block:: sh

   jq . --indent 4 File.json

7.Enable timestamp in history command
--------------------------------------
`From Linux Handbook <https://linuxhandbook.com/history-command-timestamp/?ref=lhb-linux-digest-newsletter>`_

.. code-block:: sh

   export HISTTIMEFORMAT="%F %T "

8.Search processes
-------------------
.. code-block:: sh

   pgrep testmac
   pgrep -i FIREFOX #case-insensitive
   ps aux | grep -i "testmac"

9.Redirect to different terminals
----------------------------------
.. code-block:: sh

   tty # which terminal
   python --version > /dev/pts/0
   node --version > /dev/pts/1

10.Create subshells
-------------------
.. code-block:: sh

   # goto build directory
   (cd bin; ./ULAKDU --gtest_filter="")

11.ACL
-------
`From Linux Handbook <https://linuxhandbook.com/chattr-command/?ref=lhb-linux-digest-newsletter>`_

.. code-block:: sh

   getfacl File.txt

.. autosummary::
   :toctree: generated