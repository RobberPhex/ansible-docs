.. _sf_check_connections:


sf_check_connections - Check connectivity to MVIP and SVIP.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Used to test the management connection to the cluster.
* The test pings the MVIP and SVIP, and executes a simple API method to verify connectivity.


Requirements (on host that executes module)
-------------------------------------------

  * solidfire-sdk-python (1.1.0.92)


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
        <td><div>The hostname or IP address of the SolidFire cluster.</div>        </td></tr>
                <tr><td>mvip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Optionally, use to test connection of a different MVIP.</div><div>This is not needed to test the connection to the target cluster.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>skip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>svip</li><li>mvip</li></ul></td>
        <td><div>Skip checking connection to SVIP or MVIP.</div>        </td></tr>
                <tr><td>svip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Optionally, use to test connection of a different SVIP.</div><div>This is not needed to test the connection to the target cluster.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Please ensure that the user has the adequate permissions. For more information, please read the official documentation <a href='https://goo.gl/ddJa4Q'>https://goo.gl/ddJa4Q</a>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

       - name: Check connections to MVIP and SVIP
         sf_check_connections:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"


Notes
-----

.. note::
    - The modules prefixed with ``sf\_`` are built to support the SolidFire storage platform.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
