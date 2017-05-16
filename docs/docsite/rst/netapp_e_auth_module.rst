.. _netapp_e_auth:


netapp_e_auth - Sets or updates the password for a storage array.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Sets or updates the password for a storage array.  When the password is updated on the storage array, it must be updated on the SANtricity Web Services proxy. Note, all storage arrays do not have a Monitor or RO role.




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
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password used to authenticate against the API</div><div>This can optionally be set via an environment variable, API_PASSWORD</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The full API url.</div><div>Example: http://ENDPOINT:8080/devmgr/v2</div><div>This can optionally be set via an environment variable, API_URL</div>        </td></tr>
                <tr><td>api_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username used to authenticate against the API</div><div>This can optionally be set via an environment variable, API_USERNAME</div>        </td></tr>
                <tr><td>current_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The current admin password. This is not required if the password hasn't been set before.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the storage array. Note that if more than one storage array with this name is detected, the task will fail and you'll have to use the ID instead.</div>        </td></tr>
                <tr><td>new_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password you would like to set. Cannot be more than 30 characters.</div>        </td></tr>
                <tr><td>set_admin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Boolean value on whether to update the admin password. If set to false then the RO account is updated.</div>        </td></tr>
                <tr><td>ssid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the identifier of the storage array in the Web Services Proxy.</div>        </td></tr>
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

    - name: Test module
      netapp_e_auth:
        name: trex
        current_password: OldPasswd
        new_password: NewPasswd
        set_admin: yes
        api_url: '{{ netapp_api_url }}'
        api_username: '{{ netapp_api_username }}'
        api_password: '{{ netapp_api_password }}'

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
        <td align=center> Password Updated Successfully </td>
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
