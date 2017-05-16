.. _udm_group:


udm_group - Manage of the posix group
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows to manage user groups on a univention corporate server (UCS). It uses the python API of the UCS to create a new object or edit it.


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
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Group description.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the posix group.</div></td></tr>
            <tr>
    <td>ou<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>LDAP OU, e.g. school for LDAP OU <code>ou=school,dc=example,dc=com</code>.</div></td></tr>
            <tr>
    <td>position<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>define the whole ldap position of the group, e.g. <code>cn=g123m-1A,cn=classes,cn=schueler,cn=groups,ou=schule,dc=example,dc=com</code>.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the group is present or not.</div></td></tr>
            <tr>
    <td>subpath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Subpath inside the OU, e.g. <code>cn=classes,cn=students,cn=groups</code>.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a POSIX group
    - udm_group: name=g123m-1A
    
    # Create a POSIX group with the exact DN
    # C(cn=g123m-1A,cn=classes,cn=students,cn=groups,ou=school,dc=school,dc=example,dc=com)
    - udm_group: name=g123m-1A
                 subpath='cn=classes,cn=students,cn=groups'
                 ou=school
    # or
    - udm_group: name=g123m-1A
                 position='cn=classes,cn=students,cn=groups,ou=school,dc=school,dc=example,dc=com'




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

