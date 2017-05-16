.. _opendj_backendprop:


opendj_backendprop - Will update the backend configuration of OpenDJ via the dsconfig set-backend-prop command.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module will update settings for OpenDJ with the command set-backend-prop.
It will check first via de get-backend-prop if configuration needs to be applied.




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
    <td>backend<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the backend on which the property needs to be updated.</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname of the OpenDJ server.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The configuration setting to update.</div></td></tr>
            <tr>
    <td>opendj_bindir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/opt/opendj/bin</td>
        <td><ul></ul></td>
        <td><div>The path to the bin directory of OpenDJ.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password for the cn=Directory Manager user.</div><div>Either password or passwordfile is needed.</div></td></tr>
            <tr>
    <td>passwordfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Location to the password file which holds the password for the cn=Directory Manager user.</div><div>Either password or passwordfile is needed.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Admin port on which the OpenDJ instance is available.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul></ul></td>
        <td><div>If configuration needs to be added/updated</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cn=Directory Manager</td>
        <td><ul></ul></td>
        <td><div>The username to connect to.</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The value for the configuration item.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: "Add or update OpenDJ backend properties"
        action: opendj_backendprop
                hostname=localhost
                port=4444
                username="cn=Directory Manager"
                password=password
                backend=userRoot
                name=index-entry-limit
                value=5000




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

