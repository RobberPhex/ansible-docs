.. _sf_volume_access_group_manager:


sf_volume_access_group_manager - Manage SolidFire Volume Access Groups
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, destroy, or update volume access groups on SolidFire


Requirements (on host that executes module)
-------------------------------------------

  * solidfire-sdk-python (1.1.0.92)


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
                <tr><td>attributes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of Name/Value pairs in JSON object format.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the SolidFire cluster.</div>        </td></tr>
                <tr><td>initiators<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of initiators to include in the volume access group. If unspecified, the access group will start out without configured initiators.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the volume access group. It is not required to be unique, but recommended.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified volume access group should exist or not.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Please ensure that the user has the adequate permissions. For more information, please read the official documentation <a href='https://goo.gl/ddJa4Q'>https://goo.gl/ddJa4Q</a>.</div>        </td></tr>
                <tr><td>virtual_network_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The ID of the SolidFire Virtual Network ID to associate the volume access group with.</div>        </td></tr>
                <tr><td>virtual_network_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The ID of the VLAN Virtual Network Tag to associate the volume access group with.</div>        </td></tr>
                <tr><td>volume_access_group_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The ID of the volume access group to modify or delete.</div>        </td></tr>
                <tr><td>volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of volumes to initially include in the volume access group. If unspecified, the access group will start without any volumes.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

       - name: Create Volume Access Group
         sf_volume_access_group_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: present
           name: AnsibleVolumeAccessGroup
           volumes: [7,8]
    
       - name: Modify Volume Access Group
         sf_volume_access_group_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: present
           volume_access_group_id: 1
           name: AnsibleVolumeAccessGroup-Renamed
           attributes: {"volumes": [1,2,3], "virtual_network_id": 12345}
    
       - name: Delete Volume Access Group
         sf_volume_access_group_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: absent
           volume_access_group_id: 1


Notes
-----

.. note::
    - The modules prefixed with ``sf\_`` are built to support the SolidFire storage platform.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
