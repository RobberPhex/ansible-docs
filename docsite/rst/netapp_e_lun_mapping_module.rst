.. _netapp_e_lun_mapping:


netapp_e_lun_mapping - Create or Remove LUN Mappings
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Allows for the creation and removal of volume to host mappings for NetApp E-series storage arrays.




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
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password used to authenticate against the API. This can optionally be set via an environment variable, API_PASSWORD</div></td></tr>
            <tr>
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The full API url. Example: http://ENDPOINT:8080/devmgr/v2</div><div>This can optionally be set via an environment variable, API_URL</div></td></tr>
            <tr>
    <td>api_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username used to authenticate against the API. This can optionally be set via an environment variable, API_USERNAME</div></td></tr>
            <tr>
    <td>lun<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The LUN number you wish to give the mapping</div><div>If the supplied <em>volume_name</em> is associated with a different LUN, it will be updated to what is supplied here.</div></td></tr>
            <tr>
    <td>ssid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The storage system array identifier.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Present will ensure the mapping exists, absent will remove the mapping.</div><div>All parameters <em>lun</em>, <em>target</em>, <em>target_type</em> and <em>volume_name</em> must still be supplied.</div></td></tr>
            <tr>
    <td>target<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of host or hostgroup you wish to assign to the mapping</div><div>If omitted, the default hostgroup is used.</div><div>If the supplied <em>volume_name</em> is associated with a different target, it will be updated to what is supplied here.</div></td></tr>
            <tr>
    <td>target_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>host</li><li>group</li></ul></td>
        <td><div>Whether the target is a host or group.</div><div>Required if supplying an explicit target.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Should https certificates be validated?</div></td></tr>
            <tr>
    <td>volume_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the volume you wish to include in the mapping.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
        - name: Lun Mapping Example
          netapp_e_lun_mapping:
            state: present
            ssid: 1
            lun: 12
            target: Wilson
            volume_name: Colby1
            target_type: group
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

