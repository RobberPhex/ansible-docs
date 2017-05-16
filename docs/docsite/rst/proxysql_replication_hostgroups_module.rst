.. _proxysql_replication_hostgroups:


proxysql_replication_hostgroups - Manages replication hostgroups using the proxysql admin interface.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Each row in mysql_replication_hostgroups represent a pair of writer_hostgroup and reader_hostgroup. ProxySQL will monitor the value of read_only for all the servers in specified hostgroups, and based on the value of read_only will assign the server to the writer or reader hostgroups.




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
        <td><div>Text field that can be used for any purposed defined by the user.</div>        </td></tr>
                <tr><td>config_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a config file from which login_user and login_password are to be read.</div>        </td></tr>
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
                <tr><td>reader_hostgroup<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Id of the reader hostgroup.</div>        </td></tr>
                <tr><td>save_to_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Save mysql host config to sqlite db on disk to persist the configuration.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>When <code>present</code> - adds the replication hostgroup, when <code>absent</code> - removes the replication hostgroup.</div>        </td></tr>
                <tr><td>writer_hostgroup<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Id of the writer hostgroup.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # This example adds a replication hostgroup, it saves the mysql server config
    # to disk, but avoids loading the mysql server config to runtime (this might be
    # because several replication hostgroup are being added and the user wants to
    # push the config to runtime in a single batch using the
    # M(proxysql_manage_config) module).  It uses supplied credentials to connect
    # to the proxysql admin interface.
    
    - proxysql_replication_hostgroups:
        login_user: 'admin'
        login_password: 'admin'
        writer_hostgroup: 1
        reader_hostgroup: 2
        state: present
        load_to_runtime: False
    
    # This example removes a replication hostgroup, saves the mysql server config
    # to disk, and dynamically loads the mysql server config to runtime.  It uses
    # credentials in a supplied config file to connect to the proxysql admin
    # interface.
    
    - proxysql_replication_hostgroups:
        config_file: '~/proxysql.cnf'
        writer_hostgroup: 3
        reader_hostgroup: 4
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
        <td> The replication hostgroup modified or removed from proxysql </td>
        <td align=center> On create/update will return the newly modified group, on delete it will return the deleted record. </td>
        <td align=center> dict </td>
        <td align=center> {'msg': 'Added server to mysql_hosts', 'repl_group': {'comment': '', 'reader_hostgroup': '1', 'writer_hostgroup': '2'}, 'state': 'present', 'changed': True} </td>
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
