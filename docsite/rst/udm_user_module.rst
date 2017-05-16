.. _udm_user:


udm_user - Manage posix users on a univention corporate server
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows to manage posix users on a univention corporate server (UCS). It uses the python API of the UCS to create a new object or edit it.


Requirements (on host that executes module)
-------------------------------------------

  * Python >= 2.6


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
    <td>birthday<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Birthday</div></td></tr>
            <tr>
    <td>city<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>City of users business address.</div></td></tr>
            <tr>
    <td>country<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Country of users business address.</div></td></tr>
            <tr>
    <td>department_number<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Department number of users business address.</div></br>
        <div style="font-size: small;">aliases: departmentNumber<div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Description (not gecos)</div></td></tr>
            <tr>
    <td>display_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Display name (not gecos)</div></br>
        <div style="font-size: small;">aliases: displayName<div></td></tr>
            <tr>
    <td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'']</td>
        <td><ul></ul></td>
        <td><div>A list of e-mail addresses.</div></td></tr>
            <tr>
    <td>employee_number<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Employee number</div></br>
        <div style="font-size: small;">aliases: employeeNumber<div></td></tr>
            <tr>
    <td>employee_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Employee type</div></br>
        <div style="font-size: small;">aliases: employeeType<div></td></tr>
            <tr>
    <td>firstname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>First name. Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>gecos<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>GECOS</div></td></tr>
            <tr>
    <td>groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>POSIX groups, the LDAP DNs of the groups will be found with the LDAP filter for each group as $GROUP: <code>(&amp;(objectClass=posixGroup</code>(cn=$GROUP))).</div></td></tr>
            <tr>
    <td>home_share<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Home NFS share. Must be a LDAP DN, e.g. <code>cn=home,cn=shares,ou=school,dc=example,dc=com</code>.</div></br>
        <div style="font-size: small;">aliases: homeShare<div></td></tr>
            <tr>
    <td>home_share_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Path to home NFS share, inside the homeShare.</div></br>
        <div style="font-size: small;">aliases: homeSharePath<div></td></tr>
            <tr>
    <td>home_telephone_number<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of private telephone numbers.</div></br>
        <div style="font-size: small;">aliases: homeTelephoneNumber<div></td></tr>
            <tr>
    <td>homedrive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Windows home drive, e.g. <code>"H:"</code>.</div></td></tr>
            <tr>
    <td>lastname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Last name. Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>mail_alternative_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of alternative e-mail addresses.</div></br>
        <div style="font-size: small;">aliases: mailAlternativeAddress<div></td></tr>
            <tr>
    <td>mail_home_server<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>FQDN of mail server</div></br>
        <div style="font-size: small;">aliases: mailHomeServer<div></td></tr>
            <tr>
    <td>mail_primary_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Primary e-mail address</div></br>
        <div style="font-size: small;">aliases: mailPrimaryAddress<div></td></tr>
            <tr>
    <td>mobile_telephone_number<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Mobile phone number</div></br>
        <div style="font-size: small;">aliases: mobileTelephoneNumber<div></td></tr>
            <tr>
    <td>organisation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Organisation</div></td></tr>
            <tr>
    <td>ou<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Organizational Unit inside the LDAP Base DN, e.g. <code>school</code> for LDAP OU <code>ou=school,dc=example,dc=com</code>.</div></td></tr>
            <tr>
    <td>override_pw_history<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Override password history</div></br>
        <div style="font-size: small;">aliases: overridePWHistory<div></td></tr>
            <tr>
    <td>override_pw_length<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Override password check</div></br>
        <div style="font-size: small;">aliases: overridePWLength<div></td></tr>
            <tr>
    <td>pager_telephonenumber<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of pager telephone numbers.</div></br>
        <div style="font-size: small;">aliases: pagerTelephonenumber<div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Password. Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>phone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of telephone numbers.</div></td></tr>
            <tr>
    <td>position<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Define the whole position of users object inside the LDAP tree, e.g. <code>cn=employee,cn=users,ou=school,dc=example,dc=com</code>.</div></td></tr>
            <tr>
    <td>postcode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Postal code of users business address.</div></td></tr>
            <tr>
    <td>primary_group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cn=Domain Users,cn=groups,$LDAP_BASE_DN</td>
        <td><ul></ul></td>
        <td><div>Primary group. This must be the group LDAP DN.</div></br>
        <div style="font-size: small;">aliases: primaryGroup<div></td></tr>
            <tr>
    <td>profilepath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Windows profile directory</div></td></tr>
            <tr>
    <td>pwd_change_next_login<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Change password on next login.</div></br>
        <div style="font-size: small;">aliases: pwdChangeNextLogin<div></td></tr>
            <tr>
    <td>room_number<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Room number of users business address.</div></br>
        <div style="font-size: small;">aliases: roomNumber<div></td></tr>
            <tr>
    <td>samba_privileges<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Samba privilege, like allow printer administration, do domain join.</div></br>
        <div style="font-size: small;">aliases: sambaPrivileges<div></td></tr>
            <tr>
    <td>samba_user_workstations<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Allow the authentication only on this Microsoft Windows host.</div></br>
        <div style="font-size: small;">aliases: sambaUserWorkstations<div></td></tr>
            <tr>
    <td>sambahome<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Windows home path, e.g. <code>'\\$FQDN\$USERNAME'</code>.</div></td></tr>
            <tr>
    <td>scriptpath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Windows logon script.</div></td></tr>
            <tr>
    <td>secretary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of superiors as LDAP DNs.</div></td></tr>
            <tr>
    <td>serviceprovider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'']</td>
        <td><ul></ul></td>
        <td><div>Enable user for the following service providers.</div></td></tr>
            <tr>
    <td>shell<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/bin/bash</td>
        <td><ul></ul></td>
        <td><div>Login shell</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the user is present or not.</div></td></tr>
            <tr>
    <td>street<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Street of users business address.</div></td></tr>
            <tr>
    <td>subpath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cn=users</td>
        <td><ul></ul></td>
        <td><div>LDAP subpath inside the organizational unit, e.g. <code>cn=teachers,cn=users</code> for LDAP container <code>cn=teachers,cn=users,dc=example,dc=com</code>.</div></td></tr>
            <tr>
    <td>title<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Title, e.g. <code>Prof.</code>.</div></td></tr>
            <tr>
    <td>unixhome<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/home/$USERNAME</td>
        <td><ul></ul></td>
        <td><div>Unix home directory</div></td></tr>
            <tr>
    <td>userexpiry<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Today + 1 year</td>
        <td><ul></ul></td>
        <td><div>Account expiry date, e.g. <code>1999-12-31</code>.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>User name</div></br>
        <div style="font-size: small;">aliases: name<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a user on a UCS
    - udm_user: name=FooBar
                password=secure_password
                firstname=Foo
                lastname=Bar
    
    # Create a user with the DN
    # C(uid=foo,cn=teachers,cn=users,ou=school,dc=school,dc=example,dc=com)
    - udm_user: name=foo
                password=secure_password
                firstname=Foo
                lastname=Bar
                ou=school
                subpath='cn=teachers,cn=users'
    # or define the position
    - udm_user: name=foo
                password=secure_password
                firstname=Foo
                lastname=Bar
                position='cn=teachers,cn=users,ou=school,dc=school,dc=example,dc=com'




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

