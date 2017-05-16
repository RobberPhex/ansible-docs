.. _os_network:


os_network - Creates/removes networks from OpenStack
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove network from OpenStack.


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
            <tr>
    <td>admin_state_up<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether the state should be marked as up or down.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>How long should the socket layer wait before timing out for API calls. If this is omitted, nothing will be passed to the requests library.</div></td></tr>
            <tr>
    <td>auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary containing auth information as needed by the cloud's auth plugin strategy. For the default <em>password</em> plugin, this would contain <em>auth_url</em>, <em>username</em>, <em>password</em>, <em>project_name</em> and any information about domains if the cloud supports them. For other plugins, this param will need to contain whatever parameters that auth plugin requires. This parameter is not needed if a named cloud is provided or OpenStack OS_* environment variables are present.</div></td></tr>
            <tr>
    <td>auth_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>password</td>
        <td><ul></ul></td>
        <td><div>Name of the auth plugin to use. If the cloud uses something other than password authentication, the name of the plugin should be indicated here and the contents of the <em>auth</em> parameter should be updated accordingly.</div></td></tr>
            <tr>
    <td>availability_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the availability zone.</div></td></tr>
            <tr>
    <td>cacert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a CA Cert bundle that can be used as part of verifying SSL API requests.</div></td></tr>
            <tr>
    <td>cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a client certificate to use as part of the SSL transaction</div></td></tr>
            <tr>
    <td>cloud<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Named cloud to operate against. Provides default values for <em>auth</em> and <em>auth_type</em>. This parameter is not needed if <em>auth</em> is provided or if OpenStack OS_* environment variables are present.</div></td></tr>
            <tr>
    <td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div></td></tr>
            <tr>
    <td>external<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether this network is externally accessible.</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a client key to use as part of the SSL transaction</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name to be assigned to the network.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Project name or ID containing the network (name admin-only)</div></td></tr>
            <tr>
    <td>provider_network_type<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>flat</li><li>vlan</li><li>vxlan</li><li>gre</li></ul></td>
        <td><div>The type of physical network that maps to this network resource.</div></td></tr>
            <tr>
    <td>provider_physical_network<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The physical network where this network object is implemented.</div></td></tr>
            <tr>
    <td>provider_segmentation_id<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>An isolated segment on the physical network. The <em>network_type</em> attribute defines the segmentation model. For example, if the <em>network_type</em> value is vlan, this ID is a vlan identifier. If the <em>network_type</em> value is gre, this ID is a gre key.</div></td></tr>
            <tr>
    <td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the region.</div></td></tr>
            <tr>
    <td>shared<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether this network is shared or not.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td><ul></ul></td>
        <td><div>How long should ansible wait for the requested resource.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether or not SSL API requests should be verified.</div></br>
        <div style="font-size: small;">aliases: verify<div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Should ansible wait until the requested resource is complete.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create an externally accessible network named 'ext_network'.
    - os_network:
        cloud: mycloud
        state: present
        name: ext_network
        external: true

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
        <td> network </td>
        <td> Dictionary describing the network. </td>
        <td align=center> On success when I(state) is 'present'. </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> status </td>
        <td> Network status. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> ACTIVE </td>
        </tr>
                <tr>
        <td> router:external </td>
        <td> Indicates whether this network is externally accessible. </td>
        <td align=center>  </td>
        <td align=center> bool </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> name </td>
        <td> Network name. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> ext_network </td>
        </tr>
                <tr>
        <td> provider:physical_network </td>
        <td> The physical network where this network object is implemented. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> my_vlan_net </td>
        </tr>
                <tr>
        <td> subnets </td>
        <td> The associated subnets. </td>
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center> [] </td>
        </tr>
                <tr>
        <td> tenant_id </td>
        <td> The tenant ID. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 06820f94b9f54b119636be2728d216fc </td>
        </tr>
                <tr>
        <td> admin_state_up </td>
        <td> The administrative state of the network. </td>
        <td align=center>  </td>
        <td align=center> bool </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> mtu </td>
        <td> The MTU of a network resource. </td>
        <td align=center>  </td>
        <td align=center> integer </td>
        <td align=center> 0 </td>
        </tr>
                <tr>
        <td> shared </td>
        <td> Indicates whether this network is shared across all tenants. </td>
        <td align=center>  </td>
        <td align=center> bool </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> port_security_enabled </td>
        <td> The port security status </td>
        <td align=center>  </td>
        <td align=center> bool </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> provider:network_type </td>
        <td> The type of physical network that maps to this network resource. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> vlan </td>
        </tr>
                <tr>
        <td> id </td>
        <td> Network ID. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 4bb4f9a5-3bd2-4562-bf6a-d17a6341bb56 </td>
        </tr>
                <tr>
        <td> provider:segmentation_id </td>
        <td> An isolated segment on the physical network. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 101 </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note:: The standard OpenStack environment variables, such as ``OS_USERNAME`` may be used instead of providing explicit values.
.. note:: Auth information is driven by os-client-config, which means that values can come from a yaml config file in /etc/ansible/openstack.yaml, /etc/openstack/clouds.yaml or ~/.config/openstack/clouds.yaml, then from standard environment variables, then finally by explicit parameters in plays. More information can be found at http://docs.openstack.org/developer/os-client-config


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

