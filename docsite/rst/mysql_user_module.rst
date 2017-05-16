.. _mysql_user:


mysql_user - Adds or removes a user from a MySQL database.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Adds or removes a user from a MySQL database.

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
    <td>append_privs</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Append the privileges defined by priv to the existing ones for this user instead of overwriting existing ones. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>check_implicit_admin</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Check if mysql allows login as root/nopassword before trying supplied credentials. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>host</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>the 'host' part of the MySQL username</td>
    </tr>
            <tr>
    <td>login_host</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>Host running the database</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The password used to authenticate with</td>
    </tr>
            <tr>
    <td>login_port</td>
    <td>no</td>
    <td>3306</td>
        <td><ul></ul></td>
        <td>Port of the MySQL server (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>login_unix_socket</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The path to a Unix domain socket for local connections</td>
    </tr>
            <tr>
    <td>login_user</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The username used to authenticate with</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the user (role) to add or remove</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>set the user's password</td>
    </tr>
            <tr>
    <td>priv</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>MySQL privileges string in the format: <code>db.table:priv1,priv2</code></td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether the user should exist.  When <code>absent</code>, removes the user.</td>
    </tr>
        </table>


.. note:: Requires ConfigParser


.. note:: Requires MySQLdb


Examples
--------

.. raw:: html

    <br/>


::

    # Create database user with name 'bob' and password '12345' with all database privileges
    - mysql_user: name=bob password=12345 priv=*.*:ALL state=present
    
    # Creates database user 'bob' and password '12345' with all database privileges and 'WITH GRANT OPTION'
    - mysql_user: name=bob password=12345 priv=*.*:ALL,GRANT state=present
    
    # Modifiy user Bob to require SSL connections. Note that REQUIRESSL is a special privilege that should only apply to *.* by itself.
    - mysql_user: name=bob append=true priv=*.*:REQUIRESSL state=present
    
    # Ensure no user named 'sally' exists, also passing in the auth credentials.
    - mysql_user: login_user=root login_password=123456 name=sally state=absent
    
    # Specify grants composed of more than one word
    - mysql_user: name=replication password=12345 priv=*.*:"REPLICATION CLIENT" state=present
    
    # Revoke all privileges for user 'bob' and password '12345' 
    - mysql_user: name=bob password=12345 priv=*.*:USAGE state=present
    
    # Example privileges string format
    mydb.*:INSERT,UPDATE/anotherdb.*:SELECT/yetanotherdb.*:ALL
    
    # Example using login_unix_socket to connect to server
    - mysql_user: name=root password=abc123 login_unix_socket=/var/run/mysqld/mysqld.sock
    
    # Example .my.cnf file for setting the root password
    # Note: don't use quotes around the password, because the mysql_user module
    # will include them in the password but the mysql client will not
    
    [client]
    user=root
    password=n<_665{vS43y

.. note:: Requires the MySQLdb Python package on the remote host. For Ubuntu, this is as easy as apt-get install python-mysqldb.
.. note:: Both ``login_password`` and ``login_username`` are required when you are passing credentials. If none are present, the module will attempt to read the credentials from ``~/.my.cnf``, and finally fall back to using the MySQL default login of 'root' with no password.
.. note:: MySQL server installs with default login_user of 'root' and no password. To secure this user as part of an idempotent playbook, you must create at least two tasks: the first must change the root user's password, without providing any login_user/login_password details. The second must drop a ~/.my.cnf file containing the new root credentials. Subsequent runs of the playbook will then succeed by reading the new credentials from the file.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

