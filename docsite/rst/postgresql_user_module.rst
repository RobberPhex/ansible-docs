.. _postgresql_user:


postgresql_user - Adds or removes a users (roles) from a PostgreSQL database.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Add or remove PostgreSQL users (roles) from a remote host and, optionally, grant the users access to an existing database or tables.
The fundamental function of the module is to create, or delete, roles from a PostgreSQL cluster. Privilege assignment, or removal, is an optional step, which works on one database at a time. This allows for the module to be called several times in the same module to modify the permissions on different databases, or to grant permissions to already existing users.
A user cannot be removed until all the privileges have been stripped from the user. In such situation, if the module tries to remove the user it will fail. To avoid this from happening the fail_on_user option signals the module to try to remove the user, but if not possible keep going; the module will report if changes happened and separately if the user was removed or not.

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
    <td>db</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of database where permissions will be granted</td>
    </tr>
            <tr>
    <td>encrypted</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>denotes if the password is already encrypted. boolean. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>expires</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>sets the user's password expiration. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>fail_on_user</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if <code>yes</code>, fail when user can't be removed. Otherwise just log and continue</td>
    </tr>
            <tr>
    <td>login_host</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>Host running PostgreSQL.</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Password used to authenticate with PostgreSQL</td>
    </tr>
            <tr>
    <td>login_unix_socket</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to a Unix domain socket for local connections</td>
    </tr>
            <tr>
    <td>login_user</td>
    <td>no</td>
    <td>postgres</td>
        <td><ul></ul></td>
        <td>User (role) used to authenticate with PostgreSQL</td>
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
        <td>set the user's password, before 1.4 this was required.When passing an encrypted password, the encrypted parameter must also be true, and it must be generated with the format <code>'str["md5"] + md5[ password + username ]'</code>, resulting in a total of 35 characters.  An easy way to do this is: <code>echo "md5`echo -n "verysecretpasswordJOE" | md5`"</code>.</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>5432</td>
        <td><ul></ul></td>
        <td>Database port to connect to.</td>
    </tr>
            <tr>
    <td>priv</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>PostgreSQL privileges string in the format: <code>table:priv1,priv2</code></td>
    </tr>
            <tr>
    <td>role_attr_flags</td>
    <td>no</td>
    <td></td>
        <td><ul><li>[NO]SUPERUSER</li><li>[NO]CREATEROLE</li><li>[NO]CREATEUSER</li><li>[NO]CREATEDB</li><li>[NO]INHERIT</li><li>[NO]LOGIN</li><li>[NO]REPLICATION</li></ul></td>
        <td>PostgreSQL role attributes string in the format: CREATEDB,CREATEROLE,SUPERUSER</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>The user (role) state</td>
    </tr>
        </table>


.. note:: Requires psycopg2


Examples
--------

.. raw:: html

    <br/>


::

    # Create django user and grant access to database and products table
    - postgresql_user: db=acme name=django password=ceec4eif7ya priv=CONNECT/products:ALL
    
    # Create rails user, grant privilege to create other databases and demote rails from super user status
    - postgresql_user: name=rails password=secret role_attr_flags=CREATEDB,NOSUPERUSER
    
    # Remove test user privileges from acme
    - postgresql_user: db=acme name=test priv=ALL/products:ALL state=absent fail_on_user=no
    
    # Remove test user from test database and the cluster
    - postgresql_user: db=test name=test priv=ALL state=absent
    
    # Example privileges string format
    INSERT,UPDATE/table:SELECT/anothertable:ALL
    
    # Remove an existing user's password
    - postgresql_user: db=test user=test password=NULL

.. note:: The default authentication assumes that you are either logging in as or sudo'ing to the postgres account on the host.
.. note:: This module uses psycopg2, a Python PostgreSQL database adapter. You must ensure that psycopg2 is installed on the host before using this module. If the remote host is the PostgreSQL server (which is the default case), then PostgreSQL must also be installed on the remote host. For Ubuntu-based systems, install the postgresql, libpq-dev, and python-psycopg2 packages on the remote host before using this module.
.. note:: If you specify PUBLIC as the user, then the privilege changes will apply to all users. You may not specify password or role_attr_flags when the PUBLIC user is specified.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

