.. _nxos_ospf_vrf:


nxos_ospf_vrf - Manages a VRF for an OSPF router.
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages a VRF for an OSPF router.




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
    <td>auto_cost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the reference bandwidth used to assign OSPF cost. Valid values are an integer, in Mbps, or the keyword 'default'.</div></td></tr>
            <tr>
    <td>default_metric<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the default Metric value. Valid values are an integer or the keyword 'default'.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>log_adjacency<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>log</li><li>detail</li><li>default</li></ul></td>
        <td><div>Controls the level of log messages generated whenever a neighbor changes state. Valid values are 'log', 'detail', and 'default'.</div></td></tr>
            <tr>
    <td>ospf<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the OSPF instance.</div></td></tr>
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
    <td>router_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Router Identifier (ID) of the OSPF router VRF instance.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div></td></tr>
            <tr>
    <td>timer_throttle_lsa_hold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the hold interval for rate-limiting Link-State Advertisement (LSA) generation. Valid values are an integer, in milliseconds, or the keyword 'default'.</div></td></tr>
            <tr>
    <td>timer_throttle_lsa_max<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the max interval for rate-limiting Link-State Advertisement (LSA) generation. Valid values are an integer, in milliseconds, or the keyword 'default'.</div></td></tr>
            <tr>
    <td>timer_throttle_lsa_start<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the start interval for rate-limiting Link-State Advertisement (LSA) generation. Valid values are an integer, in milliseconds, or the keyword 'default'.</div></td></tr>
            <tr>
    <td>timer_throttle_spf_hold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify minimum hold time between Shortest Path First (SPF) calculations. Valid values are an integer, in milliseconds, or the keyword 'default'.</div></td></tr>
            <tr>
    <td>timer_throttle_spf_max<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the maximum wait time between Shortest Path First (SPF) calculations. Valid values are an integer, in milliseconds, or the keyword 'default'.</div></td></tr>
            <tr>
    <td>timer_throttle_spf_start<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify initial Shortest Path First (SPF) schedule delay. Valid values are an integer, in milliseconds, or the keyword 'default'.</div></td></tr>
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
            <tr>
    <td>vrf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default</td>
        <td><ul></ul></td>
        <td><div>Name of the resource instance. Valid value is a string. The name 'default' is a valid VRF representing the global OSPF.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - nxos_ospf_vrf:
        ospf: 1
        timer_throttle_spf_start: 50
        timer_throttle_spf_hold: 1000
        timer_throttle_spf_max: 2000
        timer_throttle_lsa_start: 60
        timer_throttle_lsa_hold: 1100
        timer_throttle_lsa_max: 3000
        vrf: test
        state: present
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
        <td> k/v pairs of configuration after module execution </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'router_id': '', 'timer_throttle_lsa_max': '3000', 'timer_throttle_spf_max': '2000', 'timer_throttle_lsa_hold': '1100', 'default_metric': '', 'log_adjacency': '', 'timer_throttle_lsa_start': '60', 'vrf': 'test', 'auto_cost': '40000', 'timer_throttle_spf_start': '50', 'ospf': '1', 'timer_throttle_spf_hold': '1000'} </td>
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
        <td align=center> ['router ospf 1', 'vrf test', 'timers throttle lsa 60 1100 3000', 'timers throttle spf 50 1000 2000'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'timer_throttle_lsa_max': '3000', 'timer_throttle_spf_max': '2000', 'timer_throttle_lsa_hold': '1100', 'timer_throttle_lsa_start': '60', 'vrf': 'test', 'timer_throttle_spf_start': '50', 'ospf': '1', 'timer_throttle_spf_hold': '1000'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing configuration </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'router_id': '', 'timer_throttle_lsa_max': '5000', 'timer_throttle_spf_max': '5000', 'timer_throttle_lsa_hold': '5000', 'default_metric': '', 'log_adjacency': '', 'timer_throttle_lsa_start': '0', 'vrf': 'test', 'auto_cost': '40000', 'timer_throttle_spf_start': '200', 'ospf': '1', 'timer_throttle_spf_hold': '1000'} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Value *default* restores params default value, if any. Otherwise it removes the existing param configuration.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

