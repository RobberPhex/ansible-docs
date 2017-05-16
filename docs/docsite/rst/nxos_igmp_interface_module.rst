.. _nxos_igmp_interface:


nxos_igmp_interface - Manages IGMP interface configuration.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages IGMP interface configuration settings.




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
                <tr><td>group_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the group membership timeout for IGMPv2. Values can range from 3 to 65,535 seconds. The default is 260 seconds.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                <tr><td>immediate_leave<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enables the device to remove the group entry from the multicast routing table immediately upon receiving a leave message for the group. Use this command to minimize the leave latency of IGMPv2 group memberships on a given IGMP interface because the device does not send group-specific queries. The default is disabled.</div>        </td></tr>
                <tr><td>interface<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The full interface name for IGMP configuration. e.g. <em>Ethernet1/2</em>.</div>        </td></tr>
                <tr><td>last_member_qrt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the query interval waited after sending membership reports before the software deletes the group state. Values can range from 1 to 25 seconds. The default is 1 second.</div>        </td></tr>
                <tr><td>last_member_query_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the number of times that the software sends an IGMP query in response to a host leave message. Values can range from 1 to 5. The default is 2.</div>        </td></tr>
                <tr><td>oif_prefix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configure a prefix for static outgoing interface (OIF).</div>        </td></tr>
                <tr><td>oif_routemap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configure a routemap for static outgoing interface (OIF).</div>        </td></tr>
                <tr><td>oif_source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configure a source for static outgoing interface (OIF).</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>nxapi</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>nxapi</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).</div>        </td></tr>
                <tr><td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Convenience method that allows all <em>nxos</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div>        </td></tr>
                <tr><td>querier_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the querier timeout that the software uses when deciding to take over as the querier. Values can range from 1 to 65535 seconds. The default is 255 seconds.</div>        </td></tr>
                <tr><td>query_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the frequency at which the software sends IGMP host query messages. Values can range from 1 to 18000 seconds. he default is 125 seconds.</div>        </td></tr>
                <tr><td>query_mrt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the response time advertised in IGMP queries. Values can range from 1 to 25 seconds. The default is 10 seconds.</div>        </td></tr>
                <tr><td>report_llg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Configures report-link-local-groups. Enables sending reports for groups in 224.0.0.0/24. Reports are always sent for nonlink local groups. By default, reports are not sent for link local groups.</div>        </td></tr>
                <tr><td>restart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Restart IGMP.</div>        </td></tr>
                <tr><td>robustness<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the robustness variable. Values can range from 1 to 7. The default is 2.</div>        </td></tr>
                <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                <tr><td>startup_query_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Query count used when the IGMP process starts up. The range is from 1 to 10. The default is 2.</div>        </td></tr>
                <tr><td>startup_query_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Query interval used when the IGMP process starts up. The range is from 1 to 18000. The default is 31.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>default</li></ul></td>
        <td><div>Manages desired state of the resource.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error. NX-API can be slow to return on long-running commands (sh mac, sh bgp, etc).</div>        </td></tr>
                <tr><td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div>        </td></tr>
                <tr><td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <code>transport=nxapi</code>, otherwise this value is ignored.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate either the CLI login or the nxapi authentication depending on which transport is used. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.  If the transport argument is not nxapi, this value is ignored.</div>        </td></tr>
                <tr><td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>2</li><li>3</li></ul></td>
        <td><div>IGMP version. It can be 2 or 3.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - nxos_igmp_interface:
        interface: ethernet1/32
        startup_query_interval: 30
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
        <td> k/v pairs of BGP configuration after module execution </td>
        <td align=center> always </td>
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
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'router_id': '1.1.1.1', 'asn': '65535', 'vrf': 'test'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing BGP configuration </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'router_id': '11.11.11.11', 'neighbor_down_fib_accelerate': False, 'confederation_peers': '', 'confederation_id': '', 'bestpath_compare_neighborid': False, 'local_as': '', 'bestpath_always_compare_med': False, 'bestpath_med_non_deterministic': False, 'cluster_id': '', 'vrf': 'test', 'graceful_restart_helper': False, 'timer_bgp_hold': '180', 'bestpath_aspath_multipath_relax': False, 'asn': '65535', 'timer_bestpath_limit': '', 'graceful_restart_timers_stalepath_time': '300', 'graceful_restart_timers_restart': '120', 'maxas_limit': '', 'bestpath_med_confed': False, 'log_neighbor_changes': False, 'timer_bgp_keepalive': '60', 'bestpath_cost_community_ignore': False, 'reconnect_interval': '60', 'suppress_fib_pending': False, 'bestpath_med_missing_as_worst': False, 'bestpath_compare_routerid': False, 'graceful_restart': True} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - When ``state=default``, supported params will be reset to a default state. These include ``version``, ``startup_query_interval``, ``startup_query_count``, ``robustness``, ``querier_timeout``, ``query_mrt``, ``query_interval``, ``last_member_qrt``, ``last_member_query_count``, ``group_timeout``, ``report_llg``, and ``immediate_leave``.
    - When ``state=absent``, all configs for ``oif_prefix``, ``oif_source``, and ``oif_routemap`` will be removed.
    - PIM must be enabled to use this module.
    - This module is for Layer 3 interfaces.
    - Route-map check not performed (same as CLI) check when configuring route-map with 'static-oif'
    - If restart is set to true with other params set, the restart will happen last, i.e. after the configuration takes place.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
