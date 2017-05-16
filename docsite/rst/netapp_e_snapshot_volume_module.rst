.. _netapp_e_snapshot_volume:


netapp_e_snapshot_volume - Manage E/EF-Series snapshot volumes.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update, remove snapshot volumes for NetApp E/EF-Series storage arrays.




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
    <td>api_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password to authenticate with the SANtricity WebServices Proxy or embedded REST API.</div></td></tr>
            <tr>
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The url to the SANtricity WebServices Proxy or embedded REST API.</div></td></tr>
            <tr>
    <td>api_username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username to authenticate with the SANtricity WebServices Proxy or embedded REST API.</div></td></tr>
            <tr>
    <td>full_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>85</td>
        <td><ul></ul></td>
        <td><div>The repository utilization warning threshold percentage</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name you wish to give the snapshot volume</div></td></tr>
            <tr>
    <td>repo_percentage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>20</td>
        <td><ul></ul></td>
        <td><div>The size of the view in relation to the size of the base volume</div></td></tr>
            <tr>
    <td>snapshot_image_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The identifier of the snapshot image used to create the new snapshot volume.</div><div>Note: You'll likely want to use the <span class='module'>netapp_e_facts</span> module to find the ID of the image you want.</div></td></tr>
            <tr>
    <td>ssid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>storage array ID</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Whether to create or remove the snapshot volume</div></td></tr>
            <tr>
    <td>storage_pool_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the storage pool on which to allocate the repository volume.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Should https certificates be validated?</div></td></tr>
            <tr>
    <td>view_mode<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>modeUnknown</li><li>readWrite</li><li>readOnly</li><li>__UNDEFINED</li></ul></td>
        <td><div>The snapshot volume access mode</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: Snapshot volume
          netapp_e_snapshot_volume:
            ssid: "{{ ssid }}"
            api_url: "{{ netapp_api_url }}"/
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            state: present
            storage_pool_name: "{{ snapshot_volume_storage_pool_name }}"
            snapshot_image_id: "{{ snapshot_volume_image_id }}"
            name: "{{ snapshot_volume_name }}"

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
        <td> msg </td>
        <td> Success message </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Json facts for the volume that was created. </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

