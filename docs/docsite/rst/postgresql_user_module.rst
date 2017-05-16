.. _postgresql_user:


postgresql_user - Adds or removes a users (roles) from a PostgreSQL database.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove PostgreSQL users (roles) from a remote host and, optionally, grant the users access to an existing database or tables.
* The fundamental function of the module is to create, or delete, roles from a PostgreSQL cluster. Privilege assignment, or removal, is an optional step, which works on one database at a time. This allows for the module to be called several times in the same module to modify the permissions on different databases, or to grant permissions to already existing users.
* A user cannot be removed until all the privileges have been stripped from the user. In such situation, if the module tries to remove the user it will fail. To avoid this from happening the fail_on_user option signals the module to try to remove the user, but if not possible keep going; the module will report if changes happened and separately if the user was removed or not.


Requirements (on host that executes module)
-------------------------------------------

  * psycopg2


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
                <tr><td>db<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>name of database where permissions will be granted</div>        </td></tr>
                <tr><td>encrypted<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>whether the password is stored hashed in the database. boolean. Passwords can be passed already hashed or unhashed, and postgresql ensures the stored password is hashed when encrypted is set.</div>        </td></tr>
                <tr><td>expires<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>sets the user's password expiration.</div>        </td></tr>
                <tr><td>fail_on_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>yes</code>, fail when user can't be removed. Otherwise just log and continue</div>        </td></tr>
                <tr><td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>Host running PostgreSQL.</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password used to authenticate with PostgreSQL</div>        </td></tr>
                <tr><td>login_unix_socket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to a Unix domain socket for local connections</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>postgres</td>
        <td></td>
        <td><div>User (role) used to authenticate with PostgreSQL</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the user (role) to add or remove</div>        </td></tr>
                <tr><td>no_password_changes<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>yes</code>, don't inspect database for password changes. Effective when <code>pg_authid</code> is not accessible (such as AWS RDS). Otherwise, make password changes as necessary.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>set the user's password, before 1.4 this was required.</div><div>When passing an encrypted password, the encrypted parameter must also be true, and it must be generated with the format <code>'str["md5"] + md5[ password + username ]'</code>, resulting in a total of 35 characters.  An easy way to do this is: <code>echo "md5`echo -n "verysecretpasswordJOE" | md5`"</code>. Note that if encrypted is set, the stored password will be hashed whether or not it is pre-encrypted.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5432</td>
        <td></td>
        <td><div>Database port to connect to.</div>        </td></tr>
                <tr><td>priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>PostgreSQL privileges string in the format: <code>table:priv1,priv2</code></div>        </td></tr>
                <tr><td>role_attr_flags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>[NO]SUPERUSER</li><li>[NO]CREATEROLE</li><li>[NO]CREATEUSER</li><li>[NO]CREATEDB</li><li>[NO]INHERIT</li><li>[NO]LOGIN</li><li>[NO]REPLICATION</li></ul></td>
        <td><div>PostgreSQL role attributes string in the format: CREATEDB,CREATEROLE,SUPERUSER</div>        </td></tr>
                <tr><td>ssl_mode<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>prefer</td>
        <td><ul><li>disable</li><li>allow</li><li>prefer</li><li>require</li><li>verify-ca</li><li>verify-full</li></ul></td>
        <td><div>Determines whether or with what priority a secure SSL TCP/IP connection will be negotiated with the server.</div><div>See https://www.postgresql.org/docs/current/static/libpq-ssl.html for more information on the modes.</div><div>Default of <code>prefer</code> matches libpq default.</div>        </td></tr>
                <tr><td>ssl_rootcert<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the name of a file containing SSL certificate authority (CA) certificate(s). If the file exists, the server's certificate will be verified to be signed by one of these authorities.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The user (role) state</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create django user and grant access to database and products table
    - postgresql_user:
        db: acme
        name: django
        password: ceec4eif7ya
        priv: "CONNECT/products:ALL"
    
    # Create rails user, grant privilege to create other databases and demote rails from super user status
    - postgresql_user:
        name: rails
        password: secret
        role_attr_flags: CREATEDB,NOSUPERUSER
    
    # Remove test user privileges from acme
    - postgresql_user:
        db: acme
        name: test
        priv: "ALL/products:ALL"
        state: absent
        fail_on_user: no
    
    # Remove test user from test database and the cluster
    - postgresql_user:
        db: test
        name: test
        priv: ALL
        state: absent
    
    # Example privileges string format
    # INSERT,UPDATE/table:SELECT/anothertable:ALL
    
    # Remove an existing user's password
    - postgresql_user:
        db: test
        user: test
        password: NULL


Notes
-----

.. note::
    - The default authentication assumes that you are either logging in as or sudo'ing to the postgres account on the host.
    - This module uses psycopg2, a Python PostgreSQL database adapter. You must ensure that psycopg2 is installed on the host before using this module. If the remote host is the PostgreSQL server (which is the default case), then PostgreSQL must also be installed on the remote host. For Ubuntu-based systems, install the postgresql, libpq-dev, and python-psycopg2 packages on the remote host before using this module.
    - If the passlib library is installed, then passwords that are encrypted in the DB but not encrypted when passed as arguments can be checked for changes. If the passlib library is not installed, unencrypted passwords stored in the DB encrypted will be assumed to have changed.
    - If you specify PUBLIC as the user, then the privilege changes will apply to all users. You may not specify password or role_attr_flags when the PUBLIC user is specified.
    - The ssl_rootcert parameter requires at least Postgres version 8.4 and *psycopg2* version 2.4.3.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
