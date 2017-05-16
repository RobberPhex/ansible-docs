.. _mysql_db:


mysql_db - Add or remove MySQL databases from a remote host.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove MySQL databases from a remote host.


Requirements
------------

  * MySQLdb


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
    <td>collation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Collation mode (sorting). This only applies to new table/databases and does not update existing ones, this is a limitation of MySQL.</div></td></tr>
            <tr>
    <td>config_file<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>~/.my.cnf</td>
        <td><ul></ul></td>
        <td><div>Specify a config file from which user and password are to be read</div></td></tr>
            <tr>
    <td>encoding<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Encoding mode</div></td></tr>
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
    <td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3306</td>
        <td><ul></ul></td>
        <td><div>Port of the MySQL server. Requires login_host be defined as other then localhost if login_port is used</div></td></tr>
            <tr>
    <td>login_unix_socket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to a Unix domain socket for local connections</div></td></tr>
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
        <td><div>name of the database to add or remove</div><div>name=all May only be provided if <em>state</em> is <code>dump</code> or <code>import</code>.</div><div>if name=all Works like --all-databases option for mysqldump (Added in 2.0)</div></br>
        <div style="font-size: small;">aliases: db<div></td></tr>
            <tr>
    <td>ssl_ca<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to a Certificate Authority (CA) certificate. This option, if used, must specify the same certificate as used by the server.</div></td></tr>
            <tr>
    <td>ssl_cert<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to a client public key certificate.</div></td></tr>
            <tr>
    <td>ssl_key<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to the client private key.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>dump</li><li>import</li></ul></td>
        <td><div>The database state</div></td></tr>
            <tr>
    <td>target<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Location, on the remote host, of the dump file to read from or write to. Uncompressed SQL files (<code>.sql</code>) as well as bzip2 (<code>.bz2</code>), gzip (<code>.gz</code>) and xz (Added in 2.0) compressed files are supported.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new database with name 'bobdata'
    - mysql_db: name=bobdata state=present
    
    # Copy database dump file to remote host and restore it to database 'my_db'
    - copy: src=dump.sql.bz2 dest=/tmp
    - mysql_db: name=my_db state=import target=/tmp/dump.sql.bz2
    
    # Dumps all databases to hostname.sql
    - mysql_db: state=dump name=all target=/tmp/{{ inventory_hostname }}.sql
    
    # Imports file.sql similiar to mysql -u <username> -p <password> < hostname.sql
    - mysql_db: state=import name=all target=/tmp/{{ inventory_hostname }}.sql


Notes
-----

.. note:: Requires the MySQLdb Python package on the remote host. For Ubuntu, this is as easy as apt-get install python-mysqldb. (See :ref:`apt <apt>`.) For CentOS/Fedora, this is as easy as yum install MySQL-python. (See :ref:`yum <yum>`.)
.. note:: Both ``login_password`` and ``login_user`` are required when you are passing credentials. If none are present, the module will attempt to read the credentials from ``~/.my.cnf``, and finally fall back to using the MySQL default login of 'root' with no password.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

