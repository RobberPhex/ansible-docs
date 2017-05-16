.. _mongodb_user:


mongodb_user - Adds or removes a user from a MongoDB database.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds or removes a user from a MongoDB database.


Requirements
------------

  * pymongo


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
    <td>database<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the database to add/remove the user from</div></td></tr>
            <tr>
    <td>login_database<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The database where login credentials are stored</div></td></tr>
            <tr>
    <td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>The host running the database</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password used to authenticate with</div></td></tr>
            <tr>
    <td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>27017</td>
        <td><ul></ul></td>
        <td><div>The port to connect to</div></td></tr>
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
        <td><div>The name of the user to add or remove</div></br>
        <div style="font-size: small;">aliases: user<div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password to use for the user</div></td></tr>
            <tr>
    <td>replica_set<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Replica set to connect to (automatically connects to primary for writes)</div></td></tr>
            <tr>
    <td>roles<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>readWrite</td>
        <td><ul></ul></td>
        <td><div>The database user roles valid values are one or more of the following: read, 'readWrite', 'dbAdmin', 'userAdmin', 'clusterAdmin', 'readAnyDatabase', 'readWriteAnyDatabase', 'userAdminAnyDatabase', 'dbAdminAnyDatabase'</div><div>This param requires mongodb 2.4+ and pymongo 2.5+</div></td></tr>
            <tr>
    <td>ssl<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether to use an SSL connection when connecting to the database</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The database user state</div></td></tr>
            <tr>
    <td>update_password<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>always</td>
        <td><ul><li>always</li><li>on_create</li></ul></td>
        <td><div><code>always</code> will update passwords if they differ.  <code>on_create</code> will only set the password for newly created users.</div></td></tr>
        </table>
    </br>



Examples
--------

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


Notes
-----

.. note:: Requires the pymongo Python package on the remote host, version 2.4.2+. This can be installed using pip or the OS package manager. @see http://api.mongodb.org/python/current/installation.html


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

