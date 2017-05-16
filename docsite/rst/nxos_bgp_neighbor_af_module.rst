.. _nxos_bgp_neighbor_af:


nxos_bgp_neighbor_af - Manages BGP address-family's neighbors configuration.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages BGP address-family's neighbors configurations on NX-OS switches.




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
    <td>additional_paths_receive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li><li>disable</li><li>inherit</li></ul></td>
        <td><div>Valid values are enable for basic command enablement; disable for disabling the command at the neighbor af level (it adds the disable keyword to the basic command); and inherit to remove the command at this level (the command value is inherited from a higher BGP layer).</div></td></tr>
            <tr>
    <td>additional_paths_send<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li><li>disable</li><li>inherit</li></ul></td>
        <td><div>Valid values are enable for basic command enablement; disable for disabling the command at the neighbor af level (it adds the disable keyword to the basic command); and inherit to remove the command at this level (the command value is inherited from a higher BGP layer).</div></td></tr>
            <tr>
    <td>advertise_map_exist<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Conditional route advertisement. This property requires two route maps, an advertise-map and an exist-map. Valid values are an array specifying both the advertise-map name and the exist-map name, or simply 'default' e.g. ['my_advertise_map', 'my_exist_map']. This command is mutually exclusive with the advertise_map_non_exist property.</div></td></tr>
            <tr>
    <td>advertise_map_non_exist<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Conditional route advertisement. This property requires two route maps, an advertise-map and an exist-map. Valid values are an array specifying both the advertise-map name and the non-exist-map name, or simply 'default' e.g. ['my_advertise_map', 'my_non_exist_map']. This command is mutually exclusive with the advertise_map_exist property.</div></td></tr>
            <tr>
    <td>afi<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>ipv4</li><li>ipv6</li><li>vpnv4</li><li>vpnv6</li><li>l2vpn</li></ul></td>
        <td><div>Address Family Identifier.</div></td></tr>
            <tr>
    <td>allowas_in<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Activate allowas-in property</div></td></tr>
            <tr>
    <td>allowas_in_max<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optional max-occurrences value for allowas_in. Valid values are an integer value or 'default'. Can be used independently or in conjunction with allowas_in.</div></td></tr>
            <tr>
    <td>as_override<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Activate the as-override feature.</div></td></tr>
            <tr>
    <td>asn<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>BGP autonomous system number. Valid values are String, Integer in ASPLAIN or ASDOT notation.</div></td></tr>
            <tr>
    <td>default_originate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Activate the default-originate feature.</div></td></tr>
            <tr>
    <td>default_originate_route_map<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optional route-map for the default_originate property. Can be used independently or in conjunction with <code>default_originate</code>. Valid values are a string defining a route-map name, or 'default'.</div></td></tr>
            <tr>
    <td>filter_list_in<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Valid values are a string defining a filter-list name, or 'default'.</div></td></tr>
            <tr>
    <td>filter_list_out<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Valid values are a string defining a filter-list name, or 'default'.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>max_prefix_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optional restart interval. Valid values are an integer. Requires max_prefix_limit.</div></td></tr>
            <tr>
    <td>max_prefix_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>maximum-prefix limit value. Valid values are an integer value or 'default'.</div></td></tr>
            <tr>
    <td>max_prefix_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optional threshold percentage at which to generate a warning. Valid values are an integer value. Requires max_prefix_limit.</div></td></tr>
            <tr>
    <td>max_prefix_warning<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Optional warning-only keyword. Requires max_prefix_limit.</div></td></tr>
            <tr>
    <td>neighbor<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Neighbor Identifier. Valid values are string. Neighbors may use IPv4 or IPv6 notation, with or without prefix length.</div></td></tr>
            <tr>
    <td>next_hop_self<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Activate the next-hop-self feature.</div></td></tr>
            <tr>
    <td>next_hop_third_party<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Activate the next-hop-third-party feature.</div></td></tr>
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
    <td>prefix_list_in<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Valid values are a string defining a prefix-list name, or 'default'.</div></td></tr>
            <tr>
    <td>prefix_list_out<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Valid values are a string defining a prefix-list name, or 'default'.</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convenience method that allows all <em>nxos</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>route_map_in<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Valid values are a string defining a route-map name, or 'default'.</div></td></tr>
            <tr>
    <td>route_map_out<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Valid values are a string defining a route-map name, or 'default'.</div></td></tr>
            <tr>
    <td>route_reflector_client<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Router reflector client.</div></td></tr>
            <tr>
    <td>safi<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>unicast</li><li>multicast</li><li>evpn</li></ul></td>
        <td><div>Sub Address Family Identifier.</div></td></tr>
            <tr>
    <td>send_community<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>none</li><li>both</li><li>extended</li><li>standard</li><li>default</li></ul></td>
        <td><div>send-community attribute.</div></td></tr>
            <tr>
    <td>soft_reconfiguration_in<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li><li>always</li><li>inherit</li></ul></td>
        <td><div>Valid values are 'enable' for basic command enablement; 'always' to add the always keyword to the basic command; and 'inherit' to remove the command at this level (the command value is inherited from a higher BGP layer).</div></td></tr>
            <tr>
    <td>soo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Site-of-origin. Valid values are a string defining a VPN extcommunity or 'default'.</div></td></tr>
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
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Determines whether the config should be present or not on the device.</div></td></tr>
            <tr>
    <td>suppress_inactive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li><li>default</li></ul></td>
        <td><div>suppress-inactive feature.</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td><ul></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div></td></tr>
            <tr>
    <td>unsuppress_map<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>unsuppress-map. Valid values are a string defining a route-map name or 'default'.</div></td></tr>
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
        <td><div>Name of the VRF. The name 'default' is a valid VRF representing the global bgp.</div></td></tr>
            <tr>
    <td>weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Weight value. Valid values are an integer value or 'default'.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    configure RR client
    - nxos_bgp_neighbor_af:
        asn: 65535
        neighbor: '3.3.3.3'
        afi: ipv4
        safi: unicast
        route_reflector_client: true
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
        <td align=center> {'default_originate': False, 'route_reflector_client': True, 'additional_paths_send': 'inherit', 'soo': '', 'additional_paths_receive': 'inherit', 'suppress_inactive': False, 'unsuppress_map': '', 'prefix_list_out': '', 'as_override': False, 'filter_list_out': '', 'afi': 'ipv4', 'allowas_in': False, 'max_prefix_warning': '', 'max_prefix_threshold': '', 'advertise_map_non_exist': [], 'default_originate_route_map': '', 'send_community': '', 'safi': 'unicast', 'filter_list_in': '', 'weight': '', 'vrf': 'default', 'max_prefix_limit': '', 'asn': '65535', 'route_map_in': '', 'soft_reconfiguration_in': 'inherit', 'max_prefix_interval': '', 'route_map_out': '', 'next_hop_self': False, 'prefix_list_in': '', 'neighbor': '3.3.3.3', 'next_hop_third_party': True, 'advertise_map_exist': [], 'allowas_in_max': ''} </td>
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
        <td align=center> ['router bgp 65535', 'neighbor 3.3.3.3', 'address-family ipv4 unicast', 'route-reflector-client'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'route_reflector_client': True, 'afi': 'ipv4', 'neighbor': '3.3.3.3', 'safi': 'unicast', 'asn': '65535', 'vrf': 'default'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing configuration </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: ``state=absent`` removes the whole BGP address-family's neighbor configuration.
.. note:: Default, when supported, removes properties
.. note:: In order to default maximum-prefix configuration, only ``max_prefix_limit=default`` is needed.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

