.. _netapp_e_storagepool:


netapp_e_storagepool - Manage disk groups and disk pools
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or remove disk groups and disk pools for NetApp E-series storage arrays.




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
                <tr><td>criteria_drive_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of disks to use for building the storage pool. The pool will be expanded if this number exceeds the number of disks already in place</div>        </td></tr>
                <tr><td>criteria_drive_interface_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>sas</li><li>sas4k</li><li>fibre</li><li>fibre520b</li><li>scsi</li><li>sata</li><li>pata</li></ul></td>
        <td><div>The interface type to use when selecting drives for the storage pool (no value means all interface types will be considered)</div>        </td></tr>
                <tr><td>criteria_drive_min_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The minimum individual drive size (in size_unit) to consider when choosing drives for the storage pool.</div>        </td></tr>
                <tr><td>criteria_drive_require_fde<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether full disk encryption ability is required for drives to be added to the storage pool</div>        </td></tr>
                <tr><td>criteria_drive_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>hdd</li><li>ssd</li></ul></td>
        <td><div>The type of disk (hdd or ssd) to use when searching for candidates to use.</div>        </td></tr>
                <tr><td>criteria_min_usable_capacity<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The minimum size of the storage pool (in size_unit). The pool will be expanded if this value exceeds itscurrent size.</div>        </td></tr>
                <tr><td>criteria_size_unit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>gb</td>
        <td><ul><li>bytes</li><li>b</li><li>kb</li><li>mb</li><li>gb</li><li>tb</li><li>pb</li><li>eb</li><li>zb</li><li>yb</li></ul></td>
        <td><div>The unit used to interpret size parameters</div>        </td></tr>
                <tr><td>erase_secured_drives<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Whether to erase secured disks before adding to storage pool</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the storage pool to manage</div>        </td></tr>
                <tr><td>raid_level<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>raidAll</li><li>raid0</li><li>raid1</li><li>raid3</li><li>raid5</li><li>raid6</li><li>raidDiskPool</li></ul></td>
        <td><div>Only required when the requested state is 'present'.  The RAID level of the storage pool to be created.</div>        </td></tr>
                <tr><td>remove_volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Prior to removing a storage pool, delete all volumes in the pool.</div>        </td></tr>
                <tr><td>reserve_drive_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set the number of drives reserved by the storage pool for reconstruction operations. Only valide on raid disk pools.</div>        </td></tr>
                <tr><td>secure_pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Whether to convert to a secure storage pool. Will only work if all drives in the pool are security capable.</div>        </td></tr>
                <tr><td>ssid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The ID of the array to manage (as configured on the web services proxy).</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified storage pool should exist or not.</div><div>Note that removing a storage pool currently requires the removal of all defined volumes first.</div>        </td></tr>
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

        - name: No disk groups
          netapp_e_storagepool:
            ssid: "{{ ssid }}"
            name: "{{ item }}"
            state: absent
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            validate_certs: "{{ netapp_api_validate_certs }}"

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
        <td align=center> Json facts for the pool that was created. </td>
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
