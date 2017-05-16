.. _openvswitch_port:


openvswitch_port - Manage Open vSwitch ports
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage Open vSwitch ports


Requirements
------------

  * ovs-vsctl


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
    <td>bridge<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of bridge to manage</div></td></tr>
            <tr>
    <td>external_ids<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary of external_ids applied to a port.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of port to manage on the bridge</div></td></tr>
            <tr>
    <td>set<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Set a single property on a port.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the port should exist</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td><div>How long to wait for ovs-vswitchd to respond</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Creates port eth2 on bridge br-ex
    - openvswitch_port: bridge=br-ex port=eth2 state=present
    
    # Creates port eth6 and set ofport equal to 6.
    - openvswitch_port: bridge=bridge-loop port=eth6 state=present
                        set Interface eth6 ofport_request=6
    
    # Assign interface id server1-vifeth6 and mac address 52:54:00:30:6d:11
    # to port vifeth6 and setup port to be managed by a controller.
    - openvswitch_port: bridge=br-int port=vifeth6 state=present
      args:
        external_ids:
          iface-id: "{{inventory_hostname}}-vifeth6"
          attached-mac: "52:54:00:30:6d:11"
          vm-id: "{{inventory_hostname}}"
          iface-status: "active"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

