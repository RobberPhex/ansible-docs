.. _proxysql_mysql_users:


proxysql_mysql_users - Adds or removes mysql users from proxysql admin interface.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The :ref:`proxysql_mysql_users <proxysql_mysql_users>` module adds or removes mysql users using the proxysql admin interface.




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
                <tr><td>active<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A user with <em>active</em> set to <code>False</code> will be tracked in the database, but will be never loaded in the in-memory data structures. If omitted the proxysql database default for <em>active</em> is <code>True</code>.</div>        </td></tr>
                <tr><td>backend<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>If <em>backend</em> is set to <code>True</code>, this (username, password) pair is used for authenticating to the ProxySQL instance.</div>        </td></tr>
                <tr><td>config_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a config file from which login_user and login_password are to be read.</div>        </td></tr>
                <tr><td>default_hostgroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If there is no matching rule for the queries sent by this user, the traffic it generates is sent to the specified hostgroup. If omitted the proxysql database default for <em>use_ssl</em> is 0.</div>        </td></tr>
                <tr><td>default_schema<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The schema to which the connection should change to by default.</div>        </td></tr>
                <tr><td>fast_forward<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>fast_forward</em> is set to <code>True</code>, <em>fast_forward</em> will bypass the query processing layer (rewriting, caching) and pass through the query directly as is to the backend server. If omitted the proxysql database default for <em>fast_forward</em> is <code>False</code>.</div>        </td></tr>
                <tr><td>frontend<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>If <em>frontend</em> is set to <code>True</code>, this (username, password) pair is used for authenticating to the mysqld servers against any hostgroup.</div>        </td></tr>
                <tr><td>load_to_runtime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Dynamically load mysql host config to runtime memory.</div>        </td></tr>
                <tr><td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>127.0.0.1</td>
        <td></td>
        <td><div>The host used to connect to ProxySQL admin interface.</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The password used to authenticate to ProxySQL admin interface.</div>        </td></tr>
                <tr><td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>6032</td>
        <td></td>
        <td><div>The port used to connect to ProxySQL admin interface.</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The username used to authenticate to ProxySQL admin interface.</div>        </td></tr>
                <tr><td>max_connections<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The maximum number of connections ProxySQL will open to the backend for this user. If omitted the proxysql database default for <em>max_connections</em> is 10000.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of the user connecting to the mysqld or ProxySQL instance.</div>        </td></tr>
                <tr><td>save_to_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Save mysql host config to sqlite db on disk to persist the configuration.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>When <code>present</code> - adds the user, when <code>absent</code> - removes the user.</div>        </td></tr>
                <tr><td>transaction_persistent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If this is set for the user with which the MySQL client is connecting to ProxySQL (thus a "frontend" user), transactions started within a hostgroup will remain within that hostgroup regardless of any other rules. If omitted the proxysql database default for <em>transaction_persistent</em> is <code>False</code>.</div>        </td></tr>
                <tr><td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>use_ssl</em> is set to <code>True</code>, connections by this user will be made using SSL connections. If omitted the proxysql database default for <em>use_ssl</em> is <code>False</code>.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the user connecting to the mysqld or ProxySQL instance.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # This example adds a user, it saves the mysql user config to disk, but
    # avoids loading the mysql user config to runtime (this might be because
    # several users are being added and the user wants to push the config to
    # runtime in a single batch using the M(proxysql_manage_config) module).  It
    # uses supplied credentials to connect to the proxysql admin interface.
    
    - proxysql_mysql_users:
        login_user: 'admin'
        login_password: 'admin'
        username: 'productiondba'
        state: present
        load_to_runtime: False
    
    # This example removes a user, saves the mysql user config to disk, and
    # dynamically loads the mysql user config to runtime.  It uses credentials
    # in a supplied config file to connect to the proxysql admin interface.
    
    - proxysql_mysql_users:
        config_file: '~/proxysql.cnf'
        username: 'mysqlboy'
        state: absent

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
        <td> stdout </td>
        <td> The mysql user modified or removed from proxysql </td>
        <td align=center> On create/update will return the newly modified user, on delete it will return the deleted record. </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
