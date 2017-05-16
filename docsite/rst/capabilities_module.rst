.. _capabilities:


capabilities - Manage Linux capabilities
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module manipulates files privileges using the Linux capabilities(7) system.




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
            <tr>
    <td>capability<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Desired capability to set (with operator and flags, if state is <code>present</code>) or remove (if state is <code>absent</code>)</div></br>
        <div style="font-size: small;">aliases: cap<div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the path to the file to be managed.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the entry should be present or absent in the file's capabilities.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set cap_sys_chroot+ep on /foo
    - capabilities: path=/foo capability=cap_sys_chroot+ep state=present
    
    # Remove cap_net_bind_service from /bar
    - capabilities: path=/bar capability=cap_net_bind_service state=absent


Notes
-----

.. note:: The capabilities system will automatically transform operators and flags into the effective set, so (for example, cap_foo=ep will probably become cap_foo+ep). This module does not attempt to determine the final operator and flags to compare, so you will want to ensure that your capabilities argument matches the final capabilities.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

