.. _vertica_schema:


vertica_schema - Adds or removes Vertica database schema and roles.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds or removes Vertica database schema and, optionally, roles with schema access privileges.
A schema will not be removed until all the objects have been dropped.
In such a situation, if the module tries to remove the schema it will fail and only remove roles created for the schema if they have no dependencies.


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
    <td>create_roles<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comma separated list of roles to create and grant usage and create access to the schema.</div></br>
        <div style="font-size: small;">aliases: create_role<div></td></tr>
            <tr>
    <td>db<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the Vertica database.</div></td></tr>
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
        <td><div>Name of the schema to add or remove.</div></td></tr>
            <tr>
    <td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the user to set as owner of the schema.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5433</td>
        <td><ul></ul></td>
        <td><div>Vertica cluster port to connect to.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to create <code>present</code>, or drop <code>absent</code> a schema.</div></td></tr>
            <tr>
    <td>usage_roles<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comma separated list of roles to create and grant usage access to the schema.</div></br>
        <div style="font-size: small;">aliases: usage_role<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: creating a new vertica schema
      vertica_schema: name=schema_name db=db_name state=present
    
    - name: creating a new schema with specific schema owner
      vertica_schema: name=schema_name owner=dbowner db=db_name state=present
    
    - name: creating a new schema with roles
      vertica_schema:
        name=schema_name
        create_roles=schema_name_all
        usage_roles=schema_name_ro,schema_name_rw
        db=db_name
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

