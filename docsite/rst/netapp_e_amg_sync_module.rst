.. _netapp_e_amg_sync:


netapp_e_amg_sync - Conduct synchronization actions on asynchronous member groups.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Allows for the initialization, suspension and resumption of an asynchronous mirror group's synchronization for NetApp E-series storage arrays.




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
    <td>delete_recovery_point<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Indicates whether the failures point can be deleted on the secondary if necessary to achieve the synchronization.</div><div>If true, and if the amount of unsynchronized data exceeds the CoW repository capacity on the secondary for any member volume, the last failures point will be deleted and synchronization will continue.</div><div>If false, the synchronization will be suspended if the amount of unsynchronized data exceeds the CoW Repository capacity on the secondary and the failures point will be preserved.</div><div>NOTE: This only has impact for newly launched syncs.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the async mirror group you wish to target</div></td></tr>
            <tr>
    <td>ssid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID of the storage array containing the AMG you wish to target</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>running</li><li>suspended</li></ul></td>
        <td><div>The synchronization action you'd like to take.</div><div>If <code>running</code> then it will begin syncing if there is no active sync or will resume a suspended sync. If there is already a sync in progress, it will return with an OK status.</div><div>If <code>suspended</code> it will suspend any ongoing sync action, but return OK if there is no active sync or if the sync is already suspended</div></td></tr>
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

        - name: start AMG async
          netapp_e_amg_sync:
            name: "{{ amg_sync_name }}"
            state: running
            ssid: "{{ ssid }}"
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"

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
        <td> json </td>
        <td> The object attributes of the AMG. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

