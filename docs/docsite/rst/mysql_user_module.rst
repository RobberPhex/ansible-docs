.. _mysql_user:


mysql_user - Adds or removes a user from a MySQL database.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Adds or removes a user from a MySQL database.


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
                <tr><td>append_privs<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Append the privileges defined by priv to the existing ones for this user instead of overwriting existing ones.</div>        </td></tr>
                <tr><td>check_implicit_admin<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Check if mysql allows login as root/nopassword before trying supplied credentials.</div>        </td></tr>
                <tr><td>config_file<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>~/.my.cnf</td>
        <td></td>
        <td><div>Specify a config file from which user and password are to be read.</div>        </td></tr>
                <tr><td>connect_timeout<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>The connection timeout when connecting to the MySQL server.</div>        </td></tr>
                <tr><td>encrypted<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Indicate that the 'password' field is a `mysql_native_password` hash</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>the 'host' part of the MySQL username</div>        </td></tr>
                <tr><td>host_all<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>override the host option, making ansible apply changes to all hostnames for a given user.  This option cannot be used when creating users</div>        </td></tr>
                <tr><td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>Host running the database.</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password used to authenticate with.</div>        </td></tr>
                <tr><td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3306</td>
        <td></td>
        <td><div>Port of the MySQL server. Requires <em>login_host</em> be defined as other then localhost if login_port is used.</div>        </td></tr>
                <tr><td>login_unix_socket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to a Unix domain socket for local connections.</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username used to authenticate with.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the user (role) to add or remove</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>set the user's password.</div>        </td></tr>
                <tr><td>priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>MySQL privileges string in the format: <code>db.table:priv1,priv2</code>.</div><div>Multiple privileges can be specified by separating each one using a forward slash: <code>db.table:priv/db.table:priv</code>.</div><div>The format is based on MySQL <code>GRANT</code> statement.</div><div>Database and table names can be quoted, MySQL-style.</div><div>If column privileges are used, the <code>priv1,priv2</code> part must be exactly as returned by a <code>SHOW GRANT</code> statement. If not followed, the module will always report changes. It includes grouping columns by permission (<code>SELECT(col1,col2</code>) instead of <code>SELECT(col1</code>,SELECT(col2))).</div>        </td></tr>
                <tr><td>sql_log_bin<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether binary logging should be enabled or disabled for the connection.</div>        </td></tr>
                <tr><td>ssl_ca<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to a Certificate Authority (CA) certificate. This option, if used, must specify the same certificate as used by the server.</div>        </td></tr>
                <tr><td>ssl_cert<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to a client public key certificate.</div>        </td></tr>
                <tr><td>ssl_key<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to the client private key.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the user should exist.  When <code>absent</code>, removes the user.</div>        </td></tr>
                <tr><td>update_password<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>always</td>
        <td><ul><li>always</li><li>on_create</li></ul></td>
        <td><div><code>always</code> will update passwords if they differ.  <code>on_create</code> will only set the password for newly created users.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Removes anonymous user account for localhost
    - mysql_user:
        name: ''
        host: localhost
        state: absent
    
    # Removes all anonymous user accounts
    - mysql_user:
        name: ''
        host_all: yes
        state: absent
    
    # Create database user with name 'bob' and password '12345' with all database privileges
    - mysql_user:
        name: bob
        password: 12345
        priv: '*.*:ALL'
        state: present
    
    # Create database user with name 'bob' and previously hashed mysql native password '*EE0D72C1085C46C5278932678FBE2C6A782821B4' with all database privileges
    - mysql_user:
        name: bob
        password: '*EE0D72C1085C46C5278932678FBE2C6A782821B4'
        encrypted: yes
        priv: '*.*:ALL'
        state: present
    
    # Creates database user 'bob' and password '12345' with all database privileges and 'WITH GRANT OPTION'
    - mysql_user:
        name: bob
        password: 12345
        priv: '*.*:ALL,GRANT'
        state: present
    
    # Modify user Bob to require SSL connections. Note that REQUIRESSL is a special privilege that should only apply to *.* by itself.
    - mysql_user:
        name: bob
        append_privs: true
        priv: '*.*:REQUIRESSL'
        state: present
    
    # Ensure no user named 'sally'@'localhost' exists, also passing in the auth credentials.
    - mysql_user:
        login_user: root
        login_password: 123456
        name: sally
        state: absent
    
    # Ensure no user named 'sally' exists at all
    - mysql_user:
        name: sally
        host_all: yes
        state: absent
    
    # Specify grants composed of more than one word
    - mysql_user:
        name: replication
        password: 12345
        priv: "*.*:REPLICATION CLIENT"
        state: present
    
    # Revoke all privileges for user 'bob' and password '12345'
    - mysql_user:
        name: bob
        password: 12345
        priv: "*.*:USAGE"
        state: present
    
    # Example privileges string format
    # mydb.*:INSERT,UPDATE/anotherdb.*:SELECT/yetanotherdb.*:ALL
    
    # Example using login_unix_socket to connect to server
    - mysql_user:
        name: root
        password: abc123
        login_unix_socket: /var/run/mysqld/mysqld.sock
    
    # Example of skipping binary logging while adding user 'bob'
    - mysql_user:
        name: bob
        password: 12345
        priv: "*.*:USAGE"
        state: present
        sql_log_bin: no
    
    # Example .my.cnf file for setting the root password
    # [client]
    # user=root
    # password=n<_665{vS43y


Notes
-----

.. note::
    - MySQL server installs with default login_user of 'root' and no password. To secure this user as part of an idempotent playbook, you must create at least two tasks: the first must change the root user's password, without providing any login_user/login_password details. The second must drop a ~/.my.cnf file containing the new root credentials. Subsequent runs of the playbook will then succeed by reading the new credentials from the file.
    - Currently, there is only support for the `mysql_native_password` encrypted password hash module.
    - Requires the MySQLdb Python package on the remote host. For Ubuntu, this is as easy as apt-get install python-mysqldb. (See :ref:`apt <apt>`.) For CentOS/Fedora, this is as easy as yum install MySQL-python. (See :ref:`yum <yum>`.)
    - Both ``login_password`` and ``login_user`` are required when you are passing credentials. If none are present, the module will attempt to read the credentials from ``~/.my.cnf``, and finally fall back to using the MySQL default login of 'root' with no password.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
