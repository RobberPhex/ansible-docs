.. _postgresql_db:


postgresql_db - Add or remove PostgreSQL databases from a remote host.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Add or remove PostgreSQL databases from a remote host.

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
    <td>encoding</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Encoding of the database</td>
    </tr>
            <tr>
    <td>lc_collate</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Collation order (LC_COLLATE) to use in the database. Must match collation order of template database unless <code>template0</code> is used as template.</td>
    </tr>
            <tr>
    <td>lc_ctype</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Character classification (LC_CTYPE) to use in the database (e.g. lower, upper, ...) Must match LC_CTYPE of template database unless <code>template0</code> is used as template.</td>
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
    <td>owner</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the role to set as owner of the database</td>
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
        <td>The database state</td>
    </tr>
            <tr>
    <td>template</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Template used to create the database</td>
    </tr>
        </table>


.. note:: Requires psycopg2


Examples
--------

.. raw:: html

    <br/>


::

    # Create a new database with name "acme"
    - postgresql_db: name=acme
    
    # Create a new database with name "acme" and specific encoding and locale
    # settings. If a template different from "template0" is specified, encoding
    # and locale settings must match those of the template.
    - postgresql_db: name=acme
                     encoding='UTF-8'
                     lc_collate='de_DE.UTF-8'
                     lc_ctype='de_DE.UTF-8'
                     template='template0'

.. note:: The default authentication assumes that you are either logging in as or sudo'ing to the ``postgres`` account on the host.
.. note:: This module uses *psycopg2*, a Python PostgreSQL database adapter. You must ensure that psycopg2 is installed on the host before using this module. If the remote host is the PostgreSQL server (which is the default case), then PostgreSQL must also be installed on the remote host. For Ubuntu-based systems, install the ``postgresql``, ``libpq-dev``, and ``python-psycopg2`` packages on the remote host before using this module.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

