.. _postgresql_privs:


postgresql_privs - Grant or revoke privileges on PostgreSQL database objects.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Grant or revoke privileges on PostgreSQL database objects.
This module is basically a wrapper around most of the functionality of PostgreSQL's GRANT and REVOKE statements with detection of changes (GRANT/REVOKE *privs* ON *type* *objs* TO/FROM *roles*)


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
            <tr>
    <td>database<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of database to connect to.</div><div>Alias: <em>db</em></div></td></tr>
            <tr>
    <td>grant_option<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether <code>role</code> may grant/revoke the specified privileges/group memberships to others.</div><div>Set to <code>no</code> to revoke GRANT OPTION, leave unspecified to make no changes.</div><div><em>grant_option</em> only has an effect if <em>state</em> is <code>present</code>.</div><div>Alias: <em>admin_option</em></div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Database host address. If unspecified, connect via Unix socket.</div><div>Alias: <em>login_host</em></div></td></tr>
            <tr>
    <td>login<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>postgres</td>
        <td><ul></ul></td>
        <td><div>The username to authenticate with.</div><div>Alias: <em>login_user</em></div></td></tr>
            <tr>
    <td>objs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comma separated list of database objects to set privileges on.</div><div>If <em>type</em> is <code>table</code> or <code>sequence</code>, the special value <code>ALL_IN_SCHEMA</code> can be provided instead to specify all database objects of type <em>type</em> in the schema specified via <em>schema</em>. (This also works with PostgreSQL &lt; 9.0.)</div><div>If <em>type</em> is <code>database</code>, this parameter can be omitted, in which case privileges are set for the database specified via <em>database</em>.</div><div>If <em>type</em> is <em>function</em>, colons (":") in object names will be replaced with commas (needed to specify function signatures, see examples)</div><div>Alias: <em>obj</em></div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password to authenticate with.</div><div>Alias: <em>login_password</em>)</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5432</td>
        <td><ul></ul></td>
        <td><div>Database port to connect to.</div></td></tr>
            <tr>
    <td>privs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comma separated list of privileges to grant/revoke.</div><div>Alias: <em>priv</em></div></td></tr>
            <tr>
    <td>roles<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comma separated list of role (user/group) names to set permissions for.</div><div>The special value <code>PUBLIC</code> can be provided instead to set permissions for the implicitly defined PUBLIC group.</div><div>Alias: <em>role</em></div></td></tr>
            <tr>
    <td>schema<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Schema that contains the database objects specified via <em>objs</em>.</div><div>May only be provided if <em>type</em> is <code>table</code>, <code>sequence</code> or <code>function</code>. Defaults to  <code>public</code> in these cases.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>If <code>present</code>, the specified privileges are granted, if <code>absent</code> they are revoked.</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>table</td>
        <td><ul><li>table</li><li>sequence</li><li>function</li><li>database</li><li>schema</li><li>language</li><li>tablespace</li><li>group</li></ul></td>
        <td><div>Type of database object to set privileges on.</div></td></tr>
            <tr>
    <td>unix_socket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to a Unix domain socket for local connections.</div><div>Alias: <em>login_unix_socket</em></div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # On database "library":
    # GRANT SELECT, INSERT, UPDATE ON TABLE public.books, public.authors
    # TO librarian, reader WITH GRANT OPTION
    - postgresql_privs: >
        database=library
        state=present
        privs=SELECT,INSERT,UPDATE
        type=table
        objs=books,authors
        schema=public
        roles=librarian,reader
        grant_option=yes
    
    # Same as above leveraging default values:
    - postgresql_privs: >
        db=library
        privs=SELECT,INSERT,UPDATE
        objs=books,authors
        roles=librarian,reader
        grant_option=yes
    
    # REVOKE GRANT OPTION FOR INSERT ON TABLE books FROM reader
    # Note that role "reader" will be *granted* INSERT privilege itself if this
    # isn't already the case (since state=present).
    - postgresql_privs: >
        db=library
        state=present
        priv=INSERT
        obj=books
        role=reader
        grant_option=no
    
    # REVOKE INSERT, UPDATE ON ALL TABLES IN SCHEMA public FROM reader
    # "public" is the default schema. This also works for PostgreSQL 8.x.
    - postgresql_privs: >
        db=library
        state=absent
        privs=INSERT,UPDATE
        objs=ALL_IN_SCHEMA
        role=reader
    
    # GRANT ALL PRIVILEGES ON SCHEMA public, math TO librarian
    - postgresql_privs: >
        db=library
        privs=ALL
        type=schema
        objs=public,math
        role=librarian
    
    # GRANT ALL PRIVILEGES ON FUNCTION math.add(int, int) TO librarian, reader
    # Note the separation of arguments with colons.
    - postgresql_privs: >
        db=library
        privs=ALL
        type=function
        obj=add(int:int)
        schema=math
        roles=librarian,reader
    
    # GRANT librarian, reader TO alice, bob WITH ADMIN OPTION
    # Note that group role memberships apply cluster-wide and therefore are not
    # restricted to database "library" here.
    - postgresql_privs: >
        db=library
        type=group
        objs=librarian,reader
        roles=alice,bob
        admin_option=yes
    
    # GRANT ALL PRIVILEGES ON DATABASE library TO librarian
    # Note that here "db=postgres" specifies the database to connect to, not the
    # database to grant privileges on (which is specified via the "objs" param)
    - postgresql_privs: >
        db=postgres
        privs=ALL
        type=database
        obj=library
        role=librarian
    
    # GRANT ALL PRIVILEGES ON DATABASE library TO librarian
    # If objs is omitted for type "database", it defaults to the database
    # to which the connection is established
    - postgresql_privs: >
        db=library
        privs=ALL
        type=database
        role=librarian


Notes
-----

.. note:: Default authentication assumes that postgresql_privs is run by the ``postgres`` user on the remote host. (Ansible's ``user`` or ``sudo-user``).
.. note:: This module requires Python package *psycopg2* to be installed on the remote host. In the default case of the remote host also being the PostgreSQL server, PostgreSQL has to be installed there as well, obviously. For Debian/Ubuntu-based systems, install packages *postgresql* and *python-psycopg2*.
.. note:: Parameters that accept comma separated lists (*privs*, *objs*, *roles*) have singular alias names (*priv*, *obj*, *role*).
.. note:: To revoke only ``GRANT OPTION`` for a specific object, set *state* to ``present`` and *grant_option* to ``no`` (see examples).
.. note:: Note that when revoking privileges from a role R, this role  may still have access via privileges granted to any role R is a member of including ``PUBLIC``.
.. note:: Note that when revoking privileges from a role R, you do so as the user specified via *login*. If R has been granted the same privileges by another user also, R can still access database objects via these privileges.
.. note:: When revoking privileges, ``RESTRICT`` is assumed (see PostgreSQL docs).


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

