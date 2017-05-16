.. _azure_rm_securitygroup:


azure_rm_securitygroup - Manage Azure network security groups.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update or delete a network security group. A security group contains Access Control List (ACL) rules that allow or deny network traffic to subnets or individual network interfaces. A security group is created with a set of default security rules and an empty set of security rules. Shape traffic flow by adding rules to the empty set of security rules.


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
            <tr>
    <td>ad_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Active Directory username. Use when authenticating with an Active Directory user rather than service principal.</div></td></tr>
            <tr>
    <td>append_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Use to control if tags field is canonical or just appends to existing tags. When canonical, any tags not found in the tags parameter will be removed from the object's metadata.</div></td></tr>
            <tr>
    <td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>default_rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The set of default rules automatically added to a security group at creation. In general default rules will not be modified. Modify rules to shape the flow of traffic to or from a subnet or NIC. See rules below for the makeup of a rule dict.</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>resource_group location</td>
        <td><ul></ul></td>
        <td><div>Valid azure location. Defaults to location of the resource group.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the security group to operate on.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Active Directory user password. Use when authenticating with an Active Directory user rather than service principal.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Security profile found in ~/.azure/credentials file.</div></td></tr>
            <tr>
    <td>purge_default_rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remove any existing rules not matching those defined in the default_rules parameter.</div></td></tr>
            <tr>
    <td>purge_rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remove any existing rules not matching those defined in the rules parameters.</div></td></tr>
            <tr>
    <td>resource_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the resource group the security group belongs to.</div></td></tr>
            <tr>
    <td>rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set of rules shaping traffic flow to or from a subnet or NIC. Each rule is a dictionary.</div></td></tr>
            <tr>
    <td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Assert the state of the security group. Set to 'present' to create or update a security group. Set to 'absent' to remove a security group.</div></td></tr>
            <tr>
    <td>subscription_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your Azure subscription Id.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary of string:string pairs to assign as metadata to the object. Metadata tags on the object will be updated with any provided values. To remove tags set append_tags option to false.</div></td></tr>
            <tr>
    <td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure tenant ID. Use when authenticating with a Service Principal.</div></td></tr>
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

.. note:: For authentication with Azure you can pass parameters, set environment variables or use a profile stored in ~/.azure/credentials. Authentication is possible using a service principal or Active Directory user. To authenticate via service principal pass subscription_id, client_id, secret and tenant or set set environment variables AZURE_SUBSCRIPTION_ID, AZURE_CLIENT_ID, AZURE_SECRET and AZURE_TENANT.
.. note:: To Authentication via Active Directory user pass ad_user and password, or set AZURE_AD_USER and AZURE_PASSWORD in the environment.
.. note:: Alternatively, credentials can be stored in ~/.azure/credentials. This is an ini file containing a [default] section and the following keys: subscription_id, client_id, secret and tenant or subscription_id, ad_user and password. It is also possible to add additional profiles. Specify the profile by passing profile or setting AZURE_PROFILE in the environment.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

