.. _ldap_attr:


ldap_attr - Add or remove LDAP attribute values.
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove LDAP attribute values.


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
        <td><div>The DN of the entry to modify.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the attribute to modify.</div>        </td></tr>
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
        <td><ul><li>present</li><li>absent</li><li>exact</li></ul></td>
        <td><div>The state of the attribute values. If <code>present</code>, all given values will be added if they're missing. If <code>absent</code>, all given values will be removed if present. If <code>exact</code>, the set of values will be forced to exactly those provided and no others. If <em>state=exact</em> and <em>value</em> is empty, all values for this attribute will be removed.</div>        </td></tr>
                <tr><td>values<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The value(s) to add or remove. This can be a string or a list of strings. The complex argument format is required in order to pass a list of strings (see examples).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Configure directory number 1 for example.com
      ldap_attr:
        dn: olcDatabase={1}hdb,cn=config
        name: olcSuffix
        values: dc=example,dc=com
        state: exact
    
    # The complex argument format is required here to pass a list of ACL strings.
    - name: Set up the ACL
      ldap_attr:
        dn: olcDatabase={1}hdb,cn=config
        name: olcAccess
        values:
          - >-
            {0}to attrs=userPassword,shadowLastChange
            by self write
            by anonymous auth
            by dn="cn=admin,dc=example,dc=com" write
            by * none'
          - >-
            {1}to dn.base="dc=example,dc=com"
            by dn="cn=admin,dc=example,dc=com" write
            by * read
        state: exact
    
    - name: Declare some indexes
      ldap_attr:
        dn: olcDatabase={1}hdb,cn=config
        name: olcDbIndex
        values: "{{ item }}"
      with_items:
        - objectClass eq
        - uid eq
    
    - name: Set up a root user, which we can use later to bootstrap the directory
      ldap_attr:
        dn: olcDatabase={1}hdb,cn=config
        name: "{{ item.key }}"
        values: "{{ item.value }}"
        state: exact
      with_dict:
        olcRootDN: cn=root,dc=example,dc=com
        olcRootPW: "{SSHA}tabyipcHzhwESzRaGA7oQ/SDoBZQOGND"
    
    - name: Get rid of an unneeded attribute
      ldap_attr:
        dn: uid=jdoe,ou=people,dc=example,dc=com
        name: shadowExpire
        values: ""
        state: exact
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
    - name: Get rid of an unneeded attribute
      ldap_attr:
        dn: uid=jdoe,ou=people,dc=example,dc=com
        name: shadowExpire
        values: ""
        state: exact
        params: "{{ ldap_auth }}"

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
        <td> modlist </td>
        <td> list of modified parameters </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [[2, "olcRootDN", ["cn=root,dc=example,dc=com"]]] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - This only deals with attributes on existing entries. To add or remove whole entries, see :ref:`ldap_entry <ldap_entry>`.
    - The default authentication settings will attempt to use a SASL EXTERNAL bind over a UNIX domain socket. This works well with the default Ubuntu install for example, which includes a cn=peercred,cn=external,cn=auth ACL rule allowing root to modify the server configuration. If you need to use a simple bind to access your server, pass the credentials in *bind_dn* and *bind_pw*.
    - For *state=present* and *state=absent*, all value comparisons are performed on the server for maximum accuracy. For *state=exact*, values have to be compared in Python, which obviously ignores LDAP matching rules. This should work out in most cases, but it is theoretically possible to see spurious changes when target and actual values are semantically identical but lexically distinct.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
