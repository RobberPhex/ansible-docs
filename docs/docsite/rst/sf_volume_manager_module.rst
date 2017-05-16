.. _sf_volume_manager:


sf_volume_manager - Manage SolidFire volumes
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, destroy, or update volumes on SolidFire


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
                <tr><td>512emulation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Should the volume provide 512-byte sector emulation?</div><div>Required when <code>state=present</code></div>        </td></tr>
                <tr><td>access<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>readOnly</li><li>readWrite</li><li>locked</li><li>replicationTarget</li></ul></td>
        <td><div>Access allowed for the volume.</div><div>readOnly: Only read operations are allowed.</div><div>readWrite: Reads and writes are allowed.</div><div>locked: No reads or writes are allowed.</div><div>replicationTarget: Identify a volume as the target volume for a paired set of volumes. If the volume is not paired, the access status is locked.</div><div>If unspecified, the access settings of the clone will be the same as the source.</div>        </td></tr>
                <tr><td>account_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Account ID for the owner of this volume.</div>        </td></tr>
                <tr><td>attributes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A YAML dictionary of attributes that you would like to apply on this volume.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the SolidFire cluster.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the volume to manage.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>qos<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Initial quality of service settings for this volume.</div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The size of the volume in (size_unit).</div><div>Required when <code>state = present</code>.</div>        </td></tr>
                <tr><td>size_unit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>gb</td>
        <td><ul><li>bytes</li><li>b</li><li>kb</li><li>mb</li><li>gb</li><li>tb</li><li>pb</li><li>eb</li><li>zb</li><li>yb</li></ul></td>
        <td><div>The unit used to interpret the size parameter.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified volume should exist or not.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Please ensure that the user has the adequate permissions. For more information, please read the official documentation <a href='https://goo.gl/ddJa4Q'>https://goo.gl/ddJa4Q</a>.</div>        </td></tr>
                <tr><td>volume_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The ID of the volume to manage or update.</div><div>In order to create multiple volumes with the same name, but different volume_ids, please declare the <em>volume_id</em> parameter with an arbitary value. However, the specified volume_id will not be assigned to the newly created volume (since it's an auto-generated property).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

       - name: Create Volume
         sf_volume_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: present
           name: AnsibleVol
           account_id: 3
           enable512e: False
           size: 1
           size_unit: gb
    
       - name: Update Volume
         sf_volume_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: present
           name: AnsibleVol
           account_id: 3
           access: readWrite
    
       - name: Delete Volume
         sf_volume_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: absent
           name: AnsibleVol
           account_id: 2

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
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

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
