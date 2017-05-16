.. _ipa_user:


ipa_user - Manage FreeIPA users
+++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add, modify and delete user within IPA server


Requirements (on host that executes module)
-------------------------------------------

  * base64
  * hashlib


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
                <tr><td>displayname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Display name</div>        </td></tr>
                <tr><td>givenname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>First name</div>        </td></tr>
                <tr><td>ipa_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ipa.example.com</td>
        <td></td>
        <td><div>IP or hostname of IPA server</div>        </td></tr>
                <tr><td>ipa_pass<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password of administrative user</div>        </td></tr>
                <tr><td>ipa_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>Port of IPA server</div>        </td></tr>
                <tr><td>ipa_prot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https</td>
        <td><ul><li>http</li><li>https</li></ul></td>
        <td><div>Protocol used by IPA server</div>        </td></tr>
                <tr><td>ipa_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Administrative account used on IPA server</div>        </td></tr>
                <tr><td>loginshell<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Login shell</div>        </td></tr>
                <tr><td>mail<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of mail addresses assigned to the user.</div><div>If an empty list is passed all assigned email addresses will be deleted.</div><div>If None is passed email addresses will not be checked or changed.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password</div>        </td></tr>
                <tr><td>sn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Surname</div>        </td></tr>
                <tr><td>sshpubkey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of public SSH key.</div><div>If an empty list is passed all assigned public keys will be deleted.</div><div>If None is passed SSH public keys will not be checked or changed.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>enabled</li><li>disabled</li></ul></td>
        <td><div>State to ensure</div>        </td></tr>
                <tr><td>telephonenumber<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of telephone numbers assigned to the user.</div><div>If an empty list is passed all assigned telephone numbers will be deleted.</div><div>If None is passed telephone numbers will not be checked or changed.</div>        </td></tr>
                <tr><td>title<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Title</div>        </td></tr>
                <tr><td>uid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>uid of the user</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>This only applies if <code>ipa_prot</code> is <em>https</em>.</div><div>If set to <code>no</code>, the SSL certificates will not be validated.</div><div>This should only set to <code>no</code> used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure pinky is present
    - ipa_user:
        name: pinky
        state: present
        givenname: Pinky
        sn: Acme
        mail:
        - pinky@acme.com
        telephonenumber:
        - '+555123456'
        sshpubkeyfp:
        - ssh-rsa ....
        - ssh-dsa ....
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure brain is absent
    - ipa_user:
        name: brain
        state: absent
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret

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
        <td> user </td>
        <td> User as returned by IPA API </td>
        <td align=center> always </td>
        <td align=center> dict </td>
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
