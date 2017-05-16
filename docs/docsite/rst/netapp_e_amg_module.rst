.. _netapp_e_amg:


netapp_e_amg - Create, Remove, and Update Asynchronous Mirror Groups
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Allows for the creation, removal and updating of Asynchronous Mirror Groups for NetApp E-series storage arrays




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
                <tr><td>api_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password to authenticate with the SANtricity WebServices Proxy or embedded REST API.</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The url to the SANtricity WebServices Proxy or embedded REST API.</div>        </td></tr>
                <tr><td>api_username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username to authenticate with the SANtricity WebServices Proxy or embedded REST API.</div>        </td></tr>
                <tr><td>interfaceType<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>iscsi</li><li>fibre</li></ul></td>
        <td><div>The intended protocol to use if both Fibre and iSCSI are available.</div>        </td></tr>
                <tr><td>manualSync<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Setting this to true will cause other synchronization values to be ignored</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the async array you wish to target, or create.</div><div>If <code>state</code> is present and the name isn't found, it will attempt to create.</div>        </td></tr>
                <tr><td>recoveryWarnThresholdMinutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>20</td>
        <td></td>
        <td><div>Recovery point warning threshold (minutes). The user will be warned when the age of the last good failures point exceeds this value</div>        </td></tr>
                <tr><td>repoUtilizationWarnThreshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>80</td>
        <td></td>
        <td><div>Recovery point warning threshold</div>        </td></tr>
                <tr><td>secondaryArrayId<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The ID of the secondary array to be used in mirroing process</div>        </td></tr>
                <tr><td>ssid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The ID of the array to manage. This value must be unique for each array.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A <code>state</code> of present will either create or update the async mirror group.</div><div>A <code>state</code> of absent will remove the async mirror group.</div>        </td></tr>
                <tr><td>syncIntervalMinutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>The synchronization interval in minutes</div>        </td></tr>
                <tr><td>syncWarnThresholdMinutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>The threshold (in minutes) for notifying the user that periodic synchronization has taken too long to complete.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Should https certificates be validated?</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: AMG removal
          na_eseries_amg:
            state: absent
            ssid: "{{ ssid }}"
            secondaryArrayId: "{{amg_secondaryArrayId}}"
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            new_name: "{{amg_array_name}}"
            name: "{{amg_name}}"
          when: amg_create
    
        - name: AMG create
          netapp_e_amg:
            state: present
            ssid: "{{ ssid }}"
            secondaryArrayId: "{{amg_secondaryArrayId}}"
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            new_name: "{{amg_array_name}}"
            name: "{{amg_name}}"
          when: amg_create

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
        <td> Successful creation </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> {"changed": true, "connectionType": "fc", "groupRef": "3700000060080E5000299C24000006E857AC7EEC", "groupState": "optimal", "id": "3700000060080E5000299C24000006E857AC7EEC", "label": "amg_made_by_ansible", "localRole": "primary", "mirrorChannelRemoteTarget": "9000000060080E5000299C24005B06E557AC7EEC", "orphanGroup": false, "recoveryPointAgeAlertThresholdMinutes": 20, "remoteRole": "secondary", "remoteTarget": {"nodeName": {"ioInterfaceType": "fc", "iscsiNodeName": null, "remoteNodeWWN": "20040080E5299F1C"}, "remoteRef": "9000000060080E5000299C24005B06E557AC7EEC", "scsiinitiatorTargetBaseProperties": {"ioInterfaceType": "fc", "iscsiinitiatorTargetBaseParameters": null}}, "remoteTargetId": "ansible2", "remoteTargetName": "Ansible2", "remoteTargetWwn": "60080E5000299F880000000056A25D56", "repositoryUtilizationWarnThreshold": 80, "roleChangeProgress": "none", "syncActivity": "idle", "syncCompletionTimeAlertThresholdMinutes": 10, "syncIntervalMinutes": 10, "worldWideName": "60080E5000299C24000006E857AC7EEC"} </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
