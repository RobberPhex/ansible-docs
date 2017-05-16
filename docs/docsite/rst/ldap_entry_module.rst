.. _ldap_entry:


ldap_entry - Add or remove LDAP entries.
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove LDAP entries. This module only asserts the existence or non-existence of an LDAP entry, not its attributes. To assert the attribute values of an entry, see :ref:`ldap_attr <ldap_attr>`.


Requirements (on host that executes module)
-------------------------------------------

  * python-ldap


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
                <tr><td>attributes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>state=present</em>, attributes necessary to create an entry. Existing entries are never modified. To assert specific attribute values on an existing entry, use <span class='module'>ldap_attr</span> module instead.</div>        </td></tr>
                <tr><td>bind_dn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A DN to bind with. If this is omitted, we'll try a SASL bind with the EXTERNAL mechanism. If this is blank, we'll use an anonymous bind.</div>        </td></tr>
                <tr><td>bind_pw<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password to use with <em>bind_dn</em>.</div>        </td></tr>
                <tr><td>dn<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The DN of the entry to add or remove.</div>        </td></tr>
                <tr><td>objectClass<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>state=present</em>, value or list of values to use when creating the entry. It can either be a string or an actual list of strings.</div>        </td></tr>
                <tr><td>params<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of options which allows to overwrite any of the task or the <em>attributes</em> options. To remove an option, set the value of the option to <code>null</code>.</div>        </td></tr>
                <tr><td>server_uri<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ldapi:///</td>
        <td></td>
        <td><div>A URI to the LDAP server. The default value lets the underlying LDAP client library look for a UNIX domain socket in its default location.</div>        </td></tr>
                <tr><td>start_tls<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If true, we'll use the START_TLS LDAP extension.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The target state of the entry.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Make sure we have a parent entry for users
      ldap_entry:
        dn: ou=users,dc=example,dc=com
        objectClass: organizationalUnit
    
    - name: Make sure we have an admin user
      ldap_entry:
        dn: cn=admin,dc=example,dc=com
        objectClass:
          - simpleSecurityObject
          - organizationalRole
        attributes:
          description: An LDAP administrator
          userPassword: "{SSHA}tabyipcHzhwESzRaGA7oQ/SDoBZQOGND"
    
    - name: Get rid of an old entry
      ldap_entry:
        dn: ou=stuff,dc=example,dc=com
        state: absent
        server_uri: ldap://localhost/
        bind_dn: cn=admin,dc=example,dc=com
        bind_pw: password
    
    #
    # The same as in the previous example but with the authentication details
    # stored in the ldap_auth variable:
    #
    # ldap_auth:
    #   server_uri: ldap://localhost/
    #   bind_dn: cn=admin,dc=example,dc=com
    #   bind_pw: password
    - name: Get rid of an old entry
      ldap_entry:
        dn: ou=stuff,dc=example,dc=com
        state: absent
        params: "{{ ldap_auth }}"


Notes
-----

.. note::
    - The default authentication settings will attempt to use a SASL EXTERNAL bind over a UNIX domain socket. This works well with the default Ubuntu install for example, which includes a cn=peercred,cn=external,cn=auth ACL rule allowing root to modify the server configuration. If you need to use a simple bind to access your server, pass the credentials in *bind_dn* and *bind_pw*.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
