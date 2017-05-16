.. _postgresql_lang:


postgresql_lang - Adds, removes or changes procedural languages with a PostgreSQL database.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds, removes or changes procedural languages with a PostgreSQL database.
This module allows you to add a language, remote a language or change the trust relationship with a PostgreSQL database. The module can be used on the machine where executed or on a remote host.
When removing a language from a database, it is possible that dependencies prevent the database from being removed. In that case, you can specify casade to automatically drop objects that depend on the language (such as functions in the language). In case the language can't be deleted because it is required by the database system, you can specify fail_on_drop=no to ignore the error.
Be carefull when marking a language as trusted since this could be a potential security breach. Untrusted languages allow only users with the PostgreSQL superuser privilege to use this language to create new functions.


Requirements
------------

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
    <td>cascade<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>when dropping a language, also delete object that depend on this language.</div><div>only used when <code>state=absent</code>.</div></td></tr>
            <tr>
    <td>db<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of database where the language will be added, removed or changed</div></td></tr>
            <tr>
    <td>fail_on_drop<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>yes</code>, fail when removing a language. Otherwise just log and continue</div><div>in some cases, it is not possible to remove a language (used by the db-system). When         dependencies block the removal, consider using <code>cascade</code>.</div></td></tr>
            <tr>
    <td>force_trust<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>marks the language as trusted, even if it's marked as untrusted in pg_pltemplate.</div><div>use with care!</div></td></tr>
            <tr>
    <td>lang<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the procedural language to add, remove or change</div></td></tr>
            <tr>
    <td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>Host running PostgreSQL where you want to execute the actions.</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password used to authenticate with PostgreSQL (must match <code>login_user</code>)</div></td></tr>
            <tr>
    <td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>postgres</td>
        <td><ul></ul></td>
        <td><div>User used to authenticate with PostgreSQL</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5432</td>
        <td><ul></ul></td>
        <td><div>Database port to connect to.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The state of the language for the selected database</div></td></tr>
            <tr>
    <td>trust<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>make this language trusted for the selected db</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add language pltclu to database testdb if it doesn't exist:
    - postgresql_lang db=testdb lang=pltclu state=present 
    
    # Add language pltclu to database testdb if it doesn't exist and mark it as trusted:
    # Marks the language as trusted if it exists but isn't trusted yet
    # force_trust makes sure that the language will be marked as trusted
    - postgresql_lang db=testdb lang=pltclu state=present trust=yes force_trust=yes
    
    # Remove language pltclu from database testdb:
    - postgresql_lang: db=testdb lang=pltclu state=absent
    
    # Remove language pltclu from database testdb and remove all dependencies:
    - postgresql_lang: db=testdb lang=pltclu state=absent cascade=yes
    
    # Remove language c from database testdb but ignore errors if something prevents the removal:
    - postgresql_lang: db=testdb lang=pltclu state=absent fail_on_drop=no


Notes
-----

.. note:: The default authentication assumes that you are either logging in as or sudo'ing to the postgres account on the host.
.. note:: This module uses psycopg2, a Python PostgreSQL database adapter. You must ensure that psycopg2 is installed on the host before using this module. If the remote host is the PostgreSQL server (which is the default case), then PostgreSQL must also be installed on the remote host. For Ubuntu-based systems, install the postgresql, libpq-dev, and python-psycopg2 packages on the remote host before using this module.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

