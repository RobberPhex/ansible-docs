.. _azure_rm_securitygroup:


azure_rm_securitygroup - Manage Azure network security groups.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update or delete a network security group. A security group contains Access Control List (ACL) rules that allow or deny network traffic to subnets or individual network interfaces. A security group is created with a set of default security rules and an empty set of security rules. Shape traffic flow by adding rules to the empty set of security rules.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * azure == 2.0.0rc5


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
                <tr><td>ad_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Active Directory username. Use when authenticating with an Active Directory user rather than service principal.</div>        </td></tr>
                <tr><td>append_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Use to control if tags field is canonical or just appends to existing tags. When canonical, any tags not found in the tags parameter will be removed from the object's metadata.</div>        </td></tr>
                <tr><td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Azure client ID. Use when authenticating with a Service Principal.</div>        </td></tr>
                <tr><td>default_rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The set of default rules automatically added to a security group at creation. In general default rules will not be modified. Modify rules to shape the flow of traffic to or from a subnet or NIC. See rules below for the makeup of a rule dict.</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>resource_group location</td>
        <td></td>
        <td><div>Valid azure location. Defaults to location of the resource group.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the security group to operate on.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Active Directory user password. Use when authenticating with an Active Directory user rather than service principal.</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Security profile found in ~/.azure/credentials file.</div>        </td></tr>
                <tr><td>purge_default_rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Remove any existing rules not matching those defined in the default_rules parameter.</div>        </td></tr>
                <tr><td>purge_rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Remove any existing rules not matching those defined in the rules parameters.</div>        </td></tr>
                <tr><td>resource_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the resource group the security group belongs to.</div>        </td></tr>
                <tr><td rowspan="2">rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td><td></td>
    <td> <div>Set of rules shaping traffic flow to or from a subnet or NIC. Each rule is a dictionary.</div>    </tr>
    <tr>
    <td colspan="5">
    <table border=1 cellpadding=4>
    <caption><b>Dictionary object rules</b></caption>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                    <tr><td>source_address_prefix<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>*</td>
                <td></td>
                <td><div>I</div><div>P</div><div> </div><div>a</div><div>d</div><div>d</div><div>r</div><div>e</div><div>s</div><div>s</div><div> </div><div>o</div><div>r</div><div> </div><div>C</div><div>I</div><div>D</div><div>R</div><div> </div><div>f</div><div>r</div><div>o</div><div>m</div><div> </div><div>w</div><div>h</div><div>i</div><div>c</div><div>h</div><div> </div><div>t</div><div>r</div><div>a</div><div>f</div><div>f</div><div>i</div><div>c</div><div> </div><div>o</div><div>r</div><div>i</div><div>g</div><div>i</div><div>n</div><div>a</div><div>t</div><div>e</div><div>s</div><div>.</div>        </td></tr>
                    <tr><td>destination_address_prefix<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>*</td>
                <td></td>
                <td><div>I</div><div>P</div><div> </div><div>a</div><div>d</div><div>d</div><div>r</div><div>e</div><div>s</div><div>s</div><div> </div><div>o</div><div>r</div><div> </div><div>C</div><div>I</div><div>D</div><div>R</div><div> </div><div>t</div><div>o</div><div> </div><div>w</div><div>h</div><div>i</div><div>c</div><div>h</div><div> </div><div>t</div><div>r</div><div>a</div><div>f</div><div>f</div><div>i</div><div>c</div><div> </div><div>i</div><div>s</div><div> </div><div>h</div><div>e</div><div>a</div><div>d</div><div>e</div><div>d</div><div>.</div>        </td></tr>
                    <tr><td>protocol<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>*</td>
                <td><ul><li>Udp</li><li>Tcp</li><li>*</li></ul></td>
                <td><div>A</div><div>c</div><div>c</div><div>e</div><div>p</div><div>t</div><div>e</div><div>d</div><div> </div><div>t</div><div>r</div><div>a</div><div>f</div><div>f</div><div>i</div><div>c</div><div> </div><div>p</div><div>r</div><div>o</div><div>t</div><div>o</div><div>c</div><div>o</div><div>l</div><div>.</div>        </td></tr>
                    <tr><td>name<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>U</div><div>n</div><div>i</div><div>q</div><div>u</div><div>e</div><div> </div><div>n</div><div>a</div><div>m</div><div>e</div><div> </div><div>f</div><div>o</div><div>r</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>r</div><div>u</div><div>l</div><div>e</div><div>.</div>        </td></tr>
                    <tr><td>description<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>S</div><div>h</div><div>o</div><div>r</div><div>t</div><div> </div><div>d</div><div>e</div><div>s</div><div>c</div><div>r</div><div>i</div><div>p</div><div>t</div><div>i</div><div>o</div><div>n</div><div> </div><div>o</div><div>f</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>r</div><div>u</div><div>l</div><div>e</div><div>'</div><div>s</div><div> </div><div>p</div><div>u</div><div>r</div><div>p</div><div>o</div><div>s</div><div>e</div><div>.</div>        </td></tr>
                    <tr><td>direction<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>Inbound</td>
                <td><ul><li>Inbound</li><li>Outbound</li></ul></td>
                <td><div>I</div><div>n</div><div>d</div><div>i</div><div>c</div><div>a</div><div>t</div><div>e</div><div>s</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>d</div><div>i</div><div>r</div><div>e</div><div>c</div><div>t</div><div>i</div><div>o</div><div>n</div><div> </div><div>o</div><div>f</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>t</div><div>r</div><div>a</div><div>f</div><div>f</div><div>i</div><div>c</div><div> </div><div>f</div><div>l</div><div>o</div><div>w</div><div>.</div>        </td></tr>
                    <tr><td>access<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>Allow</td>
                <td><ul><li>Allow</li><li>Deny</li></ul></td>
                <td><div>W</div><div>h</div><div>e</div><div>t</div><div>h</div><div>e</div><div>r</div><div> </div><div>o</div><div>r</div><div> </div><div>n</div><div>o</div><div>t</div><div> </div><div>t</div><div>o</div><div> </div><div>a</div><div>l</div><div>l</div><div>o</div><div>w</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>t</div><div>r</div><div>a</div><div>f</div><div>f</div><div>i</div><div>c</div><div> </div><div>f</div><div>l</div><div>o</div><div>w</div><div>.</div>        </td></tr>
                    <tr><td>source_port_range<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>*</td>
                <td></td>
                <td><div>P</div><div>o</div><div>r</div><div>t</div><div> </div><div>o</div><div>r</div><div> </div><div>r</div><div>a</div><div>n</div><div>g</div><div>e</div><div> </div><div>o</div><div>f</div><div> </div><div>p</div><div>o</div><div>r</div><div>t</div><div>s</div><div> </div><div>f</div><div>r</div><div>o</div><div>m</div><div> </div><div>w</div><div>h</div><div>i</div><div>c</div><div>h</div><div> </div><div>t</div><div>r</div><div>a</div><div>f</div><div>f</div><div>i</div><div>c</div><div> </div><div>o</div><div>r</div><div>i</div><div>g</div><div>i</div><div>n</div><div>a</div><div>t</div><div>e</div><div>s</div><div>.</div>        </td></tr>
                    <tr><td>destination_port_range<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>*</td>
                <td></td>
                <td><div>P</div><div>o</div><div>r</div><div>t</div><div> </div><div>o</div><div>r</div><div> </div><div>r</div><div>a</div><div>n</div><div>g</div><div>e</div><div> </div><div>o</div><div>f</div><div> </div><div>p</div><div>o</div><div>r</div><div>t</div><div>s</div><div> </div><div>t</div><div>o</div><div> </div><div>w</div><div>h</div><div>i</div><div>c</div><div>h</div><div> </div><div>t</div><div>r</div><div>a</div><div>f</div><div>f</div><div>i</div><div>c</div><div> </div><div>i</div><div>s</div><div> </div><div>h</div><div>e</div><div>a</div><div>d</div><div>e</div><div>d</div><div>.</div>        </td></tr>
                    <tr><td>priority<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>O</div><div>r</div><div>d</div><div>e</div><div>r</div><div> </div><div>i</div><div>n</div><div> </div><div>w</div><div>h</div><div>i</div><div>c</div><div>h</div><div> </div><div>t</div><div>o</div><div> </div><div>a</div><div>p</div><div>p</div><div>l</div><div>y</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>r</div><div>u</div><div>l</div><div>e</div><div>.</div><div> </div><div>M</div><div>u</div><div>s</div><div>t</div><div> </div><div>a</div><div> </div><div>u</div><div>n</div><div>i</div><div>q</div><div>u</div><div>e</div><div> </div><div>i</div><div>n</div><div>t</div><div>e</div><div>g</div><div>e</div><div>r</div><div> </div><div>b</div><div>e</div><div>t</div><div>w</div><div>e</div><div>e</div><div>n</div><div> </div><div>1</div><div>0</div><div>0</div><div> </div><div>a</div><div>n</div><div>d</div><div> </div><div>4</div><div>0</div><div>9</div><div>6</div><div> </div><div>i</div><div>n</div><div>c</div><div>l</div><div>u</div><div>s</div><div>i</div><div>v</div><div>e</div><div>.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Assert the state of the security group. Set to 'present' to create or update a security group. Set to 'absent' to remove a security group.</div>        </td></tr>
                <tr><td>subscription_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Your Azure subscription Id.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary of string:string pairs to assign as metadata to the object. Metadata tags on the object will be updated with any provided values. To remove tags set append_tags option to false.
    </div>        </td></tr>
                <tr><td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Azure tenant ID. Use when authenticating with a Service Principal.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # Create a security group
    - azure_rm_securitygroup:
          resource_group: mygroup
          name: mysecgroup
          purge_rules: yes
          rules:
              - name: DenySSH
                protocol: TCP
                destination_port_range: 22
                access: Deny
                priority: 100
                direction: Inbound
              - name: 'AllowSSH'
                protocol: TCP
                source_address_prefix: '174.109.158.0/24'
                destination_port_range: 22
                access: Allow
                priority: 101
                direction: Inbound
    
    # Update rules on existing security group
    - azure_rm_securitygroup:
          resource_group: mygroup
          name: mysecgroup
          rules:
              - name: DenySSH
                protocol: TCP
                destination_port_range: 22-23
                access: Deny
                priority: 100
                direction: Inbound
              - name: AllowSSHFromHome
                protocol: TCP
                source_address_prefix: '174.109.158.0/24'
                destination_port_range: 22-23
                access: Allow
                priority: 102
                direction: Inbound
          tags:
              testing: testing
              delete: on-exit
    
    # Delete security group
    - azure_rm_securitygroup:
          resource_group: mygroup
          name: mysecgroup
          state: absent

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
        <td> state </td>
        <td> Current state of the security group. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'subnets': [], 'name': 'mysecgroup', 'tags': {'foo': 'bar', 'testing': 'testing', 'delete': 'on-exit'}, 'rules': [{'access': 'Deny', 'destination_address_prefix': '*', 'protocol': 'Tcp', 'description': None, 'direction': 'Inbound', 'provisioning_state': 'Succeeded', 'priority': 100, 'etag': 'W/"edf48d56-b315-40ca-a85d-dbcb47f2da7d"', 'source_port_range': '*', 'source_address_prefix': '*', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup/securityRules/DenySSH', 'destination_port_range': '22', 'name': 'DenySSH'}, {'access': 'Allow', 'destination_address_prefix': '*', 'protocol': 'Tcp', 'description': None, 'direction': 'Inbound', 'provisioning_state': 'Succeeded', 'priority': 101, 'etag': 'W/"edf48d56-b315-40ca-a85d-dbcb47f2da7d"', 'source_port_range': '*', 'source_address_prefix': '174.109.158.0/24', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup/securityRules/AllowSSH', 'destination_port_range': '22', 'name': 'AllowSSH'}], 'network_interfaces': [], 'default_rules': [{'access': 'Allow', 'destination_address_prefix': 'VirtualNetwork', 'protocol': '*', 'description': 'Allow inbound traffic from all VMs in VNET', 'direction': 'Inbound', 'provisioning_state': 'Succeeded', 'priority': 65000, 'etag': 'W/"edf48d56-b315-40ca-a85d-dbcb47f2da7d"', 'source_port_range': '*', 'source_address_prefix': 'VirtualNetwork', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup/defaultSecurityRules/AllowVnetInBound', 'destination_port_range': '*', 'name': 'AllowVnetInBound'}, {'access': 'Allow', 'destination_address_prefix': '*', 'protocol': '*', 'description': 'Allow inbound traffic from azure load balancer', 'direction': 'Inbound', 'provisioning_state': 'Succeeded', 'priority': 65001, 'etag': 'W/"edf48d56-b315-40ca-a85d-dbcb47f2da7d"', 'source_port_range': '*', 'source_address_prefix': 'AzureLoadBalancer', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup/defaultSecurityRules/AllowAzureLoadBalancerInBound', 'destination_port_range': '*', 'name': 'AllowAzureLoadBalancerInBound'}, {'access': 'Deny', 'destination_address_prefix': '*', 'protocol': '*', 'description': 'Deny all inbound traffic', 'direction': 'Inbound', 'provisioning_state': 'Succeeded', 'priority': 65500, 'etag': 'W/"edf48d56-b315-40ca-a85d-dbcb47f2da7d"', 'source_port_range': '*', 'source_address_prefix': '*', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup/defaultSecurityRules/DenyAllInBound', 'destination_port_range': '*', 'name': 'DenyAllInBound'}, {'access': 'Allow', 'destination_address_prefix': 'VirtualNetwork', 'protocol': '*', 'description': 'Allow outbound traffic from all VMs to all VMs in VNET', 'direction': 'Outbound', 'provisioning_state': 'Succeeded', 'priority': 65000, 'etag': 'W/"edf48d56-b315-40ca-a85d-dbcb47f2da7d"', 'source_port_range': '*', 'source_address_prefix': 'VirtualNetwork', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup/defaultSecurityRules/AllowVnetOutBound', 'destination_port_range': '*', 'name': 'AllowVnetOutBound'}, {'access': 'Allow', 'destination_address_prefix': 'Internet', 'protocol': '*', 'description': 'Allow outbound traffic from all VMs to Internet', 'direction': 'Outbound', 'provisioning_state': 'Succeeded', 'priority': 65001, 'etag': 'W/"edf48d56-b315-40ca-a85d-dbcb47f2da7d"', 'source_port_range': '*', 'source_address_prefix': '*', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup/defaultSecurityRules/AllowInternetOutBound', 'destination_port_range': '*', 'name': 'AllowInternetOutBound'}, {'access': 'Deny', 'destination_address_prefix': '*', 'protocol': '*', 'description': 'Deny all outbound traffic', 'direction': 'Outbound', 'provisioning_state': 'Succeeded', 'priority': 65500, 'etag': 'W/"edf48d56-b315-40ca-a85d-dbcb47f2da7d"', 'source_port_range': '*', 'source_address_prefix': '*', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup/defaultSecurityRules/DenyAllOutBound', 'destination_port_range': '*', 'name': 'DenyAllOutBound'}], 'location': 'westus', 'type': 'Microsoft.Network/networkSecurityGroups', 'id': '/subscriptions/3f7e29ba-24e0-42f6-8d9c-5149a14bda37/resourceGroups/Testing/providers/Microsoft.Network/networkSecurityGroups/mysecgroup'} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - For authentication with Azure you can pass parameters, set environment variables or use a profile stored in ~/.azure/credentials. Authentication is possible using a service principal or Active Directory user. To authenticate via service principal pass subscription_id, client_id, secret and tenant or set set environment variables AZURE_SUBSCRIPTION_ID, AZURE_CLIENT_ID, AZURE_SECRET and AZURE_TENANT.
    - To Authentication via Active Directory user pass ad_user and password, or set AZURE_AD_USER and AZURE_PASSWORD in the environment.
    - Alternatively, credentials can be stored in ~/.azure/credentials. This is an ini file containing a [default] section and the following keys: subscription_id, client_id, secret and tenant or subscription_id, ad_user and password. It is also possible to add additional profiles. Specify the profile by passing profile or setting AZURE_PROFILE in the environment.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
