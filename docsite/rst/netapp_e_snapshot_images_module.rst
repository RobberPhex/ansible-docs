.. _netapp_e_snapshot_images:


netapp_e_snapshot_images - Create and delete snapshot images
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create and delete snapshots images on snapshot groups for NetApp E-series storage arrays.
Only the oldest snapshot image can be deleted so consistency is preserved.
Related: Snapshot volumes are created from snapshot images.




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
    <td>snapshot_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the snapshot group in which you want to create a snapshot image.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>remove</li></ul></td>
        <td><div>Whether a new snapshot image should be created or oldest be deleted.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Should https certificates be validated?</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: Create Snapshot
          netapp_e_snapshot_images:
            ssid: "{{ ssid }}"
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            validate_certs: "{{ validate_certs }}"
            snapshot_group: "3300000060080E5000299C24000005B656D9F394"
            state: 'create'

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
        <td>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> image_id </td>
        <td>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> changed </td>
        <td>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

