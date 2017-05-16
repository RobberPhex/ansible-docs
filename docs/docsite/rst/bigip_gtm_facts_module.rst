.. _bigip_gtm_facts:


bigip_gtm_facts - Collect facts from F5 BIG-IP GTM devices.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Collect facts from F5 BIG-IP GTM devices.


Requirements (on host that executes module)
-------------------------------------------

  * f5-sdk


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
                <tr><td>filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Perform regex filter of response. Filtering is done on the name of the resource. Valid filters are anything that can be provided to Python's <code>re</code> module.</div>        </td></tr>
                <tr><td>include<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>pool</li><li>wide_ip</li><li>virtual_server</li></ul></td>
        <td><div>Fact category to collect</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password for the user account used to connect to the BIG-IP. This option can be omitted if the environment variable <code>F5_PASSWORD</code> is set.</div>        </td></tr>
                <tr><td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The BIG-IP host. This option can be omitted if the environment variable <code>F5_SERVER</code> is set.</div>        </td></tr>
                <tr><td>server_port<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>The BIG-IP server port. This option can be omitted if the environment variable <code>F5_SERVER_PORT</code> is set.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username to connect to the BIG-IP with. This user must have administrative privileges on the device. This option can be omitted if the environment variable <code>F5_USER</code> is set.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. This option can be omitted if the environment variable <code>F5_VALIDATE_CERTS</code> is set.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Get pool facts
      bigip_gtm_facts:
          server: "lb.mydomain.com"
          user: "admin"
          password: "secret"
          include: "pool"
          filter: "my_pool"
      delegate_to: localhost

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
        <td> virtual_server </td>
        <td> Contains the virtual server enabled and availability status, and address </td>
        <td align=center> changed </td>
        <td align=center> dict </td>
        <td align=center> {'virtual_server': [{'product': 'single-bigip', 'virtual_servers': [{'limit_max_pps_status': 'disabled', 'name': 'jsdfhsd', 'destination': '10.10.10.10:0', 'enabled': 'True', 'translation_address': 'none', 'limit_max_pps': '0', 'limit_max_bps': '0', 'limit_max_bps_status': 'disabled', 'limit_max_connections': '0', 'limit_max_connections_status': 'disabled', 'full_path': 'jsdfhsd', 'translation_port': '0'}], 'addresses': [{'translation': 'none', 'name': '10.10.10.10', 'device_name': '/Common/qweqwe'}], 'datacenter': '/Common/xfxgh', 'limit_cpu_usage': '0', 'expose_route_domains': 'no', 'virtual_server_discovery': 'disabled', 'iq_allow_snmp': 'yes', 'iq_allow_service_check': 'yes', 'limit_max_bps_status': 'disabled', 'limit_max_connections': '0', 'limit_cpu_usage_status': 'disabled', 'limit_max_pps_status': 'disabled', 'link_discovery': 'disabled', 'iq_allow_path': 'yes', 'monitor': '/Common/bigip ', 'limit_mem_avail_status': 'disabled', 'limit_mem_avail': '0', 'partition': 'Common', 'enabled': 'True', 'name': 'qweqwe', 'limit_max_pps': '0', 'limit_max_bps': '0', 'limit_max_connections_status': 'disabled', 'full_path': '/Common/qweqwe'}]} </td>
    </tr>
            <tr>
        <td> wide_ip </td>
        <td> Contains the lb method for the wide ip and the pools that are within the wide ip. </td>
        <td align=center> changed </td>
        <td align=center> dict </td>
        <td align=center> {'wide_ip': [{'pool_lb_mode': 'round-robin', 'last_resort_pool': '', 'persist_cidr_ipv4': '32', 'persist_cidr_ipv6': '128', 'name': 'foo.ok.com', 'failure_rcode_response': 'disabled', 'failure_rcode': 'noerror', 'partition': 'Common', 'enabled': 'True', 'failure_rcode_ttl': '0', 'ttl_persistence': '3600', 'full_path': '/Common/foo.ok.com', 'pools': [{'partition': 'Common', 'ratio': '1', 'name': 'd3qw', 'order': '0'}], 'minimal_response': 'enabled', 'type': 'naptr', 'persistence': 'disabled'}]} </td>
    </tr>
            <tr>
        <td> pool </td>
        <td> Contains the pool object status and enabled status. </td>
        <td align=center> changed </td>
        <td align=center> dict </td>
        <td align=center> {'pool': [{'verify_member_availability': 'disabled', 'partition': 'Common', 'qos_packet_rate': '1', 'qos_hit_ratio': '5', 'alternate_mode': 'round-robin', 'members': [{'ratio': '1', 'name': 'ok3.com', 'service': '80', 'member_order': '0', 'disabled': 'True', 'flags': 'a', 'preference': '10', 'order': '10', 'full_path': 'ok3.com'}], 'ttl': '30', 'qos_vs_score': '0', 'qos_topology': '0', 'load_balancing_mode': 'round-robin', 'max_answers_returned': '1', 'fallback_mode': 'return-to-dns', 'qos_rtt': '50', 'name': 'd3qw', 'qos_kilobytes_second': '3', 'qos_lcs': '30', 'enabled': 'True', 'qos_vs_capacity': '0', 'qos_hops': '0', 'manual_resume': 'disabled', 'full_path': '/Common/d3qw', 'type': 'naptr', 'dynamic_ratio': 'disabled'}]} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Requires the f5-sdk Python package on the host. This is as easy as pip install f5-sdk



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
