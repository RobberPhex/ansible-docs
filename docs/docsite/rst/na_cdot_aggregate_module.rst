.. _na_cdot_aggregate:


na_cdot_aggregate - Manage NetApp cDOT aggregates.
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or destroy aggregates on NetApp cDOT.


Requirements (on host that executes module)
-------------------------------------------

  * A physical or virtual clustered Data ONTAP system. The modules were developed with Clustered Data ONTAP 8.3
  * Ansible 2.2
  * netapp-lib (2015.9.25). Install using 'pip install netapp-lib'


Options
-------

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                <tr><td>disk_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of disks to place into the aggregate, including parity disks.</div><div>The disks in this newly-created aggregate come from the spare disk pool.</div><div>The smallest disks in this pool join the aggregate first, unless the <code>disk-size</code> argument is provided.</div><div>Either <code>disk-count</code> or <code>disks</code> must be supplied. Range [0..2^31-1].</div><div>Required when <code>state=present</code>.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the ONTAP instance.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the aggregate to manage.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified aggregate should exist or not.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This can be a Cluster-scoped or SVM-scoped account, depending on whether a Cluster-level or SVM-level API is required. For more information, please read the documentation <a href='https://goo.gl/BRu78Z'>https://goo.gl/BRu78Z</a>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Manage Aggregates
      na_cdot_aggregate:
        state: present
        name: ansibleAggr
        disk_count: 1
        hostname: "{{ netapp_hostname }}"
        username: "{{ netapp_username }}"
        password: "{{ netapp_password }}"
    
    - name: Manage Aggregates
      na_cdot_aggregate:
        state: present
        name: ansibleAggr
        hostname: "{{ netapp_hostname }}"
        username: "{{ netapp_username }}"
        password: "{{ netapp_password }}"


Notes
-----

.. note::
    - The modules prefixed with ``netapp\_cdot`` are built to support the ONTAP storage platform.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
