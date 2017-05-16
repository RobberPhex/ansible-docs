.. _win_dotnet_ngen:


win_dotnet_ngen - Runs ngen to recompile DLLs after .NET  updates
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

After .NET framework is installed/updated, Windows will probably want to recompile things to optimise for the host.
This happens via scheduled task, usually at some inopportune time.
This module allows you to run this task on your own schedule, so you incur the CPU hit at some more convenient and controlled time.
http://blogs.msdn.com/b/dotnet/archive/2013/08/06/wondering-why-mscorsvw-exe-has-high-cpu-usage-you-can-speed-it-up.aspx






Examples
--------

 ::

      # Run ngen tasks
      win_dotnet_ngen:


Notes
-----

.. note:: there are in fact two scheduled tasks for ngen but they have no triggers so aren't a problem
.. note:: there's no way to test if they've been completed (?)
.. note:: the stdout is quite likely to be several megabytes


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

