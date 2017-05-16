.. _netapp_e_storage_system:


netapp_e_storage_system - Add/remove arrays from the Web Services Proxy
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage the arrays accessible via a NetApp Web Services Proxy for NetApp E-series storage arrays.




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
                <tr><td>array_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The management password of the array to manage, if set.</div>        </td></tr>
                <tr><td>array_wwn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The WWN of the array to manage. Only necessary if in-band managing multiple arrays on the same agent host.  Mutually exclusive of controller_addresses parameter.</div>        </td></tr>
                <tr><td>controller_addresses<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The list addresses for the out-of-band management adapter or the agent host. Mutually exclusive of array_wwn parameter.</div>        </td></tr>
                <tr><td>enable_trace<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable trace logging for SYMbol calls to the storage system.</div>        </td></tr>
                <tr><td>meta_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Optional meta tags to associate to this storage system</div>        </td></tr>
                <tr><td>ssid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The ID of the array to manage. This value must be unique for each array.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified array should be configured on the Web Services Proxy or not.</div>        </td></tr>
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

    ---
        - name:  Presence of storage system
          netapp_e_storage_system:
            ssid: "{{ item.key }}"
            state: present
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            validate_certs: "{{ netapp_api_validate_certs }}"
            controller_addresses:
              - "{{ item.value.address1 }}"
              - "{{ item.value.address2 }}"
          with_dict: "{{ storage_systems }}"
          when: check_storage_system

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




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
