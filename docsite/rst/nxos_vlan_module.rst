.. _nxos_vlan:


nxos_vlan - Manages VLAN resources and attributes
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages VLAN configurations on NX-OS switches




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
        <td><div>Manage the vlan admin state of the VLAN equivalent to shut/no shut in vlan config mode</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of VLAN</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>nxapi</em> transports. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_PASSWORD will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when buiding the connection to the remote device.  This value applies to either <em>cli</em> or <em>nxapi</em>.  The port value will default to the approriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convience method that allows all <span class='module'>nxos</span> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_SSH_KEYFILE will be used instead.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Manage the state of the resource</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td><ul></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div></td></tr>
            <tr>
    <td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <em>transport</em> argument is configured as nxapi.  If the transport argument is not nxapi, this value is ignored</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the usename to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate either the CLI login or the nxapi authentication depending on which transport is used. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_USERNAME will be used instead.</div></td></tr>
            <tr>
    <td>vlan_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>single vlan id</div></td></tr>
            <tr>
    <td>vlan_range<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>range of VLANs such as 2-10 or 2,5,10-15, etc.</div></td></tr>
            <tr>
    <td>vlan_state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>active</td>
        <td><ul><li>active</li><li>suspend</li></ul></td>
        <td><div>Manage the vlan operational state of the VLAN (equivalent to state {active | suspend} command</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a range of VLANs are not present on the switch
    - nxos_vlan: vlan_range="2-10,20,50,55-60,100-150" host={{ inventory_hostname }} username=cisco password=cisco state=absent transport=nxapi
    
    # Ensure VLAN 50 exists with the name WEB and is in the shutdown state
    - nxos_vlan: vlan_id=50 host={{ inventory_hostname }} admin_state=down name=WEB transport=nxapi username=cisco password=cisco
    
    # Ensure VLAN is NOT on the device
    - nxos_vlan: vlan_id=50 host={{ inventory_hostname }} state=absent transport=nxapi username=cisco password=cisco
    
    

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
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module (does not include vlan_id or vlan_range) </td>
        <td align=center> always </td>
        <td align=center> dict or null </td>
        <td align=center> {'vlan_state': 'suspend', 'admin_state': 'down', 'name': 'app_vlan'} </td>
    </tr>
            <tr>
        <td> existing_vlans_list </td>
        <td> list of existing VLANs on the switch prior to making changes </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['1', '2', '3', '4', '5', '20'] </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> check to see if a change was made on the device </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> end_state_vlans_list </td>
        <td> list of VLANs after the module is executed </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['1', '2', '3', '4', '5', '20', '100'] </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing vlan or null when using vlan_range </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'vlan_state': 'suspend', 'admin_state': 'down', 'name': 'app_vlan', 'vlan_id': '20'} </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state as sent in from the playbook </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> command string sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['vlan 20', 'vlan 55'] </td>
    </tr>
            <tr>
        <td> end_state </td>
        <td> k/v pairs of the VLAN after executing module or null when using vlan_range </td>
        <td align=center> always </td>
        <td align=center> dict or null </td>
        <td align=center> {'vlan_state': 'suspend', 'admin_state': 'down', 'name': 'app_vlan', 'vlan_id': '20'} </td>
    </tr>
            <tr>
        <td> proposed_vlans_list </td>
        <td> list of VLANs being proposed </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['100'] </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

