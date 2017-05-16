.. _azure_rm_publicipaddress:


azure_rm_publicipaddress - Manage Azure Public IP Addresses.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update and delete a Public IP address. Allows setting and updating the address allocation method and domain name label. Use the azure_rm_networkinterface module to associate a Public IP with a network interface.


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
                <tr><td>allocation_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Dynamic</td>
        <td><ul><li>Dynamic</li><li>Static</li></ul></td>
        <td><div>Control whether the assigned Public IP remains permanently assigned to the object. If not set to 'Static', the IP address my changed anytime an associated virtual machine is power cycled.</div>        </td></tr>
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
                <tr><td>domain_name_label<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The customizable portion of the FQDN assigned to public IP address. This is an explicit setting. If no value is provided, any existing value will be removed on an existing public IP.</div></br>
    <div style="font-size: small;">aliases: domain_name_label<div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>resource_group location</td>
        <td></td>
        <td><div>Valid azure location. Defaults to location of the resource group.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the Public IP.</div>        </td></tr>
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
                <tr><td>resource_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of resource group with which the Public IP is associated.</div>        </td></tr>
                <tr><td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Assert the state of the Public IP. Use 'present' to create or update a and 'absent' to delete.</div>        </td></tr>
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

        - name: Create a public ip address
          azure_rm_publicipaddress:
            resource_group: testing
            name: my_public_ip
            allocation_method: Static
            domain_name: foobar
    
        - name: Delete public ip
          azure_rm_publicipaddress:
            resource_group: testing
            name: my_public_ip
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
        <td> Facts about the current state of the object. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'dns_settings': {}, 'name': 'publicip002', 'tags': {}, 'public_ip_allocation_method': 'Static', 'provisioning_state': 'Succeeded', 'ip_address': '52.160.103.93', 'etag': '"/"a5e56955-12df-445a-bda4-dc129d22c12f"', 'location': 'westus', 'idle_timeout_in_minutes': 4, 'type': 'Microsoft.Network/publicIPAddresses'} </td>
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
