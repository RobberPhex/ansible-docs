.. _azure_rm_storageaccount:


azure_rm_storageaccount - Manage Azure storage accounts.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update or delete a storage account.


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
                <tr><td>account_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Premium_LRS</li><li>Standard_GRS</li><li>Standard_LRS</li><li>Standard_RAGRS</li><li>Standard_ZRS</li></ul></td>
        <td><div>Type of storage account. Required when creating a storage account. NOTE: Standard_ZRS and Premium_LRS accounts cannot be changed to other account types, and other account types cannot be changed to Standard_ZRS or Premium_LRS.</div></br>
    <div style="font-size: small;">aliases: type<div>        </td></tr>
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
                <tr><td>custom_domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User domain assigned to the storage account. Must be a dictionary with 'name' and 'use_sub_domain' keys where 'name' is the CNAME source. Only one custom domain is supported per storage account at this time. To clear the existing custom domain, use an empty string for the custom domain name property.</div><div>Can be added to an existing storage account. Will be ignored during storage account creation.</div>        </td></tr>
                <tr><td>kind<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>Storage</td>
        <td><ul><li>Storage</li><li>StorageBlob</li></ul></td>
        <td><div>The 'kind' of storage.</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>resource_group location</td>
        <td></td>
        <td><div>Valid azure location. Defaults to location of the resource group.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the storage account to update or create.</div>        </td></tr>
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
        <td><div>Name of the resource group to use.</div>        </td></tr>
                <tr><td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Assert the state of the storage account. Use 'present' to create or update a storage account and 'absent' to delete an account.</div>        </td></tr>
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

        - name: remove account, if it exists
          azure_rm_storageaccount:
            resource_group: Testing
            name: clh0002
            state: absent
    
        - name: create an account
          azure_rm_storageaccount:
            resource_group: Testing
            name: clh0002
            type: Standard_RAGRS
            tags:
              - testing: testing
              - delete: on-exit

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
        <td> Current state of the storage account. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'secondary_location': 'centralus', 'account_type': 'Standard_RAGRS', 'custom_domain': None, 'resource_group': 'Testing', 'tags': None, 'primary_location': 'eastus2', 'secondary_endpoints': {'queue': 'https://clh0003-secondary.queue.core.windows.net/', 'table': 'https://clh0003-secondary.table.core.windows.net/', 'blob': 'https://clh0003-secondary.blob.core.windows.net/'}, 'provisioning_state': 'Succeeded', 'primary_endpoints': {'queue': 'https://clh0003.queue.core.windows.net/', 'table': 'https://clh0003.table.core.windows.net/', 'blob': 'https://clh0003.blob.core.windows.net/'}, 'location': 'eastus2', 'status_of_primary': 'Available', 'status_of_secondary': 'Available', 'type': 'Microsoft.Storage/storageAccounts', 'id': '/subscriptions/XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXX/resourceGroups/testing/providers/Microsoft.Storage/storageAccounts/clh0003', 'name': 'clh0003'} </td>
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
