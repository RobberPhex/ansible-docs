.. _nxos_bgp:


nxos_bgp - Manages BGP configuration.
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages BGP configurations on NX-OS switches.




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
                <tr><td>asn<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>BGP autonomous system number. Valid values are String, Integer in ASPLAIN or ASDOT notation.</div>        </td></tr>
                <tr><td>bestpath_always_compare_med<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable MED comparison on paths from different autonomous systems.</div>        </td></tr>
                <tr><td>bestpath_aspath_multipath_relax<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable load sharing across the providers with different (but equal-length) AS paths.</div>        </td></tr>
                <tr><td>bestpath_compare_routerid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable comparison of router IDs for identical eBGP paths.</div>        </td></tr>
                <tr><td>bestpath_cost_community_ignore<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable Ignores the cost community for BGP best-path calculations.</div>        </td></tr>
                <tr><td>bestpath_med_confed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable enforcement of bestpath to do a MED comparison only between paths originated within a confederation.</div>        </td></tr>
                <tr><td>bestpath_med_missing_as_worst<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable assigns the value of infinity to received routes that do not carry the MED attribute, making these routes the least desirable.</div>        </td></tr>
                <tr><td>bestpath_med_non_deterministic<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable deterministic selection of the best MED pat from among the paths from the same autonomous system.</div>        </td></tr>
                <tr><td>cluster_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Route Reflector Cluster-ID.</div>        </td></tr>
                <tr><td>confederation_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Routing domain confederation AS.</div>        </td></tr>
                <tr><td>confederation_peers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AS confederation parameters.</div>        </td></tr>
                <tr><td>disable_policy_batching<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable the batching evaluation of prefix advertisement to all peers.</div>        </td></tr>
                <tr><td>disable_policy_batching_ipv4_prefix_list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable/Disable the batching evaluation of prefix advertisements to all peers with prefix list.</div>        </td></tr>
                <tr><td>disable_policy_batching_ipv6_prefix_list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable/Disable the batching evaluation of prefix advertisements to all peers with prefix list.</div>        </td></tr>
                <tr><td>enforce_first_as<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable enforces the neighbor autonomous system to be the first AS number listed in the AS path attribute for eBGP. On NX-OS, this property is only supported in the global BGP context.</div>        </td></tr>
                <tr><td>event_history_cli<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>size_small</li><li>size_medium</li><li>size_large</li><li>size_disable</li><li>default</li></ul></td>
        <td><div>Enable/Disable cli event history buffer.</div>        </td></tr>
                <tr><td>event_history_detail<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>size_small</li><li>size_medium</li><li>size_large</li><li>size_disable</li><li>default</li></ul></td>
        <td><div>Enable/Disable detail event history buffer.</div>        </td></tr>
                <tr><td>event_history_events<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>size_small</li><li>size_medium</li><li>size_large</li><li>size_disable</li><li>default</li></ul></td>
        <td><div>Enable/Disable event history buffer.</div>        </td></tr>
                <tr><td>event_history_periodic<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>size_small</li><li>size_medium</li><li>size_large</li><li>size_disable</li><li>default</li></ul></td>
        <td><div>Enable/Disable periodic event history buffer.</div>        </td></tr>
                <tr><td>fast_external_fallover<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable immediately reset the session if the link to a directly connected BGP peer goes down.  Only supported in the global BGP context.</div>        </td></tr>
                <tr><td>flush_routes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable flush routes in RIB upon controlled restart. On NX-OS, this property is only supported in the global BGP context.</div>        </td></tr>
                <tr><td>graceful_restart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable graceful restart.</div>        </td></tr>
                <tr><td>graceful_restart_helper<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable graceful restart helper mode.</div>        </td></tr>
                <tr><td>graceful_restart_timers_restart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Set maximum time for a restart sent to the BGP peer.</div>        </td></tr>
                <tr><td>graceful_restart_timers_stalepath_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Set maximum time that BGP keeps the stale routes from the restarting BGP peer.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                <tr><td>isolate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable isolate this router from BGP perspective.</div>        </td></tr>
                <tr><td>local_as<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Local AS number to be used within a VRF instance.</div>        </td></tr>
                <tr><td>log_neighbor_changes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable message logging for neighbor up/down event.</div>        </td></tr>
                <tr><td>maxas_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify Maximum number of AS numbers allowed in the AS-path attribute. Valid values are between 1 and 512.</div>        </td></tr>
                <tr><td>neighbor_down_fib_accelerate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable handle BGP neighbor down event, due to various reasons.</div>        </td></tr>
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
                <tr><td>reconnect_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The BGP reconnection interval for dropped sessions. Valid values are between 1 and 60.</div>        </td></tr>
                <tr><td>router_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Router Identifier (ID) of the BGP router VRF instance.</div>        </td></tr>
                <tr><td>shutdown<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Administratively shutdown the BGP protocol.</div>        </td></tr>
                <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Determines whether the config should be present or not on the device.</div>        </td></tr>
                <tr><td>suppress_fib_pending<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable advertise only routes programmed in hardware to peers.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error. NX-API can be slow to return on long-running commands (sh mac, sh bgp, etc).</div>        </td></tr>
                <tr><td>timer_bestpath_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify timeout for the first best path after a restart, in seconds.</div>        </td></tr>
                <tr><td>timer_bestpath_limit_always<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/Disable update-delay-always option.</div>        </td></tr>
                <tr><td>timer_bgp_hold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set BGP hold timer.</div>        </td></tr>
                <tr><td>timer_bgp_keepalive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set BGP keepalive timer.</div>        </td></tr>
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
                <tr><td>vrf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the VRF. The name 'default' is a valid VRF representing the global BGP.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Configure a simple ASN
      nxos_bgp:
          asn: 65535
          vrf: test
          router_id: 1.1.1.1
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

.. note::
    - ``state=absent`` removes the whole BGP ASN configuration when ``vrf=default`` or the whole VRF instance within the BGP process when using a different VRF.
    - Default when supported restores params default value.
    - Configuring global parmas is only permitted if ``vrf=default``.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
