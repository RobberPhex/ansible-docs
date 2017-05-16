.. _ping:


ping - Try to connect to host, verify a usable python and return ``pong`` on success.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

A trivial test module, this module always returns ``pong`` on successful contact. It does not make sense in playbooks, but it is useful from ``/usr/bin/ansible`` to verify the ability to login and that a usable python is configured.
This is NOT ICMP ping, this is just a trivial test module.






Examples
--------

 ::

    # Test we can logon to 'webservers' and execute python with json lib.
    ansible webservers -m ping




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

