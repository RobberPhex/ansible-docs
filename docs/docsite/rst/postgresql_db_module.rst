.. _postgresql_db:


postgresql_db - Add or remove PostgreSQL databases from a remote host.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove PostgreSQL databases from a remote host.


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
                <tr><td>encoding<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Encoding of the database</div>        </td></tr>
                <tr><td>lc_collate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Collation order (LC_COLLATE) to use in the database. Must match collation order of template database unless <code>template0</code> is used as template.</div>        </td></tr>
                <tr><td>lc_ctype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Character classification (LC_CTYPE) to use in the database (e.g. lower, upper, ...) Must match LC_CTYPE of template database unless <code>template0</code> is used as template.</div>        </td></tr>
                <tr><td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host running the database</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password used to authenticate with</div>        </td></tr>
                <tr><td>login_unix_socket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to a Unix domain socket for local connections</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>postgres</td>
        <td></td>
        <td><div>The username used to authenticate with</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the database to add or remove</div>        </td></tr>
                <tr><td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the role to set as owner of the database</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5432</td>
        <td></td>
        <td><div>Database port to connect to.</div>        </td></tr>
                <tr><td>ssl_mode<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>prefer</td>
        <td><ul><li>disable</li><li>allow</li><li>prefer</li><li>require</li><li>verify-ca</li><li>verify-full</li></ul></td>
        <td><div>Determines whether or with what priority a secure SSL TCP/IP connection will be negotiated with the server.</div><div>See https://www.postgresql.org/docs/current/static/libpq-ssl.html for more information on the modes.</div><div>Default of <code>prefer</code> matches libpq default.</div>        </td></tr>
                <tr><td>ssl_rootcert<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the name of a file containing SSL certificate authority (CA) certificate(s).</div><div>If the file exists, the server's certificate will be verified to be signed by one of these authorities.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The database state</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Template used to create the database</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new database with name "acme"
    - postgresql_db:
        name: acme
    
    # Create a new database with name "acme" and specific encoding and locale
    # settings. If a template different from "template0" is specified, encoding
    # and locale settings must match those of the template.
    - postgresql_db:
        name: acme
        encoding: UTF-8
        lc_collate: de_DE.UTF-8
        lc_ctype: de_DE.UTF-8
        template: template0


Notes
-----

.. note::
    - The default authentication assumes that you are either logging in as or sudo'ing to the ``postgres`` account on the host.
    - This module uses *psycopg2*, a Python PostgreSQL database adapter. You must ensure that psycopg2 is installed on the host before using this module. If the remote host is the PostgreSQL server (which is the default case), then PostgreSQL must also be installed on the remote host. For Ubuntu-based systems, install the ``postgresql``, ``libpq-dev``, and ``python-psycopg2`` packages on the remote host before using this module.
    - The ssl_rootcert parameter requires at least Postgres version 8.4 and *psycopg2* version 2.4.3.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
