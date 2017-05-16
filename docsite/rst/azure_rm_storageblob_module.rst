.. _azure_rm_storageblob:


azure_rm_storageblob - Manage blob containers and blob objects.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update and delete blob containers and blob objects. Use to upload a file and store it as a blob object, or download a blob object to a file.


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
    <td>blob<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of a blob object within the container.</div></br>
        <div style="font-size: small;">aliases: blob_name<div></td></tr>
            <tr>
    <td>cache_control<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the blob cache-control header.</div></td></tr>
            <tr>
    <td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>container<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of a blob container within the storage account.</div></br>
        <div style="font-size: small;">aliases: container_name<div></td></tr>
            <tr>
    <td>content_disposition<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the blob content-disposition header.</div></td></tr>
            <tr>
    <td>content_encoding<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the blob encoding header.</div></td></tr>
            <tr>
    <td>content_language<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the blob content-language header.</div></td></tr>
            <tr>
    <td>content_md5<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the blob md5 hash value.</div></td></tr>
            <tr>
    <td>content_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the blob content-type header. For example, 'image/png'.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Destination file path. Use with state 'present' to download a blob.</div></br>
        <div style="font-size: small;">aliases: destination<div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Overwrite existing blob or file when uploading or downloading. Force deletion of a container that contains blobs.</div></td></tr>
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
    <td>public_access<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>container</li><li>blob</li></ul></td>
        <td><div>Determine a container's level of public access. By default containers are private. Can only be set at time of container creation.</div></td></tr>
            <tr>
    <td>resource_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the resource group to use.</div></td></tr>
            <tr>
    <td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Source file path. Use with state 'present' to upload a blob.</div></br>
        <div style="font-size: small;">aliases: source<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Assert the state of a container or blob.</div><div>Use state 'absent' with a container value only to delete a container. Include a blob value to remove a specific blob. A container will not be deleted, if it contains blobs. Use the force option to override, deleting the container and all associated blobs.</div><div>Use state 'present' to create or update a container and upload or download a blob. If the container does not exist, it will be created. If it exists, it will be updated with configuration options. Provide a blob name and either src or dest to upload or download. Provide a src path to upload and a dest path to download. If a blob (uploading) or a file (downloading) already exists, it will not be overwritten unless the force parameter is true.</div></td></tr>
            <tr>
    <td>storage_account_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the storage account to use.</div></br>
        <div style="font-size: small;">aliases: account_name<div></td></tr>
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

    - name: Remove container foo
      azure_rm_storageblob:
        resource_group: testing
        storage_account_name: clh0002
        container: foo
        state: absent
    
    - name: Create container foo and upload a file
      azure_rm_storageblob:
        resource_group: Testing
        storage_account_name: clh0002
        container: foo
        blob: graylog.png
        src: ./files/graylog.png
        public_access: container
        content_type: 'application/image'
    
    - name: Download the file
      azure_rm_storageblob:
        resource_group: Testing
        storage_account_name: clh0002
        container: foo
        blob: graylog.png
        dest: ~/tmp/images/graylog.png

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
        <td> container </td>
        <td> Facts about the current state of the selected container. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'last_mdoified': '09-Mar-2016 19:28:26 +0000', 'name': 'foo', 'tags': {}} </td>
    </tr>
            <tr>
        <td> blob </td>
        <td> Facts about the current state of the blob. </td>
        <td align=center> when a blob is operated on </td>
        <td align=center> dict </td>
        <td align=center> {'content_length': 136532, 'last_modified': '09-Mar-2016 22:08:25 +0000', 'name': 'graylog.png', 'tags': {}, 'content_settings': {'content_language': None, 'content_encoding': None, 'content_type': 'application/image', 'content_md5': None, 'content_disposition': None, 'cache_control': None}, 'type': 'BlockBlob'} </td>
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

