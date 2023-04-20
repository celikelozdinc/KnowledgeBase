gdb Cheat Sheet
===============

.. _gdb:

1.Catch Exceptions When Is Thrown
----------------------------------
.. code-block:: cpp

    catch throw //all exceptions, when thrown
    catch catch //all exceptions, when caught

2.Watch
-------
.. code-block:: cpp

    watch <variable> //pause the program if the watched variable has been changed

3.Print
-------
.. code-block:: sh

    (gdb) p ((archive_ctx*)0x2c606ff4)

    (gdb) p (ie->value.u._InitialUEMessage_IEs_id_NAS_PDU->data)
    $6 = (OSOCTET *) 0x7fffdc0046f0

    (gdb) p (nasPdu.data)
    $7 = (OSOCTET *) 0x7fffdc0047f8

    (gdb) select-frame 2
    p ueContextConfig.dlGlobalBwpIndex
    p ueContextConfig.ulGlobalBwpIndex

4.Memory Dump
-------------
`How to print unique_ptr? <https://medium.com/@steveyang_44123/gdb-how-to-print-pounique-ptr-745e868f0062>`_
`Investigate on coredump <https://www.cse.unsw.edu.au/~learn/debugging/modules/gdb_coredumps/>`_

.. code-block:: sh

    #23 : size of pointer
    (gdb) x/23bx (ie_nas->value.u._InitialUEMessage_IEs_id_NAS_PDU->data)
    0x7fffdc0046f0:	0x7e	0x00	0x41	0x79	0x00	0x0d	0x01	0x82
    0x7fffdc0046f8:	0xf6	0x61	0xf0	0xff	0x00	0x00	0x00	0x00
    0x7fffdc004700:	0x00	0x30	0x06	0x2e	0x02	0xe0	0xe0

    #23 : size of pointer
    (gdb) x/23bx (nasPdu.data)

    (gdb) select frame 2
    (gdb) info args
    (gdb) thread apply all bt
    (gdb) thread 8
    (gdb) whatis sctpInfo.socketIpc
    (gdb) p sctpInfo.socketIpc._M_ptr
    $3 = (std::__shared_ptr<_NR5G::IpcInterface, __gnu_cxx::_S_atomic>::element_type *) 0x2d3cd20
    (gdb) p *sctpInfo.socketIpc._M_ptr
    $4 = {_vptr.IpcInterface = 0x1741810 <vtable for _NR5G::CommonSocketReceiver+16>}

    #statik ömürlü nesnenin adresini print et
    (gdb) p &_NR5G::_CU::CUConfiguration::get_instance()
    #adresten itibaren 10 byte print et
    (gdb) x/10h <address>

5.Breakpoint
------------
.. code-block:: sh

    (gdb) b main
    (gdb) n -> sonraki satır
    (gdb) n -> sonraki satır
    (gdb) c -> sonraki breakpoint'e kadar devam etsin
    (gdb) s/step -> o satırdaki fonksiyonun içine girmek istiyoruz


6.Singleton Instance
--------------------
.. code-block:: sh

    (gdb) p _NR5G::_DU::MacCellContextManager::get_instance()._macCellContextList[0]._cellIndex
    (gdb) p _NR5G::_CU::CUConfiguration::get_instance()._localIp
    (gdb) p _NR5G::_CU::CUConfiguration::get_instance()._cellConfigurationList
    (gdb) p _NR5G::_CU::CUConfiguration::get_instance()._cellConfigurationList
    (gdb) p _NR5G::_CU::CUConfiguration::get_instance()._cellConfigurationList.size()
    (gdb) p *(_NR5G::_CU::CUConfiguration::get_instance()._cellConfigurationList._M_impl._M_start + 1)
    (gdb) p *(_NR5G::_CU::CUConfiguration::get_instance()._cellConfigurationList._M_impl._M_start)->get_pci()

7. info Subcommands
-------------------
`From medium <https://medium.com/@amit.kulkarni/gdb-basics-bf3407593285>`_

.. code-block:: sh

    (gdb) info args # arguments of function
    (gdb) info variables
    (gdb) help status   # lists a bunch of info commands
    (gdb) info frame    # list information about the current stack frame
    (gdb) info locals   # list local variable values of current stack frame
    (gdb) info args     # list argument values of current stack frame
    (gdb) print argv[0]
    (gdb) print argv[1]
    (gdb) info registers        # list register values
    (gdb) info breakpoints      # list status of all breakpoints
    (gdb) info breaks
    (gdb) info functions  # All defined functions



.. autosummary::
   :toctree: generated