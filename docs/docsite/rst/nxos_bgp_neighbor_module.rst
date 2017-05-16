.. _nxos_bgp_neighbor:


nxos_bgp_neighbor - Manages BGP neighbors configurations.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages BGP neighbors configurations on NX-OS switches.




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
        <td><div>BGP autonomous system number. Valid values are string, Integer in ASPLAIN or ASDOT notation.</div>        </td></tr>
                <tr><td>capability_negotiation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Configure whether or not to negotiate capability with this neighbor.</div>        </td></tr>
                <tr><td>connected_check<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Configure whether or not to check for directly connected peer.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the neighbor.</div>        </td></tr>
                <tr><td>dynamic_capability<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Configure whether or not to enable dynamic capability.</div>        </td></tr>
                <tr><td>ebgp_multihop<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify multihop TTL for a remote peer. Valid values are integers between 2 and 255, or keyword 'default' to disable this property.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                <tr><td>local_as<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the local-as number for the eBGP neighbor. Valid values are String or Integer in ASPLAIN or ASDOT notation, or 'default', which means not to configure it.</div>        </td></tr>
                <tr><td>log_neighbor_changes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li><li>disable</li><li>inherit</li></ul></td>
        <td><div>Specify whether or not to enable log messages for neighbor up/down event.</div>        </td></tr>
                <tr><td>low_memory_exempt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Specify whether or not to shut down this neighbor under memory pressure.</div>        </td></tr>
                <tr><td>maximum_peers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify Maximum number of peers for this neighbor prefix Valid values are between 1 and 1000, or 'default', which does not impose the limit.</div>        </td></tr>
                <tr><td>neighbor<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Neighbor Identifier. Valid values are string. Neighbors may use IPv4 or IPv6 notation, with or without prefix length.</div>        </td></tr>
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
                <tr><td>pwd<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the password for neighbor. Valid value is string.</div>        </td></tr>
                <tr><td>pwd_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>3des</li><li>cisco_type_7</li></ul></td>
        <td><div>Specify the encryption type the password will use. Valid values are '3des' or 'cisco_type_7' encryption.</div>        </td></tr>
                <tr><td>remote_as<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify Autonomous System Number of the neighbor. Valid values are String or Integer in ASPLAIN or ASDOT notation, or 'default', which means not to configure it.</div>        </td></tr>
                <tr><td>remove_private_as<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li><li>disable</li><li>all</li><li>replace-as</li></ul></td>
        <td><div>Specify the config to remove private AS number from outbound updates. Valid values are 'enable' to enable this config, 'disable' to disable this config, 'all' to remove all private AS number, or 'replace-as', to replace the private AS number.</div>        </td></tr>
                <tr><td>shutdown<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Configure to administratively shutdown this neighbor.</div>        </td></tr>
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
                <tr><td>suppress_4_byte_as<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Configure to suppress 4-byte AS Capability.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error. NX-API can be slow to return on long-running commands (sh mac, sh bgp, etc).</div>        </td></tr>
                <tr><td>timers_holdtime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify holdtime timer value. Valid values are integers between 0 and 3600 in terms of seconds, or 'default', which is 180.</div>        </td></tr>
                <tr><td>timers_keepalive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify keepalive timer value. Valid values are integers between 0 and 3600 in terms of seconds, or 'default', which is 60.</div>        </td></tr>
                <tr><td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div>        </td></tr>
                <tr><td>transport_passive_only<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Specify whether or not to only allow passive connection setup. Valid values are 'true', 'false', and 'default', which defaults to 'false'. This property can only be configured when the neighbor is in 'ip' address format without prefix length. This property and the transport_passive_mode property are mutually exclusive.</div>        </td></tr>
                <tr><td>update_source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify source interface of BGP session and updates.</div>        </td></tr>
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
    <td>default</td>
        <td></td>
        <td><div>Name of the VRF. The name 'default' is a valid VRF representing the global bgp.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # create a new neighbor
    - nxos_bgp_neighbor:
        asn: 65535
        neighbor: 3.3.3.3
        local_as: 20
        remote_as: 30
        description: "just a description"
        update_source: Ethernet1/3
        shutdown: default
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
        <td> k/v pairs of BGP neighbor configuration after module execution </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'update_source': 'Ethernet1/3', 'maximum_peers': '', 'timers_holdtime': '180', 'local_as': '20', 'pwd_type': '', 'timers_keepalive': '60', 'dynamic_capability': True, 'vrf': 'default', 'shutdown': False, 'low_memory_exempt': False, 'log_neighbor_changes': '', 'remove_private_as': 'disable', 'suppress_4_byte_as': False, 'connected_check': False, 'remote_as': '30', 'ebgp_multihop': '', 'description': 'just a description', 'pwd': '', 'asn': '65535', 'transport_passive_only': False, 'capability_negotiation': False, 'neighbor': '3.3.3.3'} </td>
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
        <td align=center> ['router bgp 65535', 'neighbor 3.3.3.3', 'remote-as 30', 'update-source Ethernet1/3', 'description just a description', 'local-as 20'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'update_source': 'Ethernet1/3', 'remote_as': '30', 'shutdown': 'default', 'local_as': '20', 'vrf': 'default', 'neighbor': '3.3.3.3', 'asn': '65535', 'description': 'just a description'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing BGP neighbor configuration </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - ``state=absent`` removes the whole BGP neighbor configuration.
    - Default, where supported, restores params default value.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
