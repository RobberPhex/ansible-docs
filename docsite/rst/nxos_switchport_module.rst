.. _nxos_switchport:


nxos_switchport - Manages Layer 2 switchport interfaces.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages Layer 2 interfaces




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
    <td>access_vlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If <code>mode=access</code>, used as the access VLAN ID.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>interface<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Full name of the interface, i.e. Ethernet1/1.</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>access</li><li>trunk</li></ul></td>
        <td><div>Mode for the Layer 2 port.</div></td></tr>
            <tr>
    <td>native_vlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If <code>mode=trunk</code>, used as the trunk native VLAN ID.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>nxapi</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>nxapi</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convenience method that allows all <em>nxos</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>unconfigured</li></ul></td>
        <td><div>Manage the state of the resource.</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td><ul></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div></td></tr>
            <tr>
    <td>trunk_allowed_vlans<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>if <code>mode=trunk</code>, these are the only VLANs that will be configured on the trunk, i.e. "2-10,15".</div></td></tr>
            <tr>
    <td>trunk_vlans<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If <code>mode=trunk</code>, used as the VLAN range to ADD or REMOVE from the trunk.</div></br>
        <div style="font-size: small;">aliases: trunk_add_vlans<div></td></tr>
            <tr>
    <td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <code>transport=nxapi</code>, otherwise this value is ignored.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate either the CLI login or the nxapi authentication depending on which transport is used. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # ENSURE Eth1/5 is in its default switchport state
    - nxos_switchport: interface=eth1/5 state=unconfigured host={{ inventory_hostname }}
    # ENSURE Eth1/5 is configured for access vlan 20
    - nxos_switchport: interface=eth1/5 mode=access access_vlan=20 host={{ inventory_hostname }}
    # ENSURE Eth1/5 only has vlans 5-10 as trunk vlans
    - nxos_switchport: interface=eth1/5 mode=trunk native_vlan=10 trunk_vlans=5-10 host={{ inventory_hostname }}
    # Ensure eth1/5 is a trunk port and ensure 2-50 are being tagged (doesn't mean others aren't also being tagged)
    - nxos_switchport: interface=eth1/5 mode=trunk native_vlan=10 trunk_vlans=2-50 host={{ inventory_hostname }}
    # Ensure these VLANs are not being tagged on the trunk
    - nxos_switchport: interface=eth1/5 mode=trunk trunk_vlans=51-4094 host={{ inventory_hostname }} state=absent

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
        <td align=center> {'native_vlan': '1', 'access_vlan': '10', 'switchport': 'Enabled', 'access_vlan_name': 'VLAN0010', 'trunk_vlans': '1-4094', 'mode': 'access', 'interface': 'Ethernet1/5', 'native_vlan_name': 'default'} </td>
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
        <td> command string sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['interface eth1/5', 'switchport access vlan 20'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'interface': 'eth1/5', 'access_vlan': '10', 'mode': 'access'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing switchport </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center> {'native_vlan': '1', 'access_vlan': '10', 'switchport': 'Enabled', 'access_vlan_name': 'VLAN0010', 'trunk_vlans': '1-4094', 'mode': 'access', 'interface': 'Ethernet1/5', 'native_vlan_name': 'default'} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: When ``state=absent``, VLANs can be added/removed from trunk links and the existing access VLAN can be 'unconfigured' to just having VLAN 1 on that interface.
.. note:: When working with trunks VLANs the keywords add/remove are always sent in the `switchport trunk allowed vlan` command. Use verbose mode to see commands sent.
.. note:: When ``state=unconfigured``, the interface will result with having a default Layer 2 interface, i.e. vlan 1 in access mode.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

