.. _netscaler:


netscaler - Manages Citrix NetScaler entities
+++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages Citrix NetScaler server and service entities.




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
    <td>action<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>disable</td>
        <td><ul><li>enable</li><li>disable</li></ul></td>
        <td><div>the action you want to perform on the entity</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>hostname</td>
        <td><ul></ul></td>
        <td><div>name of the entity</div></td></tr>
            <tr>
    <td>nsc_host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>hostname or ip of your netscaler</div></td></tr>
            <tr>
    <td>nsc_protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https</td>
        <td><ul></ul></td>
        <td><div>protocol used to access netscaler</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>password</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>server</td>
        <td><ul><li>server</li><li>service</li></ul></td>
        <td><div>type of the entity</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>username</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Disable the server
    ansible host -m netscaler -a "nsc_host=nsc.example.com user=apiuser password=apipass"
    
    # Enable the server
    ansible host -m netscaler -a "nsc_host=nsc.example.com user=apiuser password=apipass action=enable"
    
    # Disable the service local:8080
    ansible host -m netscaler -a "nsc_host=nsc.example.com user=apiuser password=apipass name=local:8080 type=service action=disable"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

