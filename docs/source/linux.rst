Linux Cheat Sheet
=================

.. _linux:


0.HW Architecture
-------------------
`SSH Config File <https://linuxhandbook.com/ssh-config-file/>`_

.. code-block:: sh

   uname -m
   arch
   lscpu
   dpkg --print-architecture

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

   du -sh <source>
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
   find /path/to/search -type f -name "*.sh" -exec chmod +x '{}' +
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
   pgrep -l teams #process name
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
   (cd bin; echo $OLDPWD; ./ULAKDU --gtest_filter="")

11.ACL
-------
`From Linux Handbook <https://linuxhandbook.com/chattr-command/?ref=lhb-linux-digest-newsletter>`_

.. code-block:: sh

   getfacl File.txt

11.awk
-------
`Division on wc output <https://www.unix.com/unix-for-dummies-questions-and-answers/222915-division-wc-output.html>`_

.. code-block:: sh

   cat <file.txt> | wc -l | awk '{x=$1/2; print x}'

12.docker
----------------------------------
.. code-block:: sh

   docker builder du
   docker builder prune


13.tmux
--------
`A beginner's guide to tmux <https://medium.com/pragmatic-programmers/a-beginners-guide-to-tmux-7e6daa5c0154>`_
`How I Learned TMUX <https://medium.com/@hammad.ai/how-i-learned-tmux-became-a-workflow-ninja-7d33cc796793>`_

.. code-block:: sh

      creates several pseudo terminals from a single terminal
         (1)Launces a new tmux server
         (2)Creates a default session with a single Window
         (3)Attaches to it
      
      Ctrl + B = prefix (can also be customized)

      Detach from tmux session -> prefix + D
      Split window into 2 panes horizontally -> prefix + %
      Split window into 2 panes vertically -> prefix + ""
      Move between panes -> prefix + arrow keys
      Create new window -> prefix + C
      Move to next/previous window -> prefix + N/P
      Move to specific window by number -> prefix + (0,1,2)
      Rename window name -> prefix + rename-window newname
                         -> prefix + ,
      List all windwos -> prefix + w

      Attach to tmux session  -> tmux attach -t 0 (target session)
                              -> tmux a -t 0
      
      Ctrl B + [ -> copy mode
      Ctrl + W -> write to buffer
      Ctrl B + ] -> paste mode

      Create new sesion -> tmux new -s {SessionName}
      Enter command mode -> prefix + : (for example, customizing status bar)
         # set color for status bar
         set-option -g status-style bg=colour235,fg=yellow,dim
         set -g status-bg magenta #status bar background color
         set status-bg black  #Sets the background color of the status bar to black

         # set window title list colors
         set-window-option -g window-status-style fg=brightblue,bg=colour236,dim
         set -g window-status style bg=... #inactive window color
         
         # active window title colors
         set-window-option -g window-status-current-style fg=brightred,bg=colour236,bright
         setw window-status-current-style fg=yellow
         set -g window-status-current-style bg=...,fg=... #active window color
         setw -g window-status-current-style fg=black,bg=white
         
         set -g mouse #enabling mouse
         set-option -g status-justify centre
         set-window-option -g window-status-separator '     '


.. autosummary::
   :toctree: generated
