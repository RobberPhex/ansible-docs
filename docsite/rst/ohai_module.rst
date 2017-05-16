.. _ohai:


ohai - Returns inventory data from *Ohai*
+++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Similar to the :ref:`facter <facter>` module, this runs the *Ohai* discovery program (http://wiki.opscode.com/display/chef/Ohai) on the remote host and returns JSON inventory data. *Ohai* data is a bit more verbose and nested than *facter*.


Requirements (on host that executes module)
-------------------------------------------

  * ohai




Examples
--------

 ::

    # Retrieve (ohai) data from all Web servers and store in one-file per host
    ansible webservers -m ohai --tree=/tmp/ohaidata




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

