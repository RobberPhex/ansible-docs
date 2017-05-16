.. _ovirt_auth:


ovirt_auth - Module to manage authentication to oVirt.
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module authenticates to oVirt engine and creates SSO token, which should be later used in all other oVirt modules, so all modules don't need to perform login and logout. This module returns an Ansible fact called *ovirt_auth*. Every module can use this fact as ``auth`` parameter, to perform authentication.




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
    <td>ca_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A PEM file containing the trusted CA certificates. The certificate presented by the server will be verified using these CA certificates. If <code>ca_file</code> parameter is not set, system wide CA certificate store is used.</div></td></tr>
            <tr>
    <td>compress<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A boolean flag indicating if the SDK should ask the server to send compressed responses. The default is <em>True</em>. Note that this is a hint for the server, and that it may return uncompressed data even when this parameter is set to <em>True</em>.</div></td></tr>
            <tr>
    <td>insecure<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A boolean flag that indicates if the server TLS certificate and host name should be checked.</div></td></tr>
            <tr>
    <td>kerberos<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A boolean flag indicating if Kerberos authentication should be used instead of the default basic authentication.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password of the user.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specifies if a token should be created or revoked.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The maximum total time to wait for the response, in seconds. A value of zero (the default) means wait forever. If the timeout expires before the response is received an exception will be raised.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A string containing the base URL of the server. For example: <em>https://server.example.com/ovirt-engine/api</em>.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the user. For example: <em>admin@internal</em>.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    tasks:
      - block:
           # Create a vault with `ovirt_password` variable which store your
           # oVirt user's password, and include that yaml file with variable:
           - include_vars: ovirt_password.yml
    
           - name: Obtain SSO token with using username/password credentials:
             ovirt_auth:
               url: https://ovirt.example.com/ovirt-engine/api
               username: admin@internal
               ca_file: ca.pem
               password: "{{ ovirt_password }}"
    
           # Previous task generated I(ovirt_auth) fact, which you can later use
           # in different modules as follows:
           - ovirt_vms:
               auth: "{{ ovirt_auth }}"
               state: absent
               name: myvm
    
          always:
            - name: Always revoke the SSO token
              ovirt_auth:
                state: absent
                ovirt_auth: "{{ ovirt_auth }}"

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
        <td> ovirt_auth </td>
        <td> Authentication facts, needed to perform authentication to oVirt. </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> token </td>
        <td> SSO token which is used for connection to oVirt engine. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> kdfVWp9ZgeewBXV-iq3Js1-xQJZPSEQ334FLb3eksoEPRaab07DhZ8ED8ghz9lJd-MQ2GqtRIeqhvhCkrUWQPw </td>
        </tr>
                <tr>
        <td> timeout </td>
        <td> Number of seconds to wait for response. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
        </tr>
                <tr>
        <td> ca_file </td>
        <td> CA file, which is used to verify SSL/TLS connection. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ca.pem </td>
        </tr>
                <tr>
        <td> url </td>
        <td> URL of the oVirt engine API endpoint. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> https://ovirt.example.com/ovirt-engine/api </td>
        </tr>
                <tr>
        <td> insecure </td>
        <td> Flag indicating if insecure connection is used. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> kerberos </td>
        <td> Flag indicating if kerberos is used for authentication. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> compress </td>
        <td> Flag indicating if compression is used for connection. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> True </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note:: Everytime you use ovirt_auth module to obtain ticket, you need to also revoke the ticket, when you no longer need it, otherwise the ticket would be revoked by engine when it expires. For an example of how to achieve that, please take a look at *examples* section.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

