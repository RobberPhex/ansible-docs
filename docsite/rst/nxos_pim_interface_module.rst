.. _nxos_pim_interface:


nxos_pim_interface - Manages PIM interface configuration.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages PIM interface configuration settings.




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
    <td>border<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Configures interface to be a boundary of a PIM domain.</div></td></tr>
            <tr>
    <td>hello_auth_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Authentication for hellos on this interface.</div></td></tr>
            <tr>
    <td>hello_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Hello interval in milliseconds for this interface.</div></td></tr>
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
        <td><div>Full name of the interface such as Ethernet1/33.</div></td></tr>
            <tr>
    <td>jp_policy_in<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Policy for join-prune messages (inbound).</div></td></tr>
            <tr>
    <td>jp_policy_out<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Policy for join-prune messages (outbound).</div></td></tr>
            <tr>
    <td>jp_type_in<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>prefix</li><li>routemap</li></ul></td>
        <td><div>Type of policy mapped to <code>jp_policy_in</code>.</div></td></tr>
            <tr>
    <td>jp_type_out<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>prefix</li><li>routemap</li></ul></td>
        <td><div>Type of policy mapped to <code>jp_policy_out</code>.</div></td></tr>
            <tr>
    <td>neighbor_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures a neighbor policy for filtering adjacencies.</div></td></tr>
            <tr>
    <td>neighbor_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>prefix</li><li>routemap</li></ul></td>
        <td><div>Type of policy mapped to neighbor_policy.</div></td></tr>
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
    <td>sparse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/disable sparse-mode on the interface.</div></td></tr>
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
        <td><ul><li>present</li><li>default</li></ul></td>
        <td><div>Manages desired state of the resource.</div></td></tr>
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

    # ensure PIM is not running on the interface
    - nxos_pim_interface:
        interface: eth1/33
        state: absent
        host: {{ inventory_hostname }}
        username: {{ un }}
        password: {{ pwd }}
    
    # ensure the interface has pim-sm enabled with the appropriate priority and hello interval
    - nxos_pim_interface:
        interface: eth1/33
        dr_prio: 10
        hello_interval: 40
        state: present
        host: {{ inventory_hostname }}
        username: {{ un }}
        password: {{ pwd }}
    
    # ensure join-prune policies exist
    - nxos_pim_interface:
        interface: eth1/33
        jp_policy_in: JPIN
        jp_policy_out: JPOUT
        jp_type_in: routemap
        jp_type_out: routemap
        host: {{ inventory_hostname }}
        username: {{ un }}
        password: {{ pwd }}
    
    # ensure defaults are in place
    - nxos_pim_interface:
        interface: eth1/33
        state: default
        host: {{ inventory_hostname }}
        username: {{ un }}
        password: {{ pwd }}

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
        <td> k/v pairs of configuration after module execution </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'jp_bidir': False, 'dr_prio': '1', 'hello_interval': '30000', 'jp_policy_out': '1', 'jp_type_in': 'routemap', 'neighbor_type': 'routemap', 'neighbor_policy': 'test', 'sparse': True, 'isauth': False, 'jp_policy_in': 'JPIN', 'border': False, 'jp_type_out': None} </td>
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
        <td> command sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['interface eth1/33', 'ip pim neighbor-policy test', 'ip pim neighbor-policy test'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'interface': 'eth1/33', 'neighbor_type': 'routemap', 'neighbor_policy': 'test', 'sparse': True} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> ['k/v pairs of existing configuration'] </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center> {'jp_bidir': False, 'dr_prio': '1', 'hello_interval': '30000', 'jp_policy_out': '1', 'jp_type_in': 'routemap', 'neighbor_type': 'prefix', 'neighbor_policy': 'test1', 'sparse': True, 'isauth': False, 'jp_policy_in': 'JPIN', 'border': False, 'jp_type_out': None} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: When ``state=default``, supported params will be reset to a default state. These include ``dr_prio``, ``hello_auth_key``, ``hello_interval``, ``jp_policy_out``, ``jp_policy_in``, ``jp_type_in``, ``jp_type_out``, ``border``, ``neighbor_policy``, ``neighbor_type``.
.. note:: The ``hello_auth_key`` param is not idempotent.
.. note:: ``hello_auth_key`` only supports clear text passwords.
.. note:: When ``state=absent``, pim interface configuration will be set to defaults and pim-sm will be disabled on the interface.
.. note:: PIM must be enabled on the device to use this module.
.. note:: This module is for Layer 3 interfaces.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

