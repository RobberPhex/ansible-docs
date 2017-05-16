.. _mongodb_user:


mongodb_user - Adds or removes a user from a MongoDB database.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

Adds or removes a user from a MongoDB database.

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
    <td>database</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the database to add/remove the user from</td>
    </tr>
            <tr>
    <td>login_host</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>The host running the database</td>
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
    <td>27017</td>
        <td><ul></ul></td>
        <td>The port to connect to</td>
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
        <td>The name of the user to add or remove</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The password to use for the user</td>
    </tr>
            <tr>
    <td>replica_set</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Replica set to connect to (automatically connects to primary for writes) (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>roles</td>
    <td>no</td>
    <td>readWrite</td>
        <td><ul></ul></td>
        <td>The database user roles valid values are one or more of the following: read, 'readWrite', 'dbAdmin', 'userAdmin', 'clusterAdmin', 'readAnyDatabase', 'readWriteAnyDatabase', 'userAdminAnyDatabase', 'dbAdminAnyDatabase'This param requires mongodb 2.4+ and pymongo 2.5+ (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>ssl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether to use an SSL connection when connecting to the database (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>The database user state</td>
    </tr>
        </table>


.. note:: Requires pymongo


Examples
--------

.. raw:: html

    <br/>


::

    # Create 'burgers' database user with name 'bob' and password '12345'.
    - mongodb_user: database=burgers name=bob password=12345 state=present
    
    # Create a database user via SSL (MongoDB must be compiled with the SSL option and configured properly)
    - mongodb_user: database=burgers name=bob password=12345 state=present ssl=True
    
    # Delete 'burgers' database user with name 'bob'.
    - mongodb_user: database=burgers name=bob state=absent
    
    # Define more users with various specific roles (if not defined, no roles is assigned, and the user will be added via pre mongo 2.2 style)
    - mongodb_user: database=burgers name=ben password=12345 roles='read' state=present
    - mongodb_user: database=burgers name=jim password=12345 roles='readWrite,dbAdmin,userAdmin' state=present
    - mongodb_user: database=burgers name=joe password=12345 roles='readWriteAnyDatabase' state=present
    
    # add a user to database in a replica set, the primary server is automatically discovered and written to
    - mongodb_user: database=burgers name=bob replica_set=blecher password=12345 roles='readWriteAnyDatabase' state=present

.. note:: Requires the pymongo Python package on the remote host, version 2.4.2+. This can be installed using pip or the OS package manager. @see http://api.mongodb.org/python/current/installation.html


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

