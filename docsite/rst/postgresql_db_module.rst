.. _postgresql_db:


postgresql_db - Add or remove PostgreSQL databases from a remote host.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove PostgreSQL databases from a remote host.


Requirements
------------

  * psycopg2


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
    <td>encoding<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Encoding of the database</div></td></tr>
            <tr>
    <td>lc_collate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Collation order (LC_COLLATE) to use in the database. Must match collation order of template database unless <code>template0</code> is used as template.</div></td></tr>
            <tr>
    <td>lc_ctype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Character classification (LC_CTYPE) to use in the database (e.g. lower, upper, ...) Must match LC_CTYPE of template database unless <code>template0</code> is used as template.</div></td></tr>
            <tr>
    <td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>Host running the database</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password used to authenticate with</div></td></tr>
            <tr>
    <td>login_unix_socket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to a Unix domain socket for local connections</div></td></tr>
            <tr>
    <td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username used to authenticate with</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the database to add or remove</div></td></tr>
            <tr>
    <td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the role to set as owner of the database</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5432</td>
        <td><ul></ul></td>
        <td><div>Database port to connect to.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The database state</div></td></tr>
            <tr>
    <td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Template used to create the database</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new database with name "acme"
    - postgresql_db: name=acme
    
    # Create a new database with name "acme" and specific encoding and locale
    # settings. If a template different from "template0" is specified, encoding
    # and locale settings must match those of the template.
    - postgresql_db: name=acme
                     encoding='UTF-8'
                     lc_collate='de_DE.UTF-8'
                     lc_ctype='de_DE.UTF-8'
                     template='template0'


Notes
-----

.. note:: The default authentication assumes that you are either logging in as or sudo'ing to the ``postgres`` account on the host.
.. note:: This module uses *psycopg2*, a Python PostgreSQL database adapter. You must ensure that psycopg2 is installed on the host before using this module. If the remote host is the PostgreSQL server (which is the default case), then PostgreSQL must also be installed on the remote host. For Ubuntu-based systems, install the ``postgresql``, ``libpq-dev``, and ``python-psycopg2`` packages on the remote host before using this module.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

