.. _vsphere_copy:


vsphere_copy - Copy a file to a vCenter datastore
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Upload files to a vCenter datastore




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
                <tr><td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The datacenter on the vCenter server that holds the datastore.</div>        </td></tr>
                <tr><td>datastore<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The datastore on the vCenter server to push files to.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The vCenter server on which the datastore is available.</div>        </td></tr>
                <tr><td>login<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The login name to authenticate on the vCenter server.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password to authenticate on the vCenter server.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The file to push to the datastore on the vCenter server.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The file to push to vCenter</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be set to <code>no</code> when no other option exists.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - vsphere_copy:
        host: vhost
        login: vuser
        password: vpass
        src: /some/local/file
        datacenter: DC1 Someplace
        datastore: datastore1
        path: some/remote/file
      transport: local
    - vsphere_copy:
        host: vhost
        login: vuser
        password: vpass
        src: /other/local/file
        datacenter: DC2 Someplace
        datastore: datastore2
        path: other/remote/file
      delegate_to: other_system


Notes
-----

.. note::
    - This module ought to be run from a system that can access vCenter directly and has the file to transfer. It can be the normal remote target or you can change it either by using ``transport: local`` or using ``delegate_to``.
    - Tested on vSphere 5.5



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
