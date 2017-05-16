.. _postgresql_lang:


postgresql_lang - Adds, removes or changes procedural languages with a PostgreSQL database.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.7

Adds, removes or changes procedural languages with a PostgreSQL database.
This module allows you to add a language, remote a language or change the trust relationship with a PostgreSQL database. The module can be used on the machine where executed or on a remote host.
When removing a language from a database, it is possible that dependencies prevent the database from being removed. In that case, you can specify casade to automatically drop objects that depend on the language (such as functions in the language). In case the language can't be deleted because it is required by the database system, you can specify fail_on_drop=no to ignore the error.
Be carefull when marking a language as trusted since this could be a potential security breach. Untrusted languages allow only users with the PostgreSQL superuser privilege to use this language to create new functions.

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
    <td>cascade</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>when dropping a language, also delete object that depend on this language.only used when <code>state=absent</code>.</td>
    </tr>
            <tr>
    <td>db</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of database where the language will be added, removed or changed</td>
    </tr>
            <tr>
    <td>fail_on_drop</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if <code>yes</code>, fail when removing a language. Otherwise just log and continuein some cases, it is not possible to remove a language (used by the db-system). When         dependencies block the removal, consider using <code>cascade</code>.</td>
    </tr>
            <tr>
    <td>force_trust</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>marks the language as trusted, even if it's marked as untrusted in pg_pltemplate.use with care!</td>
    </tr>
            <tr>
    <td>lang</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the procedural language to add, remove or change</td>
    </tr>
            <tr>
    <td>login_host</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>Host running PostgreSQL where you want to execute the actions.</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Password used to authenticate with PostgreSQL (must match <code>login_user</code>)</td>
    </tr>
            <tr>
    <td>login_user</td>
    <td>no</td>
    <td>postgres</td>
        <td><ul></ul></td>
        <td>User used to authenticate with PostgreSQL</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>5432</td>
        <td><ul></ul></td>
        <td>Database port to connect to.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>The state of the language for the selected database</td>
    </tr>
            <tr>
    <td>trust</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>make this language trusted for the selected db</td>
    </tr>
        </table>


.. note:: Requires psycopg2


Examples
--------

.. raw:: html

    <br/>


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

.. note:: The default authentication assumes that you are either logging in as or sudo'ing to the postgres account on the host.
.. note:: This module uses psycopg2, a Python PostgreSQL database adapter. You must ensure that psycopg2 is installed on the host before using this module. If the remote host is the PostgreSQL server (which is the default case), then PostgreSQL must also be installed on the remote host. For Ubuntu-based systems, install the postgresql, libpq-dev, and python-psycopg2 packages on the remote host before using this module.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

