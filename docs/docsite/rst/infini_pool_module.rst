.. _infini_pool:


infini_pool - Create, Delete and Modify Pools on Infinibox
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module to creates, deletes or modifies pools on Infinibox.


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
        <td><div>Pool Name</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Infinibox User password.</div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Pool Physical Capacity in MB, GB or TB units. If pool size is not set on pool creation, size will be equal to 1TB. See examples.</div>        </td></tr>
                <tr><td>ssd_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enable/Disable SSD Cache on Pool</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Creates/Modifies Pool when present or removes when absent</div>        </td></tr>
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
                <tr><td>vsize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Pool Virtual Capacity in MB, GB or TB units. If pool vsize is not set on pool creation, Virtual Capacity will be equal to Physical Capacity. See examples.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Make sure pool foo exists. Set pool physical capacity to 10TB
      infini_pool:
        name: foo
        size: 10TB
        vsize: 10TB
        user: admin
        password: secret
        system: ibox001
    
    - name: Disable SSD Cache on pool
      infini_pool:
        name: foo
        ssd_cache: no
        user: admin
        password: secret
        system: ibox001


Notes
-----

.. note::
    - Infinibox Admin level access is required for pool modifications
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
