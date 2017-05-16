.. _netapp_e_amg_role:


netapp_e_amg_role - Update the role of a storage array within an Asynchronous Mirror Group (AMG).
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Update a storage array to become the primary or secondary instance in an asynchronous mirror group




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
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether to force the role reversal regardless of the online-state of the primary</div></td></tr>
            <tr>
    <td>noSync<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Whether to avoid synchronization prior to role reversal</div></td></tr>
            <tr>
    <td>role<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>primary</li><li>secondary</li></ul></td>
        <td><div>Whether the array should be the primary or secondary array for the AMG</div></td></tr>
            <tr>
    <td>ssid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID of the primary storage array for the async mirror action</div></td></tr>
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

        - name: Update the role of a storage array
          netapp_e_amg_role:
            name: updating amg role
            role: primary
            ssid: "{{ ssid }}"
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
        <td> Failure message </td>
        <td align=center> failure </td>
        <td align=center> string </td>
        <td align=center> No Async Mirror Group with the name. </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

