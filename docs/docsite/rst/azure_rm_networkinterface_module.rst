.. _azure_rm_networkinterface:


azure_rm_networkinterface - Manage Azure network interfaces.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update or delete a network interface. When creating a network interface you must provide the name of an existing virtual network, the name of an existing subnet within the virtual network. A default security group and public IP address will be created automatically, or you can provide the name of an existing security group and public IP address. See the examples below for more details.


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
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>resource_group location</td>
        <td></td>
        <td><div>Valid azure location. Defaults to location of the resource group.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the network interface.</div>        </td></tr>
                <tr><td>open_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When a default security group is created for a Linux host a rule will be added allowing inbound TCP connections to the default SSH port 22, and for a Windows host rules will be added allowing inbound access to RDP ports 3389 and 5986. Override the default ports by providing a list of open ports.</div>        </td></tr>
                <tr><td>os_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Linux</td>
        <td><ul><li>Windows</li><li>Linux</li></ul></td>
        <td><div>Determines any rules to be added to a default security group. When creating a network interface, if no security group name is provided, a default security group will be created. If the os_type is 'Windows', a rule will be added allowing RDP access. If the os_type is 'Linux', a rule allowing SSH access will be added.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Active Directory user password. Use when authenticating with an Active Directory user rather than service principal.</div>        </td></tr>
                <tr><td>private_ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Valid IPv4 address that falls within the specified subnet.</div>        </td></tr>
                <tr><td>private_ip_allocation_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Dynamic</td>
        <td><ul><li>Dynamic</li><li>Static</li></ul></td>
        <td><div>Specify whether or not the assigned IP address is permanent. NOTE: when creating a network interface specifying a value of 'Static' requires that a private_ip_address value be provided. You can update the allocation method to 'Static' after a dynamic private ip address has been assigned.</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Security profile found in ~/.azure/credentials file.</div>        </td></tr>
                <tr><td>public_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>When creating a network interface, if no public IP address name is provided a default public IP address will be created. Set to false, if you do not want a public IP address automatically created.</div>        </td></tr>
                <tr><td>public_ip_address_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of an existing public IP address object to associate with the security group.</div></br>
    <div style="font-size: small;">aliases: public_ip_address, public_ip_name<div>        </td></tr>
                <tr><td>public_ip_allocation_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Dynamic</td>
        <td><ul><li>Dynamic</li><li>Static</li></ul></td>
        <td><div>If a public_ip_address_name is not provided, a default public IP address will be created. The allocation method determines whether or not the public IP address assigned to the network interface is permanent.</div>        </td></tr>
                <tr><td>resource_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of a resource group where the network interface exists or will be created.</div>        </td></tr>
                <tr><td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div>        </td></tr>
                <tr><td>security_group_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of an existing security group with which to associate the network interface. If not provided, a default security group will be created.</div></br>
    <div style="font-size: small;">aliases: security_group<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Assert the state of the network interface. Use 'present' to create or update an interface and 'absent' to delete an interface.</div>        </td></tr>
                <tr><td>subnet_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of an existing subnet within the specified virtual network. Required when creating a network interface</div></br>
    <div style="font-size: small;">aliases: subnet<div>        </td></tr>
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
                <tr><td>virtual_network_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of an existing virtual network with which the network interface will be associated. Required when creating a network interface.</div></br>
    <div style="font-size: small;">aliases: virtual_network<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: Create a network interface with minimal parameters
          azure_rm_networkinterface:
                name: nic001
                resource_group: Testing
                virtual_network_name: vnet001
                subnet_name: subnet001
    
        - name: Create a network interface with private IP address only (no Public IP)
          azure_rm_networkinterface:
                name: nic001
                resource_group: Testing
                virtual_network_name: vnet001
                subnet_name: subnet001
                public_ip: no
    
        - name: Create a network interface for use in a Windows host (opens RDP port) with custom RDP port
          azure_rm_networkinterface:
                name: nic002
                resource_group: Testing
                virtual_network_name: vnet001
                subnet_name: subnet001
                os_type: Windows
                rdp_port: 3399
    
        - name: Create a network interface using existing security group and public IP
          azure_rm_networkinterface:
                name: nic003
                resource_group: Testing
                virtual_network_name: vnet001
                subnet_name: subnet001
                security_group_name: secgroup001
                public_ip_address_name: publicip001
    
        - name: Delete network interface
          azure_rm_networkinterface:
                resource_group: Testing
                name: nic003
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
        <td> The current state of the network interface. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'dns_settings': {'dns_servers': [], 'internal_fqdn': None, 'internal_dns_name_label': None, 'applied_dns_servers': []}, 'name': 'nic003', 'tags': None, 'primary': None, 'enable_ip_forwarding': False, 'etag': 'W/"be115a43-2148-4545-a324-f33ad444c926"', 'location': 'eastus2', 'mac_address': None, 'ip_configuration': {'private_ip_address': '10.1.0.10', 'private_ip_allocation_method': 'Static', 'public_ip_address': {'id': '/subscriptions/XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXX/resourceGroups/Testing/providers/Microsoft.Network/publicIPAddresses/publicip001', 'name': 'publicip001'}, 'name': 'default', 'subnet': {}}, 'provisioning_state': 'Succeeded', 'type': 'Microsoft.Network/networkInterfaces', 'id': '/subscriptions/XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXX/resourceGroups/Testing/providers/Microsoft.Network/networkInterfaces/nic003', 'network_security_group': {}} </td>
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
