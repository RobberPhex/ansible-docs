.. _xenserver_facts:


xenserver_facts - get facts reported on xenserver
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Reads data out of XenAPI, can be used instead of multiple xe commands.






Examples
--------

 ::

    - name: Gather facts from xenserver
      xenserver:
    
    - name: Print running VMs
      debug:
        msg: "{{ item }}"
      with_items: "{{ xs_vms.keys() }}"
      when: xs_vms[item]['power_state'] == "Running"
    
    # Which will print:
    #
    # TASK: [Print running VMs] ***********************************************************
    # skipping: [10.13.0.22] => (item=CentOS 4.7 (32-bit))
    # ok: [10.13.0.22] => (item=Control domain on host: 10.0.13.22) => {
    #     "item": "Control domain on host: 10.0.13.22",
    #     "msg": "Control domain on host: 10.0.13.22"
    # }





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
