.. _azure_rm_subnet:


azure_rm_subnet - Manage Azure subnets.
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update or delete a subnet within a given virtual network. Allows setting and updating the address prefix CIDR, which must be valid within the context of the virtual network. Use the azure_rm_networkinterface module to associate interfaces with the subnet and assign specific IP addresses.


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
    <td>address_prefix_cidr<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>CIDR defining the IPv4 address space of the subnet. Must be valid within the context of the virtual network.</div></br>
        <div style="font-size: small;">aliases: address_prefix<div></td></tr>
            <tr>
    <td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the subnet.</div></td></tr>
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
    <td>resource_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of resource group.</div></td></tr>
            <tr>
    <td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>security_group_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of an existing security group with which to associate the subnet.</div></br>
        <div style="font-size: small;">aliases: security_group<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Assert the state of the subnet. Use 'present' to create or update a subnet and 'absent' to delete a subnet.</div></td></tr>
            <tr>
    <td>subscription_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your Azure subscription Id.</div></td></tr>
            <tr>
    <td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure tenant ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>virtual_network_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of an existing virtual network with which the subnet is or will be associated.</div></br>
        <div style="font-size: small;">aliases: virtual_network<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: Create a subnet
          azure_rm_subnet:
            name: foobar
            virtual_network_name: My_Virtual_Network
            resource_group: Testing
            address_prefix_cidr: "10.1.0.0/24"
    
        - name: Delete a subnet
          azure_rm_subnet:
            name: foobar
            virtual_network_name: My_Virtual_Network
            resource_group: Testing
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
        <td> Current state of the subnet. </td>
        <td align=center> success </td>
        <td align=center> complex </td>
        <td align=center>  </td>
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

