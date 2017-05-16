.. _azure_rm_networkinterface_facts:


azure_rm_networkinterface_facts - Get network interface facts.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Get facts for a specific network interface or all network interfaces within a resource group.


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
    <td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Only show results for a specific network interface.</div></td></tr>
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
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the resource group containing the network interface(s). Required when searching by name.</div></td></tr>
            <tr>
    <td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div></td></tr>
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
        <td><div>Limit results by providing a list of tags. Format tags as 'key' or 'key:value'.</div></td></tr>
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

        - name: Get facts for one network interface
          azure_rm_networkinterface_facts:
            resource_group: Testing
            name: nic001
    
        - name: Get network interfaces within a resource group
          azure_rm_networkinterface_facts:
            resource_group: Testing
    
        - name: Get network interfaces by tag
          azure_rm_networkinterface_facts:
            resource_group: Testing
            tags:
              - testing
              - foo:bar

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
        <td> azure_networkinterfaces </td>
        <td> List of network interface dicts. </td>
        <td align=center> always </td>
        <td align=center> list </td>
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

