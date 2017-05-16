.. _postgresql_ext:


postgresql_ext - Add or remove PostgreSQL extensions from a database.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Add or remove PostgreSQL extensions from a database.

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
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the database to add or remove the extension to/from</td>
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
        <td>name of the extension to add or remove</td>
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
        <td>The database extension state</td>
    </tr>
        </table>


.. note:: Requires psycopg2


Examples
--------

.. raw:: html

    <br/>


::

    # Adds postgis to the database "acme"
    - postgresql_ext: name=postgis db=acme

.. note:: The default authentication assumes that you are either logging in as or sudo'ing to the ``postgres`` account on the host.
.. note:: This module uses *psycopg2*, a Python PostgreSQL database adapter. You must ensure that psycopg2 is installed on the host before using this module. If the remote host is the PostgreSQL server (which is the default case), then PostgreSQL must also be installed on the remote host. For Ubuntu-based systems, install the ``postgresql``, ``libpq-dev``, and ``python-psycopg2`` packages on the remote host before using this module.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

