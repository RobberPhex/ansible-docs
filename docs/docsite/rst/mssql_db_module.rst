.. _mssql_db:


mssql_db - Add or remove MSSQL databases from a remote host.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove MSSQL databases from a remote host.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * pymssql


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
                <tr><td>autocommit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>false</li><li>true</li></ul></td>
        <td><div>Automatically commit the change only if the import succeed. Sometimes it is necessary to use autocommit=true, since some content can't be changed within a transaction.</div>        </td></tr>
                <tr><td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host running the database</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password used to authenticate with</div>        </td></tr>
                <tr><td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1433</td>
        <td></td>
        <td><div>Port of the MSSQL server. Requires login_host be defined as other then localhost if login_port is used</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username used to authenticate with</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the database to add or remove</div></br>
    <div style="font-size: small;">aliases: db<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>import</li></ul></td>
        <td><div>The database state</div>        </td></tr>
                <tr><td>target<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Location, on the remote host, of the dump file to read from or write to. Uncompressed SQL files (<code>.sql</code>) files are supported.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new database with name 'jackdata'
    - mssql_db:
        name: jackdata
        state: present
    
    # Copy database dump file to remote host and restore it to database 'my_db'
    - copy:
        src: dump.sql
        dest: /tmp
    
    - mssql_db:
        name: my_db
        state: import
        target: /tmp/dump.sql


Notes
-----

.. note::
    - Requires the pymssql Python package on the remote host. For Ubuntu, this is as easy as pip install pymssql (See :ref:`pip <pip>`.)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
