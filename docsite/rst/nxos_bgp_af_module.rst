.. _nxos_bgp_af:


nxos_bgp_af - Manages BGP Address-family configuration.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages BGP Address-family configurations on NX-OS switches.




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
    <td>additional_paths_install<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Install a backup path into the forwarding table and provide prefix independent convergence (PIC) in case of a PE-CE link failure.</div></td></tr>
            <tr>
    <td>additional_paths_receive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enables the receive capability of additional paths for all of the neighbors under this address family for which the capability has not been disabled.</div></td></tr>
            <tr>
    <td>additional_paths_selection<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the capability of selecting additional paths for a prefix. Valid values are a string defining the name of the route-map.</div></td></tr>
            <tr>
    <td>additional_paths_send<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enables the send capability of additional paths for all of the neighbors under this address family for which the capability has not been disabled.</div></td></tr>
            <tr>
    <td>advertise_l2vpn_evpn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Advertise evpn routes.</div></td></tr>
            <tr>
    <td>afi<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>ipv4</li><li>ipv6</li><li>vpnv4</li><li>vpnv6</li><li>l2vpn</li></ul></td>
        <td><div>Address Family Identifier.</div></td></tr>
            <tr>
    <td>asn<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>BGP autonomous system number. Valid values are String, Integer in ASPLAIN or ASDOT notation.</div></td></tr>
            <tr>
    <td>client_to_client<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Configure client-to-client route reflection.</div></td></tr>
            <tr>
    <td>dampen_igp_metric<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify dampen value for IGP metric-related changes, in seconds. Valid values are integer and keyword 'default'.</div></td></tr>
            <tr>
    <td>dampening_half_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify decay half-life in minutes for route-flap dampening. Valid values are integer and keyword 'default'.</div></td></tr>
            <tr>
    <td>dampening_max_suppress_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify max suppress time for route-flap dampening stable route. Valid values are integer and keyword 'default'.</div></td></tr>
            <tr>
    <td>dampening_reuse_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify route reuse time for route-flap dampening. Valid values are integer and keyword 'default'.</div></td></tr>
            <tr>
    <td>dampening_routemap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify route-map for route-flap dampening. Valid values are a string defining the name of the route-map.</div></td></tr>
            <tr>
    <td>dampening_state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable/disable route-flap dampening.</div></td></tr>
            <tr>
    <td>dampening_suppress_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify route suppress time for route-flap dampening. Valid values are integer and keyword 'default'.</div></td></tr>
            <tr>
    <td>default_information_originate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Default information originate.</div></td></tr>
            <tr>
    <td>default_metric<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets default metrics for routes redistributed into BGP. Valid values are Integer or keyword 'default'</div></td></tr>
            <tr>
    <td>distance_ebgp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets the administrative distance for eBGP routes. Valid values are Integer or keyword 'default'.</div></td></tr>
            <tr>
    <td>distance_ibgp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets the administrative distance for iBGP routes. Valid values are Integer or keyword 'default'.</div></td></tr>
            <tr>
    <td>distance_local<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets the administrative distance for local BGP routes. Valid values are Integer or keyword 'default'.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>inject_map<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An array of route-map names which will specify prefixes to inject. Each array entry must first specify the inject-map name, secondly an exist-map name, and optionally the copy-attributes keyword which indicates that attributes should be copied from the aggregate. For example [['lax_inject_map', 'lax_exist_map'], ['nyc_inject_map', 'nyc_exist_map', 'copy-attributes'], ['fsd_inject_map', 'fsd_exist_map']].</div></td></tr>
            <tr>
    <td>maximum_paths<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the maximum number of equal-cost paths for load sharing. Valid value is an integer in the range 1-64.</div></td></tr>
            <tr>
    <td>maximum_paths_ibgp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the maximum number of ibgp equal-cost paths for load sharing. Valid value is an integer in the range 1-64.</div></td></tr>
            <tr>
    <td>networks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Networks to configure. Valid value is a list of network prefixes to advertise. The list must be in the form of an array. Each entry in the array must include a prefix address and an optional route-map. For example [['10.0.0.0/16', 'routemap_LA'], ['192.168.1.1', 'Chicago'], ['192.168.2.0/24], ['192.168.3.0/24', 'routemap_NYC']].</div></td></tr>
            <tr>
    <td>next_hop_route_map<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configure a route-map for valid nexthops. Valid values are a string defining the name of the route-map.</div></td></tr>
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
    <td>redistribute<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of redistribute directives. Multiple redistribute entries are allowed. The list must be in the form of a nested array. the first entry of each array defines the source-protocol to redistribute from; the second entry defines a route-map name. A route-map is highly advised but may be optional on some platforms, in which case it may be omitted from the array list. For example [['direct', 'rm_direct'], ['lisp', 'rm_lisp']].</div></td></tr>
            <tr>
    <td>safi<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>unicast</li><li>multicast</li><li>evpn</li></ul></td>
        <td><div>Sub Address Family Identifier.</div></td></tr>
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
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Advertises only active routes to peers.</div></td></tr>
            <tr>
    <td>table_map<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Apply table-map to filter routes downloaded into URIB. Valid values are a string.</div></td></tr>
            <tr>
    <td>table_map_filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Filters routes rejected by the route-map and does not download them to the RIB.</div></td></tr>
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
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the VRF. The name 'default' is a valid VRF representing the global bgp.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # configure a simple address-family
    - nxos_bgp_af:
        asn: 65535
        vrf: TESTING
        afi: ipv4
        safi: unicast
        advertise_l2vpn_evpn: true
        state: present

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
        <td> k/v pairs of BGP AF configuration after module execution </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'table_map_filter': False, 'asn': '65535', 'dampening_max_suppress_time': '', 'additional_paths_send': False, 'safi': 'unicast', 'default_metric': '', 'additional_paths_install': False, 'client_to_client': True, 'dampen_igp_metric': '600', 'dampening_state': False, 'additional_paths_selection': '', 'additional_paths_receive': False, 'vrf': 'TESTING', 'suppress_inactive': False, 'distance_ebgp': '20', 'dampening_routemap': '', 'distance_ibgp': '200', 'redistribute': [], 'distance_local': '220', 'advertise_l2vpn_evpn': True, 'afi': 'ipv4', 'dampening_reuse_time': '', 'maximum_paths': '1', 'inject_map': [], 'networks': [], 'dampening_suppress_time': '', 'default_information_originate': False, 'next_hop_route_map': '', 'table_map': '', 'maximum_paths_ibgp': '1', 'dampening_half_time': ''} </td>
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
        <td align=center> ['router bgp 65535', 'vrf TESTING', 'address-family ipv4 unicast', 'advertise l2vpn evpn'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'afi': 'ipv4', 'asn': '65535', 'advertise_l2vpn_evpn': True, 'vrf': 'TESTING', 'safi': 'unicast'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing BGP AF configuration </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: ``state=absent`` removes the whole BGP ASN configuration
.. note:: Default, where supported, restores params default value.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

