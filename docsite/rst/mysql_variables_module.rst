.. _mysql_variables:


mysql_variables - Manage MySQL global variables
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Query / Set MySQL variables


Requirements (on host that executes module)
-------------------------------------------

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
    <td>config_file<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>~/.my.cnf</td>
        <td><ul></ul></td>
        <td><div>Specify a config file from which user and password are to be read</div></td></tr>
            <tr>
    <td>connect_timeout<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>The connection timeout when connecting to the MySQL server.</div></td></tr>
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
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set, then sets variable value to this</div></td></tr>
            <tr>
    <td>variable<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Variable name to operate</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Check for sync_binlog setting
    - mysql_variables: variable=sync_binlog
    
    # Set read_only variable to 1
    - mysql_variables: variable=read_only value=1


Notes
-----

.. note:: Requires the MySQLdb Python package on the remote host. For Ubuntu, this is as easy as apt-get install python-mysqldb. (See :ref:`apt <apt>`.) For CentOS/Fedora, this is as easy as yum install MySQL-python. (See :ref:`yum <yum>`.)
.. note:: Both ``login_password`` and ``login_user`` are required when you are passing credentials. If none are present, the module will attempt to read the credentials from ``~/.my.cnf``, and finally fall back to using the MySQL default login of 'root' with no password.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

