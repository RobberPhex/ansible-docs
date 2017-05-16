.. _facter:


facter - Runs the discovery program *facter* on the remote system
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Runs the *facter* discovery program (https://github.com/puppetlabs/facter) on the remote system, returning JSON data that can be useful for inventory purposes.


Requirements (on host that executes module)
-------------------------------------------

  * facter
  * ruby-json




Examples
--------

 ::

    # Example command-line invocation
    ansible www.example.net -m facter





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
