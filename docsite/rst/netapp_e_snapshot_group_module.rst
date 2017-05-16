.. _netapp_e_snapshot_group:


netapp_e_snapshot_group - Manage snapshot groups
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update, delete snapshot groups for NetApp E-series storage arrays




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
    <td>base_volume_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the base volume or thin volume to use as the base for the new snapshot group.</div><div>If a snapshot group with an identical <code>name</code> already exists but with a different base volume an error will be returned.</div></td></tr>
            <tr>
    <td>delete_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>The automatic deletion indicator.</div><div>If non-zero, the oldest snapshot image will be automatically deleted when creating a new snapshot image to keep the total number of snapshot images limited to the number specified.</div><div>This value is overridden by the consistency group setting if this snapshot group is associated with a consistency group.</div></td></tr>
            <tr>
    <td>full_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>purgepit</td>
        <td><ul><li>purgepit</li><li>unknown</li><li>failbasewrites</li><li>__UNDEFINED</li></ul></td>
        <td><div>The behavior on when the data repository becomes full.</div><div>This value is overridden by consistency group setting if this snapshot group is associated with a consistency group</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name to give the snapshot group</div></td></tr>
            <tr>
    <td>repo_pct<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>20</td>
        <td><ul></ul></td>
        <td><div>The size of the repository in relation to the size of the base volume</div></td></tr>
            <tr>
    <td>rollback_priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>medium</td>
        <td><ul><li>highest</li><li>high</li><li>medium</li><li>low</li><li>lowest</li><li>__UNDEFINED</li></ul></td>
        <td><div>The importance of the rollback operation.</div><div>This value is overridden by consistency group setting if this snapshot group is associated with a consistency group</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to ensure the group is present or absent.</div></td></tr>
            <tr>
    <td>storage_pool_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the storage pool on which to allocate the repository volume.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Should https certificates be validated?</div></td></tr>
            <tr>
    <td>warning_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>80</td>
        <td><ul></ul></td>
        <td><div>The repository utilization warning threshold, as a percentage of the repository volume capacity.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: Configure Snapshot group
          netapp_e_snapshot_group:
            ssid: "{{ ssid }}"
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            validate_certs: "{{ netapp_api_validate_certs }}"
            base_volume_name: SSGroup_test
            name=: OOSS_Group
            repo_pct: 20
            warning_threshold: 85
            delete_limit: 30
            full_policy: purgepit
            storage_pool_name: Disk_Pool_1
            rollback_priority: medium

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
        <td align=center> json facts for newly created snapshot group. </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

