.. _vertica_user:


vertica_user - Adds or removes Vertica database users and assigns roles.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds or removes Vertica database user and, optionally, assigns roles.
A user will not be removed until all the dependencies have been dropped.
In such a situation, if the module tries to remove the user it will fail and only remove roles granted to the user.


Requirements
------------

  * unixODBC
  * pyodbc


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
    <td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>Name of the Vertica cluster.</div></td></tr>
            <tr>
    <td>db<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the Vertica database.</div></td></tr>
            <tr>
    <td>expired<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets the user's password expiration.</div></td></tr>
            <tr>
    <td>ldap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set to true if users are authenticated via LDAP.</div><div>The user will be created with password expired and set to <em>$ldap$</em>.</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password used to authenticate with.</div></td></tr>
            <tr>
    <td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>dbadmin</td>
        <td><ul></ul></td>
        <td><div>The username used to authenticate with.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the user to add or remove.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The user's password encrypted by the MD5 algorithm.</div><div>The password must be generated with the format <code>"md5" + md5[password + username]</code>, resulting in a total of 35 characters. An easy way to do this is by querying the Vertica database with select 'md5'||md5('&lt;user_password&gt;&lt;user_name&gt;').</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5433</td>
        <td><ul></ul></td>
        <td><div>Vertica cluster port to connect to.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets the user's profile.</div></td></tr>
            <tr>
    <td>resource_pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets the user's resource pool.</div></td></tr>
            <tr>
    <td>roles<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comma separated list of roles to assign to the user.</div></br>
        <div style="font-size: small;">aliases: role<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>locked</li></ul></td>
        <td><div>Whether to create <code>present</code>, drop <code>absent</code> or lock <code>locked</code> a user.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: creating a new vertica user with password
      vertica_user: name=user_name password=md5<encrypted_password> db=db_name state=present
    
    - name: creating a new vertica user authenticated via ldap with roles assigned
      vertica_user:
        name=user_name
        ldap=true
        db=db_name
        roles=schema_name_ro
        state=present


Notes
-----

.. note:: The default authentication assumes that you are either logging in as or sudo'ing to the ``dbadmin`` account on the host.
.. note:: This module uses ``pyodbc``, a Python ODBC database adapter. You must ensure that ``unixODBC`` and ``pyodbc`` is installed on the host and properly configured.
.. note:: Configuring ``unixODBC`` for Vertica requires ``Driver = /opt/vertica/lib64/libverticaodbc.so`` to be added to the ``Vertica`` section of either ``/etc/odbcinst.ini`` or ``$HOME/.odbcinst.ini`` and both ``ErrorMessagesPath = /opt/vertica/lib64`` and ``DriverManagerEncoding = UTF-16`` to be added to the ``Driver`` section of either ``/etc/vertica.ini`` or ``$HOME/.vertica.ini``.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

