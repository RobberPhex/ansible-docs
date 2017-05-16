.. _win_dotnet_ngen:


win_dotnet_ngen - Runs ngen to recompile DLLs after .NET  updates
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* After .NET framework is installed/updated, Windows will probably want to recompile things to optimise for the host.
* This happens via scheduled task, usually at some inopportune time.
* This module allows you to run this task on your own schedule, so you incur the CPU hit at some more convenient and controlled time.
* http://blogs.msdn.com/b/dotnet/archive/2013/08/06/wondering-why-mscorsvw-exe-has-high-cpu-usage-you-can-speed-it-up.aspx






Examples
--------

 ::

      # Run ngen tasks
      win_dotnet_ngen:


Notes
-----

.. note::
    - there are in fact two scheduled tasks for ngen but they have no triggers so aren't a problem
    - there's no way to test if they've been completed (?)
    - the stdout is quite likely to be several megabytes



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
