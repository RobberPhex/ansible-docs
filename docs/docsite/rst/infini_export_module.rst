.. _infini_export:


infini_export - Create, Delete or Modify NFS Exports on Infinibox
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module creates, deletes or modifies NFS exports on Infinibox.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * infinisdk


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
                <tr><td>client_list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>All Hosts(*), RW, no_root_squash: True</td>
        <td></td>
        <td><div>List of dictionaries with client entries. See examples. Check infini_export_client module to modify individual NFS client entries for export.</div>        </td></tr>
                <tr><td>filesystem<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of exported file system.</div>        </td></tr>
                <tr><td>inner_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td></td>
        <td><div>Internal path of the export.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Export name. Should always start with <code>/</code>. (ex. name=/data)</div></br>
    <div style="font-size: small;">aliases: export, path<div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Infinibox User password.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Creates/Modifies export when present and removes when absent.</div>        </td></tr>
                <tr><td>system<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Infinibox Hostname or IPv4 Address.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Infinibox User username with sufficient priveledges ( see notes ).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Export bar filesystem under foo pool as /data
      infini_export:
        name: /data01
        filesystem: foo
        user: admin
        password: secret
        system: ibox001
    
    - name: Export and specify client list explicitly
      infini_export:
        name: /data02
        filesystem: foo
        client_list:
          - client: 192.168.0.2
            access: RW
            no_root_squash: True
          - client: 192.168.0.100
            access: RO
            no_root_squash: False
          - client: 192.168.0.10-192.168.0.20
            access: RO
            no_root_squash: False
        system: ibox001
        user: admin
        password: secret


Notes
-----

.. note::
    - This module requires infinisdk python library
    - You must set INFINIBOX_USER and INFINIBOX_PASSWORD environment variables if user and password arguments are not passed to the module directly
    - Ansible uses the infinisdk configuration file ``~/.infinidat/infinisdk.ini`` if no credentials are provided. See http://infinisdk.readthedocs.io/en/latest/getting_started.html



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
