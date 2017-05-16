.. _os_security_group_rule:


os_security_group_rule - Add/Delete rule from an existing security group
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or Remove rule from an existing security group


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * shade


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
                <tr><td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>How long should the socket layer wait before timing out for API calls. If this is omitted, nothing will be passed to the requests library.</div>        </td></tr>
                <tr><td>auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary containing auth information as needed by the cloud's auth plugin strategy. For the default <em>password</em> plugin, this would contain <em>auth_url</em>, <em>username</em>, <em>password</em>, <em>project_name</em> and any information about domains if the cloud supports them. For other plugins, this param will need to contain whatever parameters that auth plugin requires. This parameter is not needed if a named cloud is provided or OpenStack OS_* environment variables are present.</div>        </td></tr>
                <tr><td>auth_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>password</td>
        <td></td>
        <td><div>Name of the auth plugin to use. If the cloud uses something other than password authentication, the name of the plugin should be indicated here and the contents of the <em>auth</em> parameter should be updated accordingly.</div>        </td></tr>
                <tr><td>availability_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ignored. Present for backwards compatability</div>        </td></tr>
                <tr><td>cacert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a CA Cert bundle that can be used as part of verifying SSL API requests.</div>        </td></tr>
                <tr><td>cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a client certificate to use as part of the SSL transaction.</div>        </td></tr>
                <tr><td>cloud<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Named cloud to operate against. Provides default values for <em>auth</em> and <em>auth_type</em>. This parameter is not needed if <em>auth</em> is provided or if OpenStack OS_* environment variables are present.</div>        </td></tr>
                <tr><td>direction<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ingress</td>
        <td><ul><li>egress</li><li>ingress</li></ul></td>
        <td><div>The direction in which the security group rule is applied. Not all providers support egress.</div>        </td></tr>
                <tr><td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div>        </td></tr>
                <tr><td>ethertype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>IPv4</td>
        <td><ul><li>IPv4</li><li>IPv6</li></ul></td>
        <td><div>Must be IPv4 or IPv6, and addresses represented in CIDR must match the ingress or egress rules. Not all providers support IPv6.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a client key to use as part of the SSL transaction.</div>        </td></tr>
                <tr><td>port_range_max<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Ending port</div>        </td></tr>
                <tr><td>port_range_min<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Starting port</div>        </td></tr>
                <tr><td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>tcp</li><li>udp</li><li>icmp</li><li>112</li><li>None</li></ul></td>
        <td><div>IP protocols TCP UDP ICMP 112 (VRRP)</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the region.</div>        </td></tr>
                <tr><td>remote_group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name or ID of the Security group to link (exclusive with remote_ip_prefix)</div>        </td></tr>
                <tr><td>remote_ip_prefix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Source IP address(es) in CIDR notation (exclusive with remote_group)</div>        </td></tr>
                <tr><td>security_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name or ID of the security group</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Should the resource be present or absent.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td></td>
        <td><div>How long should ansible wait for the requested resource.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not SSL API requests should be verified. Before 2.3 this defaulted to True.</div></br>
    <div style="font-size: small;">aliases: verify<div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Should ansible wait until the requested resource is complete.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a security group rule
    - os_security_group_rule:
        cloud: mordred
        security_group: foo
        protocol: tcp
        port_range_min: 80
        port_range_max: 80
        remote_ip_prefix: 0.0.0.0/0
    
    # Create a security group rule for ping
    - os_security_group_rule:
        cloud: mordred
        security_group: foo
        protocol: icmp
        remote_ip_prefix: 0.0.0.0/0
    
    # Another way to create the ping rule
    - os_security_group_rule:
        cloud: mordred
        security_group: foo
        protocol: icmp
        port_range_min: -1
        port_range_max: -1
        remote_ip_prefix: 0.0.0.0/0
    
    # Create a TCP rule covering all ports
    - os_security_group_rule:
        cloud: mordred
        security_group: foo
        protocol: tcp
        port_range_min: 1
        port_range_max: 65535
        remote_ip_prefix: 0.0.0.0/0
    
    # Another way to create the TCP rule above (defaults to all ports)
    - os_security_group_rule:
        cloud: mordred
        security_group: foo
        protocol: tcp
        remote_ip_prefix: 0.0.0.0/0
    
    # Create a rule for VRRP with numbered protocol 112
    - os_security_group_rule:
        security_group: loadbalancer_sg
        protocol: 112
        remote_group: loadbalancer-node_sg

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
        <td> direction </td>
        <td> The direction in which the security group rule is applied. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> egress </td>
    </tr>
            <tr>
        <td> protocol </td>
        <td> The protocol that is matched by the security group rule. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> tcp </td>
    </tr>
            <tr>
        <td> ethertype </td>
        <td> One of IPv4 or IPv6. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> IPv4 </td>
    </tr>
            <tr>
        <td> port_range_max </td>
        <td> The maximum port number in the range that is matched by the security group rule. </td>
        <td align=center>  </td>
        <td align=center> int </td>
        <td align=center> 8000 </td>
    </tr>
            <tr>
        <td> security_group_id </td>
        <td> The security group ID to associate with this security group rule. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> port_range_min </td>
        <td> The minimum port number in the range that is matched by the security group rule. </td>
        <td align=center>  </td>
        <td align=center> int </td>
        <td align=center> 8000 </td>
    </tr>
            <tr>
        <td> remote_ip_prefix </td>
        <td> The remote IP prefix to be associated with this security group rule. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 0.0.0.0/0 </td>
    </tr>
            <tr>
        <td> id </td>
        <td> Unique rule UUID. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - The standard OpenStack environment variables, such as ``OS_USERNAME`` may be used instead of providing explicit values.
    - Auth information is driven by os-client-config, which means that values can come from a yaml config file in /etc/ansible/openstack.yaml, /etc/openstack/clouds.yaml or ~/.config/openstack/clouds.yaml, then from standard environment variables, then finally by explicit parameters in plays. More information can be found at http://docs.openstack.org/developer/os-client-config



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
