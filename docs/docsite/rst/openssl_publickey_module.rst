.. _openssl_publickey:


openssl_publickey - Generate an OpenSSL public key from its private key.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows one to (re)generate OpenSSL public keys from their private keys. It uses the pyOpenSSL python library to interact with openssl. Keys are generated in PEM format. This module works only if the version of PyOpenSSL is recent enough (> 16.0.0)


Requirements (on host that executes module)
-------------------------------------------

  * python-pyOpenSSL


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
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Should the key be regenerated even it it already exists</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the file in which the generated TLS/SSL public key will be written.</div>        </td></tr>
                <tr><td>privatekey_path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Path to the TLS/SSL private key from which to genereate the public key.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the public key should exist or not, taking action if the state is different from what is stated.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Generate an OpenSSL public key.
    - openssl_publickey:
        path: /etc/ssl/public/ansible.com.pem
        privatekey_path: /etc/ssl/private/ansible.com.pem
    
    # Force regenerate an OpenSSL public key if it already exists
    - openssl_publickey:
        path: /etc/ssl/public/ansible.com.pem
        privatekey_path: /etc/ssl/private/ansible.com.pem
        force: True
    
    # Remove an OpenSSL public key
    - openssl_publickey:
        path: /etc/ssl/public/ansible.com.pem
        privatekey_path: /etc/ssl/private/ansible.com.pem
        state: absent

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
        <td> privatekey </td>
        <td> Path to the TLS/SSL private key the public key was generated from </td>
        <td align=center> ['changed', 'success'] </td>
        <td align=center> string </td>
        <td align=center> /etc/ssl/private/ansible.com.pem </td>
    </tr>
            <tr>
        <td> filename </td>
        <td> Path to the generated TLS/SSL public key file </td>
        <td align=center> ['changed', 'success'] </td>
        <td align=center> string </td>
        <td align=center> /etc/ssl/public/ansible.com.pem </td>
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
