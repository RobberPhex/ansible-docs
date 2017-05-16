.. _infini_export_client:


infini_export_client - Create, Delete or Modify NFS Client(s) for existing exports on Infinibox
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module creates, deletes or modifys NFS client(s) for existing exports on Infinibox.


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
                <tr><td>access_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>RW</td>
        <td><ul><li>RW</li><li>RO</li></ul></td>
        <td><div>Read Write or Read Only Access.</div>        </td></tr>
                <tr><td>client<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Client IP or Range. Ranges can be defined as follows 192.168.0.1-192.168.0.254.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>export<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the export.</div>        </td></tr>
                <tr><td>no_root_squash<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Don't squash root user to anonymous. Will be set to "no" on creation if not specified explicitly.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Infinibox User password.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Creates/Modifies client when present and removes when absent.</div>        </td></tr>
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

    - name: Make sure nfs client 10.0.0.1 is configured for export. Allow root access
      infini_export_client:
        client: 10.0.0.1
        access_mode: RW
        no_root_squash: yes
        export: /data
        user: admin
        password: secret
        system: ibox001
    
    - name: Add multiple clients with RO access. Squash root priviledges
      infini_export_client:
        client: "{{ item }}"
        access_mode: RO
        no_root_squash: no
        export: /data
        user: admin
        password: secret
        system: ibox001
      with_items:
        - 10.0.0.2
        - 10.0.0.3


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
