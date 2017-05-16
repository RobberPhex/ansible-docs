.. _nxos_overlay_global:


nxos_overlay_global - Configures anycast gateway MAC of the switch.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Configures anycast gateway MAC of the switch.




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
    <td>anycast_gateway_mac<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Anycast gateway mac of the switch.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
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

    - nxos_overlay_global:
        anycast_gateway_mac: "b.b.b"
        username: "{{ un }}"
        password: "{{ pwd }}"
        host: "{{ inventory_hostname }}"

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
        <td> k/v pairs of BGP configuration after module execution </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'router_id': '1.1.1.1', 'neighbor_down_fib_accelerate': False, 'confederation_peers': '', 'confederation_id': '', 'bestpath_compare_neighborid': False, 'local_as': '', 'bestpath_always_compare_med': False, 'bestpath_med_non_deterministic': False, 'cluster_id': '', 'vrf': 'test', 'graceful_restart_helper': False, 'timer_bgp_hold': '180', 'bestpath_aspath_multipath_relax': False, 'asn': '65535', 'timer_bestpath_limit': '', 'graceful_restart_timers_stalepath_time': '300', 'graceful_restart_timers_restart': '120', 'maxas_limit': '', 'bestpath_med_confed': False, 'log_neighbor_changes': False, 'timer_bgp_keepalive': '60', 'bestpath_cost_community_ignore': False, 'reconnect_interval': '60', 'suppress_fib_pending': False, 'bestpath_med_missing_as_worst': False, 'bestpath_compare_routerid': False, 'graceful_restart': True} </td>
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
        <td> commands sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['router bgp 65535', 'vrf test', 'router-id 1.1.1.1'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'router_id': '1.1.1.1', 'asn': '65535', 'vrf': 'test'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing BGP configuration </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'router_id': '11.11.11.11', 'neighbor_down_fib_accelerate': False, 'confederation_peers': '', 'confederation_id': '', 'bestpath_compare_neighborid': False, 'local_as': '', 'bestpath_always_compare_med': False, 'bestpath_med_non_deterministic': False, 'cluster_id': '', 'vrf': 'test', 'graceful_restart_helper': False, 'timer_bgp_hold': '180', 'bestpath_aspath_multipath_relax': False, 'asn': '65535', 'timer_bestpath_limit': '', 'graceful_restart_timers_stalepath_time': '300', 'graceful_restart_timers_restart': '120', 'maxas_limit': '', 'bestpath_med_confed': False, 'log_neighbor_changes': False, 'timer_bgp_keepalive': '60', 'bestpath_cost_community_ignore': False, 'reconnect_interval': '60', 'suppress_fib_pending': False, 'bestpath_med_missing_as_worst': False, 'bestpath_compare_routerid': False, 'graceful_restart': True} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Default restores params default value
.. note:: Supported MAC address format are "E.E.E", "EE-EE-EE-EE-EE-EE", "EE:EE:EE:EE:EE:EE" and "EEEE.EEEE.EEEE"


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

