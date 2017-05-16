.. _ping:


ping - Try to connect to host, verify a usable python and return ``pong`` on success.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* A trivial test module, this module always returns ``pong`` on successful contact. It does not make sense in playbooks, but it is useful from ``/usr/bin/ansible`` to verify the ability to login and that a usable python is configured.
* This is NOT ICMP ping, this is just a trivial test module.






Examples
--------

 ::

    # Test we can logon to 'webservers' and execute python with json lib.
    ansible webservers -m ping





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
