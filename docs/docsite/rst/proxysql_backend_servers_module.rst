.. _proxysql_backend_servers:


proxysql_backend_servers - Adds or removes mysql hosts from proxysql admin interface.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The :ref:`proxysql_backend_servers <proxysql_backend_servers>` module adds or removes mysql hosts using the proxysql admin interface.




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
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Text field that can be used for any purposed defined by the user. Could be a description of what the host stores, a reminder of when the host was added or disabled, or a JSON processed by some checker script.</div>        </td></tr>
                <tr><td>compression<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If the value of <em>compression</em> is greater than 0, new connections to that server will use compression. If omitted the proxysql database default for <em>compression</em> is 0.</div>        </td></tr>
                <tr><td>config_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a config file from which login_user and login_password are to be read.</div>        </td></tr>
                <tr><td>hostgroup_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The hostgroup in which this mysqld instance is included. An instance can be part of one or more hostgroups.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The ip address at which the mysqld instance can be contacted.</div>        </td></tr>
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
        <td><div>The maximum number of connections ProxySQL will open to this backend server. If omitted the proxysql database default for <em>max_connections</em> is 1000.</div>        </td></tr>
                <tr><td>max_latency_ms<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ping time is monitored regularly. If a host has a ping time greater than <em>max_latency_ms</em> it is excluded from the connection pool (although the server stays ONLINE). If omitted the proxysql database default for <em>max_latency_ms</em> is 0.</div>        </td></tr>
                <tr><td>max_replication_lag<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If greater than 0, ProxySQL will reguarly monitor replication lag. If replication lag goes above <em>max_replication_lag</em>, proxysql will temporarily shun the server until replication catches up. If omitted the proxysql database default for <em>max_replication_lag</em> is 0.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3306</td>
        <td></td>
        <td><div>The port at which the mysqld instance can be contacted.</div>        </td></tr>
                <tr><td>save_to_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Save mysql host config to sqlite db on disk to persist the configuration.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>When <code>present</code> - adds the host, when <code>absent</code> - removes the host.</div>        </td></tr>
                <tr><td>status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>ONLINE</li><li>OFFLINE_SOFT</li><li>OFFLINE_HARD</li></ul></td>
        <td><div>ONLINE - Backend server is fully operational. OFFLINE_SOFT - When a server is put into <code>OFFLINE_SOFT</code> mode, connections are kept in use until the current transaction is completed. This allows to gracefully detach a backend. OFFLINE_HARD - When a server is put into <code>OFFLINE_HARD</code> mode, the existing connections are dropped, while new incoming connections aren't accepted either.
    If omitted the proxysql database default for <em>status</em> is <code>ONLINE</code>.</div>        </td></tr>
                <tr><td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>use_ssl</em> is set to <code>True</code>, connections to this server will be made using SSL connections. If omitted the proxysql database default for <em>use_ssl</em> is <code>False</code>.</div>        </td></tr>
                <tr><td>weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The bigger the weight of a server relative to other weights, the higher the probability of the server being chosen from the hostgroup. If omitted the proxysql database default for <em>weight</em> is 1.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # This example adds a server, it saves the mysql server config to disk, but
    # avoids loading the mysql server config to runtime (this might be because
    # several servers are being added and the user wants to push the config to
    # runtime in a single batch using the M(proxysql_manage_config) module).  It
    # uses supplied credentials to connect to the proxysql admin interface.
    
    - proxysql_backend_servers:
        login_user: 'admin'
        login_password: 'admin'
        hostname: 'mysql01'
        state: present
        load_to_runtime: False
    
    # This example removes a server, saves the mysql server config to disk, and
    # dynamically loads the mysql server config to runtime.  It uses credentials
    # in a supplied config file to connect to the proxysql admin interface.
    
    - proxysql_backend_servers:
        config_file: '~/proxysql.cnf'
        hostname: 'mysql02'
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
        <td> The mysql host modified or removed from proxysql </td>
        <td align=center> On create/update will return the newly modified host, on delete it will return the deleted record. </td>
        <td align=center> dict </td>
        <td align=center> {'msg': 'Added server to mysql_hosts', 'state': 'present', 'changed': True, 'hostname': '192.168.52.1', 'server': {'comment': '', 'status': 'ONLINE', 'compression': '0', 'weight': '1', 'hostname': '192.168.52.1', 'hostgroup_id': '1', 'use_ssl': '0', 'max_connections': '1000', 'port': '3306', 'max_latency_ms': '0', 'max_replication_lag': '0'}} </td>
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
