.. _netapp_e_volume:


netapp_e_volume - Manage storage volumes (standard and thin)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create or remove volumes (standard and thin) for NetApp E/EF-series storage arrays.




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
    <td>data_assurance_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If data assurance should be enabled for the volume</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the volume to manage</div></td></tr>
            <tr>
    <td>segment_size_kb<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>512</td>
        <td><ul></ul></td>
        <td><div>The segment size of the new volume</div></td></tr>
            <tr>
    <td>size<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Required only when state = 'present'.  The size of the volume in (size_unit).</div></td></tr>
            <tr>
    <td>size_unit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>gb</td>
        <td><ul><li>bytes</li><li>b</li><li>kb</li><li>mb</li><li>gb</li><li>tb</li><li>pb</li><li>eb</li><li>zb</li><li>yb</li></ul></td>
        <td><div>The unit used to interpret the size parameter</div></td></tr>
            <tr>
    <td>ssd_cache_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None (ignores existing SSD cache setting)</td>
        <td><ul><li>yes</li><li>no</li><li>true</li><li>false</li></ul></td>
        <td><div>Whether an existing SSD cache should be enabled on the volume (fails if no SSD cache defined)</div></td></tr>
            <tr>
    <td>ssid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID of the array to manage (as configured on the web services proxy).</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified volume should exist or not.</div></td></tr>
            <tr>
    <td>storage_pool_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Required only when requested state is 'present'.  The name of the storage pool the volume should exist on.</div></td></tr>
            <tr>
    <td>thin_provision<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li><li>true</li><li>false</li></ul></td>
        <td><div>Whether the volume should be thin provisioned.  Thin volumes can only be created on disk pools (raidDiskPool).</div></td></tr>
            <tr>
    <td>thin_volume_max_repo_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>same as size (in size_unit)</td>
        <td><ul></ul></td>
        <td><div>Maximum size that the thin volume repository volume will automatically expand to</div></td></tr>
            <tr>
    <td>thin_volume_repo_size<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Initial size of the thin volume repository volume (in size_unit)</div></td></tr>
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

        - name: No thin volume
          netapp_e_volume:
            ssid: "{{ ssid }}"
            name: NewThinVolumeByAnsible
            state: absent
            log_path: /tmp/volume.log
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            validate_certs: "{{ netapp_api_validate_certs }}"
          when: check_volume
    
    
        - name: No fat volume
          netapp_e_volume:
            ssid: "{{ ssid }}"
            name: NewVolumeByAnsible
            state: absent
            log_path: /tmp/volume.log
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            validate_certs: "{{ netapp_api_validate_certs }}"
          when: check_volume

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
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

