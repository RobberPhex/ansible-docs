.. _na_cdot_svm:


na_cdot_svm - Manage NetApp cDOT svm
++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or destroy svm on NetApp cDOT


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
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the ONTAP instance.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the SVM to manage.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>root_volume<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Root volume of the SVM. Required when <code>state=present</code>.</div>        </td></tr>
                <tr><td>root_volume_aggregate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The aggregate on which the root volume will be created.</div><div>Required when <code>state=present</code>.</div>        </td></tr>
                <tr><td>root_volume_security_style<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>unix</li><li>ntfs</li><li>mixed</li><li>unified</li></ul></td>
        <td><div>Security Style of the root volume.</div><div>When specified as part of the vserver-create, this field represents the security style for the Vserver root volume.</div><div>When specified as part of vserver-get-iter call, this will return the list of matching Vservers.</div><div>Possible values are 'unix', 'ntfs', 'mixed'.</div><div>The 'unified' security style, which applies only to Infinite Volumes, cannot be applied to a Vserver's root volume.</div><div>Valid options are "unix" for NFS, "ntfs" for CIFS, "mixed" for Mixed, "unified" for Unified.</div><div>Required when <code>state=present</code></div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified SVM should exist or not.</div>        </td></tr>
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

    
        - name: Create SVM
          na_cdot_svm:
            state: present
            name: ansibleVServer
            root_volume: vol1
            root_volume_aggregate: aggr1
            root_volume_security_style: mixed
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
