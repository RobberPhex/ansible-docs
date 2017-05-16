.. _vmware_portgroup:


vmware_portgroup - Create a VMware portgroup
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create a VMware portgroup


Requirements (on host that executes module)
-------------------------------------------

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
        <td><div>The hostname or IP address of the vSphere vCenter</div></td></tr>
            <tr>
    <td>network_policy<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Network policy specifies layer 2 security settings for a portgroup such as promiscuous mode, where guest adapter listens to all the packets, MAC address changes and forged transmits. Settings are promiscuous_mode, forged_transmits, mac_changes</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: pass, pwd<div></td></tr>
            <tr>
    <td>portgroup_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Portgroup name to add</div></td></tr>
            <tr>
    <td>switch_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>vSwitch to modify</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: user, admin<div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted</div></td></tr>
            <tr>
    <td>vlan_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>VLAN ID to assign to portgroup</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Example from Ansible playbook
    
        - name: Add Management Network VM Portgroup
          local_action:
            module: vmware_portgroup
            hostname: esxi_hostname
            username: esxi_username
            password: esxi_password
            switch_name: vswitch_name
            portgroup_name: portgroup_name
            vlan_id: vlan_id
    
        - name: Add Portgroup with Promiscuous Mode Enabled
          local_action:
            module: vmware_portgroup
            hostname: esxi_hostname
            username: esxi_username
            password: esxi_password
            switch_name: vswitch_name
            portgroup_name: portgroup_name
            network_policy:
                promiscuous_mode: True


Notes
-----

.. note:: Tested on vSphere 5.5


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

