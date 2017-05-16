.. _nxos_interface:


nxos_interface - Manages physical attributes of interfaces.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages physical attributes of interfaces of NX-OS switches.




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
    <td>admin_state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>up</td>
        <td><ul><li>up</li><li>down</li></ul></td>
        <td><div>Administrative state of the interface.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Interface description.</div></td></tr>
            <tr>
    <td>fabric_forwarding_anycast_gateway<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Associate SVI with anycast gateway under VLAN configuration mode.</div></td></tr>
            <tr>
    <td>interface<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Full name of interface, i.e. Ethernet1/1, port-channel10.</div></td></tr>
            <tr>
    <td>interface_type<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>loopback</li><li>portchannel</li><li>svi</li><li>nve</li></ul></td>
        <td><div>Interface type to be unconfigured from the device.</div></td></tr>
            <tr>
    <td>ip_forward<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li><li>disable</li></ul></td>
        <td><div>Enable/Disable ip forward feature on SVIs.</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>layer2</li><li>layer3</li></ul></td>
        <td><div>Manage Layer 2 or Layer 3 state of the interface.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>default</li></ul></td>
        <td><div>Specify desired state of the resource.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure an interface is a Layer 3 port and that it has the proper description
    - nxos_interface: interface=Ethernet1/1 description='Configured by Ansible' mode=layer3 host=68.170.147.165
    # Admin down an interface
    - nxos_interface: interface=Ethernet2/1 host=68.170.147.165 admin_state=down
    # Remove all loopback interfaces
    - nxos_interface: interface=loopback state=absent host=68.170.147.165
    # Remove all logical interfaces
    - nxos_interface: interface_type={{ item }} state=absent host={{ inventory_hostname }}
      with_items:
        - loopback
        - portchannel
        - svi
        - nve
    # Admin up all ethernet interfaces
    - nxos_interface: interface=ethernet host=68.170.147.165 admin_state=up
    # Admin down ALL interfaces (physical and logical)
    - nxos_interface: interface=all host=68.170.147.165 admin_state=down

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> end_state </td>
        <td> k/v pairs of switchport after module execution </td>
        <td align=center> always </td>
        <td align=center> dict or null </td>
        <td align=center> {'admin_state': 'down', 'description': 'None', 'ip_forward': 'enable', 'interface': 'port-channel101', 'type': 'portchannel', 'mode': 'layer2'} </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> check to see if a change was made on the device </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> command list sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['interface port-channel101', 'shutdown'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'admin_state': 'down'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing switchport </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center> {'admin_state': 'up', 'description': 'None', 'ip_forward': 'enable', 'interface': 'port-channel101', 'type': 'portchannel', 'mode': 'layer2'} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: This module is also used to create logical interfaces such as svis and loopbacks.
.. note:: Be cautious of platform specific idiosyncrasies. For example, when you default a loopback interface, the admin state toggles on certain versions of NX-OS.
.. note:: The :ref:`nxos_overlay_global <nxos_overlay_global>` ``anycast_gateway_mac`` attribute must be set before setting the ``fabric_forwarding_anycast_gateway`` property.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

