.. _infini_fs:


infini_fs - Create, Delete or Modify filesystems on Infinibox
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module creates, deletes or modifies filesystems on Infinibox.


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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>File system name.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Infinibox User password.</div>        </td></tr>
                <tr><td>pool<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Pool that will host file system.</div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>File system size in MB, GB or TB units. See examples.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Creates/Modifies file system when present or removes when absent.</div>        </td></tr>
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

    - name: Create new file system named foo under pool named bar
      infini_fs:
        name: foo
        size: 1TB
        pool: bar
        state: present
        user: admin
        password: secret
        system: ibox001


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
