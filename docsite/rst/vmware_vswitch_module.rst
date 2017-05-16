.. _vmware_vswitch:


vmware_vswitch - Add a VMware Standard Switch to an ESXi host
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add a VMware Standard Switch to an ESXi host


Requirements
------------

  * python >= 2.6
  * PyVmomi


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
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname or IP address of the ESXi server</div></td></tr>
            <tr>
    <td>mtu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>MTU to configure on vswitch</div></td></tr>
            <tr>
    <td>nic_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>vmnic name to attach to vswitch</div></td></tr>
            <tr>
    <td>number_of_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>128</td>
        <td><ul></ul></td>
        <td><div>Number of port to configure on vswitch</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password of the ESXi server</div></br>
        <div style="font-size: small;">aliases: pass, pwd<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Add or remove the switch</div></td></tr>
            <tr>
    <td>switch_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>vSwitch name to add</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username of the ESXi server</div></br>
        <div style="font-size: small;">aliases: user, admin<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Example from Ansible playbook
    
        - name: Add a VMware vSwitch
          local_action:
            module: vmware_vswitch
            hostname: esxi_hostname
            username: esxi_username
            password: esxi_password
            switch_name: vswitch_name
            nic_name: vmnic_name
            mtu: 9000


Notes
-----

.. note:: Tested on vSphere 5.5


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

