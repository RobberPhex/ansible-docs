.. _mongodb_user:


mongodb_user - Adds or removes a user from a MongoDB database.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Adds or removes a user from a MongoDB database.


Requirements (on host that executes module)
-------------------------------------------

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
                <tr><td>database<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the database to add/remove the user from</div>        </td></tr>
                <tr><td>login_database<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The database where login credentials are stored</div>        </td></tr>
                <tr><td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>The host running the database</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password used to authenticate with</div>        </td></tr>
                <tr><td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>27017</td>
        <td></td>
        <td><div>The port to connect to</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username used to authenticate with</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the user to add or remove</div></br>
    <div style="font-size: small;">aliases: user<div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password to use for the user</div>        </td></tr>
                <tr><td>replica_set<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Replica set to connect to (automatically connects to primary for writes)</div>        </td></tr>
                <tr><td>roles<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>readWrite</td>
        <td></td>
        <td><div>The database user roles valid values could either be one or more of the following strings: 'read', 'readWrite', 'dbAdmin', 'userAdmin', 'clusterAdmin', 'readAnyDatabase', 'readWriteAnyDatabase', 'userAdminAnyDatabase', 'dbAdminAnyDatabase'</div><div>Or the following dictionary '{ db: DATABASE_NAME, role: ROLE_NAME }'.</div><div>This param requires pymongo 2.5+. If it is a string, mongodb 2.4+ is also required. If it is a dictionary, mongo 2.6+  is required.</div>        </td></tr>
                <tr><td>ssl<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether to use an SSL connection when connecting to the database</div>        </td></tr>
                <tr><td>ssl_cert_reqs<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>CERT_REQUIRED</td>
        <td><ul><li>CERT_REQUIRED</li><li>CERT_OPTIONAL</li><li>CERT_NONE</li></ul></td>
        <td><div>Specifies whether a certificate is required from the other side of the connection, and whether it will be validated if provided.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The database user state</div>        </td></tr>
                <tr><td>update_password<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>always</td>
        <td><ul><li>always</li><li>on_create</li></ul></td>
        <td><div><code>always</code> will update passwords if they differ.  <code>on_create</code> will only set the password for newly created users.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create 'burgers' database user with name 'bob' and password '12345'.
    - mongodb_user:
        database: burgers
        name: bob
        password: 12345
        state: present
    
    # Create a database user via SSL (MongoDB must be compiled with the SSL option and configured properly)
    - mongodb_user:
        database: burgers
        name: bob
        password: 12345
        state: present
        ssl: True
    
    # Delete 'burgers' database user with name 'bob'.
    - mongodb_user:
        database: burgers
        name: bob
        state: absent
    
    # Define more users with various specific roles (if not defined, no roles is assigned, and the user will be added via pre mongo 2.2 style)
    - mongodb_user:
        database: burgers
        name: ben
        password: 12345
        roles: read
        state: present
    - mongodb_user:
        database: burgers
        name: jim
        password: 12345
        roles: readWrite,dbAdmin,userAdmin
        state: present
    - mongodb_user:
        database: burgers
        name: joe
        password: 12345
        roles: readWriteAnyDatabase
        state: present
    
    # add a user to database in a replica set, the primary server is automatically discovered and written to
    - mongodb_user:
        database: burgers
        name: bob
        replica_set: belcher
        password: 12345
        roles: readWriteAnyDatabase
        state: present
    
    # add a user 'oplog_reader' with read only access to the 'local' database on the replica_set 'belcher'. This is useful for oplog access (MONGO_OPLOG_URL).
    # please notice the credentials must be added to the 'admin' database because the 'local' database is not syncronized and can't receive user credentials
    # To login with such user, the connection string should be MONGO_OPLOG_URL="mongodb://oplog_reader:oplog_reader_password@server1,server2/local?authSource=admin"
    # This syntax requires mongodb 2.6+ and pymongo 2.5+
    - mongodb_user:
        login_user: root
        login_password: root_password
        database: admin
        user: oplog_reader
        password: oplog_reader_password
        state: present
        replica_set: belcher
        roles:
          - db: local
            role: read
    

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> user </td>
        <td> The name of the user to add or remove. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Requires the pymongo Python package on the remote host, version 2.4.2+. This can be installed using pip or the OS package manager. @see http://api.mongodb.org/python/current/installation.html



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
