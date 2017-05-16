.. _na_cdot_volume:


na_cdot_volume - Manage NetApp cDOT volumes
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or destroy volumes on NetApp cDOT


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
                <tr><td>aggregate_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the aggregate the flexvol should exist on. Required when <code>state=present</code>.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the ONTAP instance.</div>        </td></tr>
                <tr><td>infinite<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>False</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set True if the volume is an Infinite Volume.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the lun to manage.</div>        </td></tr>
                <tr><td>online<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Whether the specified volume is online, or not.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The size of the volume in (size_unit). Required when <code>state=present</code>.</div>        </td></tr>
                <tr><td>size_unit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>gb</td>
        <td><ul><li>bytes</li><li>b</li><li>kb</li><li>mb</li><li>gb</li><li>tb</li><li>pb</li><li>eb</li><li>zb</li><li>yb</li></ul></td>
        <td><div>The unit used to interpret the size parameter.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified volume should exist or not.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This can be a Cluster-scoped or SVM-scoped account, depending on whether a Cluster-level or SVM-level API is required. For more information, please read the documentation <a href='https://goo.gl/BRu78Z'>https://goo.gl/BRu78Z</a>.</div>        </td></tr>
                <tr><td>vserver<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>Name of the vserver to use.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
        - name: Create FlexVol
          na_cdot_volume:
            state: present
            name: ansibleVolume
            infinite: False
            aggregate_name: aggr1
            size: 20
            size_unit: mb
            vserver: ansibleVServer
            hostname: "{{ netapp_hostname }}"
            username: "{{ netapp_username }}"
            password: "{{ netapp_password }}"
    
        - name: Make FlexVol offline
          na_cdot_volume:
            state: present
            name: ansibleVolume
            infinite: False
            online: False
            vserver: ansibleVServer
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
