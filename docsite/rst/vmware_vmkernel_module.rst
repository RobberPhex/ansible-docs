.. _vmware_vmkernel:


vmware_vmkernel - Create a VMware VMkernel Interface
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create a VMware VMkernel Interface


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
    <td>enable_ft<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enable the VMK interface for Fault Tolerance traffic</div></td></tr>
            <tr>
    <td>enable_mgmt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enable the VMK interface for Management traffic</div></td></tr>
            <tr>
    <td>enable_vmotion<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enable the VMK interface for vMotion traffic</div></td></tr>
            <tr>
    <td>enable_vsan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enable the VMK interface for VSAN traffic</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname or IP address of the ESXi Server</div></td></tr>
            <tr>
    <td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The IP Address for the VMK interface</div></td></tr>
            <tr>
    <td>mtu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The MTU for the VMK interface</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password of ESXi Server</div></br>
        <div style="font-size: small;">aliases: pass, pwd<div></td></tr>
            <tr>
    <td>portgroup_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the portgroup for the VMK interface</div></td></tr>
            <tr>
    <td>subnet_mask<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Subnet Mask for the VMK interface</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username of the ESXi Server</div></br>
        <div style="font-size: small;">aliases: user, admin<div></td></tr>
            <tr>
    <td>vland_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The VLAN ID for the VMK interface</div></td></tr>
            <tr>
    <td>vswitch_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the vswitch where to add the VMK interface</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example command from Ansible Playbook
    
    -  name: Add Management vmkernel port (vmk1)
       local_action:
          module: vmware_vmkernel
          hostname: esxi_hostname
          username: esxi_username
          password: esxi_password
          vswitch_name: vswitch_name
          portgroup_name: portgroup_name
          vlan_id: vlan_id
          ip_address: ip_address
          subnet_mask: subnet_mask
          enable_mgmt: True


Notes
-----

.. note:: Tested on vSphere 5.5


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

