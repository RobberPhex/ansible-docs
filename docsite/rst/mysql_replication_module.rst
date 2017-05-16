.. _mysql_replication:


mysql_replication - Manage MySQL replication
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages MySQL server replication, slave, master status get and change master host.


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
    <td>master_auto_position<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>does the host uses GTID based replication or not</div></td></tr>
            <tr>
    <td>master_connect_retry<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_log_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_log_pos<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_ssl_ca<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_ssl_capath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_ssl_cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_ssl_cipher<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_ssl_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>master_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>getslave</td>
        <td><ul><li>getslave</li><li>getmaster</li><li>changemaster</li><li>stopslave</li><li>startslave</li><li>resetslave</li><li>resetslaveall</li></ul></td>
        <td><div>module operating mode. Could be getslave (SHOW SLAVE STATUS), getmaster (SHOW MASTER STATUS), changemaster (CHANGE MASTER TO), startslave (START SLAVE), stopslave (STOP SLAVE), resetslave (RESET SLAVE), resetslaveall (RESET SLAVE ALL)</div></td></tr>
            <tr>
    <td>relay_log_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
            <tr>
    <td>relay_log_pos<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>same as mysql variable</div></td></tr>
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
        </table>
    </br>



Examples
--------

 ::

    # Stop mysql slave thread
    - mysql_replication: mode=stopslave
    
    # Get master binlog file name and binlog position
    - mysql_replication: mode=getmaster
    
    # Change master to master server 192.0.2.1 and use binary log 'mysql-bin.000009' with position 4578
    - mysql_replication: mode=changemaster master_host=192.0.2.1 master_log_file=mysql-bin.000009 master_log_pos=4578
    
    # Check slave status using port 3308
    - mysql_replication: mode=getslave login_host=ansible.example.com login_port=3308


Notes
-----

.. note:: Requires the MySQLdb Python package on the remote host. For Ubuntu, this is as easy as apt-get install python-mysqldb. (See :ref:`apt <apt>`.) For CentOS/Fedora, this is as easy as yum install MySQL-python. (See :ref:`yum <yum>`.)
.. note:: Both ``login_password`` and ``login_user`` are required when you are passing credentials. If none are present, the module will attempt to read the credentials from ``~/.my.cnf``, and finally fall back to using the MySQL default login of 'root' with no password.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

