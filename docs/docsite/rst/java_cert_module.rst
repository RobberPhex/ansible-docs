.. _java_cert:


java_cert - Uses keytool to import/remove key from java keystore(cacerts)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This is a wrapper module around keytool. Which can be used to import/remove certificates from a given java keystore.




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
                <tr><td>cert_alias<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Imported certificate alias.</div>        </td></tr>
                <tr><td>cert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Local path to load certificate from. One of cert_url or cert_path is required to load certificate.</div>        </td></tr>
                <tr><td>cert_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>Port to connect to URL. This will be used to create server URL:PORT</div>        </td></tr>
                <tr><td>cert_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Basic URL to fetch SSL certificate from. One of cert_url or cert_path is required to load certificate.</div>        </td></tr>
                <tr><td>executable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>keytool</td>
        <td></td>
        <td><div>Path to keytool binary if not used we search in PATH for it.</div>        </td></tr>
                <tr><td>keystore_create<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Create keystore if it doesn't exist</div>        </td></tr>
                <tr><td>keystore_pass<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Keystore password.</div>        </td></tr>
                <tr><td>keystore_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to keystore.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Defines action which can be either certificate import or removal.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Import SSL certificate from google.com to a given cacerts keystore
    java_cert:
      cert_url: google.com
      cert_port: 443
      keystore_path: /usr/lib/jvm/jre7/lib/security/cacerts
      keystore_pass: changeit
      state: present
    
    # Remove certificate with given alias from a keystore
    java_cert:
      cert_url: google.com
      keystore_path: /usr/lib/jvm/jre7/lib/security/cacerts
      keystore_pass: changeit
      executable: /usr/lib/jvm/jre7/bin/keytool
      state: absent
    
    # Import SSL certificate from google.com to a keystore,
    # create it if it doesn't exist
    java_cert:
      cert_url: google.com
      keystore_path: /tmp/cacerts
      keystore_pass: changeit
      keystore_create: yes
      state: present

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
        <td> Output from stdout of keytool command after execution of given command. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Module require existing keystore at keystore_path '/tmp/test/cacerts' </td>
    </tr>
            <tr>
        <td> cmd </td>
        <td> Executed command to get action done </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> keytool -importcert -noprompt -keystore </td>
    </tr>
            <tr>
        <td> rc </td>
        <td> Keytool command execution return value </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
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
