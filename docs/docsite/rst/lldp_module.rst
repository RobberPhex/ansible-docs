.. _lldp:


lldp - get details reported by lldp
+++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Reads data out of lldpctl


Requirements (on host that executes module)
-------------------------------------------

  * lldpctl




Examples
--------

 ::

    # Retrieve switch/port information
     - name: Gather information from lldp
       lldp:
    
     - name: Print each switch/port
       debug:
        msg: "{{ lldp[item]['chassis']['name'] }} / {{ lldp[item]['port']['ifalias'] }}"
       with_items: "{{ lldp.keys() }}"
    
    # TASK: [Print each switch/port] ***********************************************************
    # ok: [10.13.0.22] => (item=eth2) => {"item": "eth2", "msg": "switch1.example.com / Gi0/24"}
    # ok: [10.13.0.22] => (item=eth1) => {"item": "eth1", "msg": "switch2.example.com / Gi0/3"}
    # ok: [10.13.0.22] => (item=eth0) => {"item": "eth0", "msg": "switch3.example.com / Gi0/3"}
    


Notes
-----

.. note::
    - Requires lldpd running and lldp enabled on switches



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
