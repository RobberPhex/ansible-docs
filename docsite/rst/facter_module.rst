.. _facter:


facter - Runs the discovery program *facter* on the remote system
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Runs the *facter* discovery program (https://github.com/puppetlabs/facter) on the remote system, returning JSON data that can be useful for inventory purposes.


Requirements (on host that executes module)
-------------------------------------------

  * facter
  * ruby-json




Examples
--------

 ::

    # Example command-line invocation
    ansible www.example.net -m facter




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

