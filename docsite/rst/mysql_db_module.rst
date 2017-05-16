.. _mysql_db:


mysql_db - Add or remove MySQL databases from a remote host.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Add or remove MySQL databases from a remote host.

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
    <td>collation</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Collation mode</td>
    </tr>
            <tr>
    <td>encoding</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Encoding mode</td>
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
        <td>Port of the MySQL server. Requires login_host be defined as other then localhost if login_port is used</td>
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
        <td>name of the database to add or remove</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>dump</li><li>import</li></ul></td>
        <td>The database state</td>
    </tr>
            <tr>
    <td>target</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Location, on the remote host, of the dump file to read from or write to. Uncompressed SQL files (<code>.sql</code>) as well as bzip2 (<code>.bz2</code>) and gzip (<code>.gz</code>) compressed files are supported.</td>
    </tr>
        </table>


.. note:: Requires ConfigParser


Examples
--------

.. raw:: html

    <br/>


::

    # Create a new database with name 'bobdata'
    - mysql_db: name=bobdata state=present
    
    # Copy database dump file to remote host and restore it to database 'my_db'
    - copy: src=dump.sql.bz2 dest=/tmp
    - mysql_db: name=my_db state=import target=/tmp/dump.sql.bz2

.. note:: Requires the MySQLdb Python package on the remote host. For Ubuntu, this is as easy as apt-get install python-mysqldb. (See ``apt``.)
.. note:: Both *login_password* and *login_user* are required when you are passing credentials. If none are present, the module will attempt to read the credentials from ``~/.my.cnf``, and finally fall back to using the MySQL default login of ``root`` with no password.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

