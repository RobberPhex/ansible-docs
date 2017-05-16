.. _openssl_privatekey:


openssl_privatekey - Generate OpenSSL private keys.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows one to (re)generate OpenSSL private keys. It uses the pyOpenSSL python library to interact with openssl. One can generate either RSA or DSA private keys. Keys are generated in PEM format.


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
        <td><div>Name of the file in which the generated TLS/SSL private key will be written. It will have 0600 mode.</div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>4096</td>
        <td></td>
        <td><div>Size (in bits) of the TLS/SSL key to generate</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the private key should exist or not, taking action if the state is different from what is stated.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>RSA</td>
        <td><ul><li>RSA</li><li>DSA</li></ul></td>
        <td><div>The algorithm used to generate the TLS/SSL private key</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Generate an OpenSSL private key with the default values (4096 bits, RSA)
    # and no public key
    - openssl_privatekey:
        path: /etc/ssl/private/ansible.com.pem
    
    # Generate an OpenSSL private key with a different size (2048 bits)
    - openssl_privatekey:
        path: /etc/ssl/private/ansible.com.pem
        size: 2048
    
    # Force regenerate an OpenSSL private key if it already exists
    - openssl_privatekey:
        path: /etc/ssl/private/ansible.com.pem
        force: True
    
    # Generate an OpenSSL private key with a different algorithm (DSA)
    - openssl_privatekey:
        path: /etc/ssl/private/ansible.com.pem
        type: DSA

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
        <td> size </td>
        <td> Size (in bits) of the TLS/SSL private key </td>
        <td align=center> ['changed', 'success'] </td>
        <td align=center> integer </td>
        <td align=center> 4096 </td>
    </tr>
            <tr>
        <td> type </td>
        <td> Algorithm used to generate the TLS/SSL private key </td>
        <td align=center> ['changed', 'success'] </td>
        <td align=center> string </td>
        <td align=center> RSA </td>
    </tr>
            <tr>
        <td> filename </td>
        <td> Path to the generated TLS/SSL private key file </td>
        <td align=center> ['changed', 'success'] </td>
        <td align=center> string </td>
        <td align=center> /etc/ssl/private/ansible.com.pem </td>
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
