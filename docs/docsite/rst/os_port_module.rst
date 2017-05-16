.. _os_port:


os_port - Add/Update/Delete ports from an OpenStack cloud.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add, Update or Remove ports from an OpenStack cloud. A *state* of 'present' will ensure the port is created or updated if required.


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
                <tr><td>admin_state_up<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Sets admin state.</div>        </td></tr>
                <tr><td>allowed_address_pairs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Allowed address pairs list.  Allowed address pairs are supported with dictionary structure. e.g.  allowed_address_pairs: - ip_address: 10.1.0.12 mac_address: ab:cd:ef:12:34:56 - ip_address: ...</div>        </td></tr>
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
                <tr><td>device_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Device ID of device using this port.</div>        </td></tr>
                <tr><td>device_owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The ID of the entity that uses this port.</div>        </td></tr>
                <tr><td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div>        </td></tr>
                <tr><td>extra_dhcp_opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Extra dhcp options to be assigned to this port.  Extra options are supported with dictionary structure. e.g.  extra_dhcp_opts: - opt_name: opt name1 opt_value: value1 - opt_name: ...</div>        </td></tr>
                <tr><td>fixed_ips<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Desired IP and/or subnet for this port.  Subnet is referenced by subnet_id and IP is referenced by ip_address.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a client key to use as part of the SSL transaction.</div>        </td></tr>
                <tr><td>mac_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>MAC address of this port.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Name that has to be given to the port.</div>        </td></tr>
                <tr><td>network<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Network ID or name this port belongs to.</div>        </td></tr>
                <tr><td>no_security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Do not associate a security group with this port.</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the region.</div>        </td></tr>
                <tr><td>security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Security group(s) ID(s) or name(s) associated with the port (comma separated string or YAML list)</div>        </td></tr>
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

    # Create a port
    - os_port:
        state: present
        auth:
          auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
          username: admin
          password: admin
          project_name: admin
        name: port1
        network: foo
    
    # Create a port with a static IP
    - os_port:
        state: present
        auth:
          auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
          username: admin
          password: admin
          project_name: admin
        name: port1
        network: foo
        fixed_ips:
          - ip_address: 10.1.0.21
    
    # Create a port with No security groups
    - os_port:
        state: present
        auth:
          auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
          username: admin
          password: admin
          project_name: admin
        name: port1
        network: foo
        no_security_groups: True
    
    # Update the existing 'port1' port with multiple security groups (version 1)
    - os_port:
        state: present
        auth:
          auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/d
          username: admin
          password: admin
          project_name: admin
        name: port1
        security_groups: 1496e8c7-4918-482a-9172-f4f00fc4a3a5,057d4bdf-6d4d-472...
    
    # Update the existing 'port1' port with multiple security groups (version 2)
    - os_port:
        state: present
        auth:
          auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/d
          username: admin
          password: admin
          project_name: admin
        name: port1
        security_groups:
          - 1496e8c7-4918-482a-9172-f4f00fc4a3a5
          - 057d4bdf-6d4d-472...

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
        <td> status </td>
        <td> Port's status. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name given to the port. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> allowed_address_pairs </td>
        <td> Allowed address pairs with this port. </td>
        <td align=center> success </td>
        <td align=center> list of dicts </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> admin_state_up </td>
        <td> Admin state up flag for this port. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> network_id </td>
        <td> Network ID this port belongs in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> tenant_id </td>
        <td> Tenant id associated with this port. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> fixed_ips </td>
        <td> Fixed ip(s) associated with this port. </td>
        <td align=center> success </td>
        <td align=center> list of dicts </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> id </td>
        <td> Unique UUID. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> security_groups </td>
        <td> Security group(s) associated with this port. </td>
        <td align=center> success </td>
        <td align=center> list of strings </td>
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
