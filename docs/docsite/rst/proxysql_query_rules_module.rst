.. _proxysql_query_rules:


proxysql_query_rules - Modifies query rules using the proxysql admin interface.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The :ref:`proxysql_query_rules <proxysql_query_rules>` module modifies query rules using the proxysql admin interface.




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
        <td><div>A rule with <em>active</em> set to <code>False</code> will be tracked in the database, but will be never loaded in the in-memory data structures.</div>        </td></tr>
                <tr><td>apply<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used in combination with <em>flagIN</em> and <em>flagOUT</em> to create chains of rules. Setting apply to True signifies the last rule to be applied.</div>        </td></tr>
                <tr><td>cache_ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of milliseconds for which to cache the result of the query. Note in ProxySQL 1.1 <em>cache_ttl</em> was in seconds.</div>        </td></tr>
                <tr><td>client_addr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Match traffic from a specific source.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Free form text field, usable for a descriptive comment of the query rule.</div>        </td></tr>
                <tr><td>config_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a config file from which login_user and login_password are to be read.</div>        </td></tr>
                <tr><td>delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of milliseconds to delay the execution of the query. This is essentially a throttling mechanism and QoS, and allows a way to give priority to queries over others. This value is added to the mysql-default_query_delay global variable that applies to all queries.</div>        </td></tr>
                <tr><td>destination_hostgroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Route matched queries to this hostgroup. This happens unless there is a started transaction and the logged in user has <em>transaction_persistent</em> set to <code>True</code> (see <span class='module'>proxysql_mysql_users</span>).</div>        </td></tr>
                <tr><td>digest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Match queries with a specific digest, as returned by stats_mysql_query_digest.digest.</div>        </td></tr>
                <tr><td>error_msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Query will be blocked, and the specified error_msg will be returned to the client.</div>        </td></tr>
                <tr><td>flagIN<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used in combination with <em>flagOUT</em> and <em>apply</em> to create chains of rules.</div>        </td></tr>
                <tr><td>flagOUT<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used in combination with <em>flagIN</em> and apply to create chains of rules. When set, <em>flagOUT</em> signifies the <em>flagIN</em> to be used in the next chain of rules.</div>        </td></tr>
                <tr><td>force_delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>By default we avoid deleting more than one schedule in a single batch, however if you need this behaviour and you're not concerned about the schedules deleted, you can set <em>force_delete</em> to <code>True</code>.</div>        </td></tr>
                <tr><td>load_to_runtime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Dynamically load mysql host config to runtime memory.</div>        </td></tr>
                <tr><td>log<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Query will be logged.</div>        </td></tr>
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
                <tr><td>match_digest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Regular expression that matches the query digest. The dialect of regular expressions used is that of re2 - https://github.com/google/re2</div>        </td></tr>
                <tr><td>match_pattern<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Regular expression that matches the query text. The dialect of regular expressions used is that of re2 - https://github.com/google/re2</div>        </td></tr>
                <tr><td>mirror_flagOUT<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enables query mirroring. If set <em>mirror_flagOUT</em> can be used to evaluates the mirrored query against the specified chain of rules.</div>        </td></tr>
                <tr><td>mirror_hostgroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enables query mirroring. If set <em>mirror_hostgroup</em> can be used to mirror queries to the same or different hostgroup.</div>        </td></tr>
                <tr><td>negate_match_pattern<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>negate_match_pattern</em> is set to <code>True</code>, only queries not matching the query text will be considered as a match. This acts as a NOT operator in front of the regular expression matching against match_pattern.</div>        </td></tr>
                <tr><td>proxy_addr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Match incoming traffic on a specific local IP.</div>        </td></tr>
                <tr><td>proxy_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Match incoming traffic on a specific local port.</div>        </td></tr>
                <tr><td>replace_pattern<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This is the pattern with which to replace the matched pattern. Note that this is optional, and when omitted, the query processor will only cache, route, or set other parameters without rewriting.</div>        </td></tr>
                <tr><td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The maximum number of times a query needs to be re-executed in case of detected failure during the execution of the query. If retries is not specified, the global variable mysql-query_retries_on_failure applies.</div>        </td></tr>
                <tr><td>rule_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The unique id of the rule. Rules are processed in rule_id order.</div>        </td></tr>
                <tr><td>save_to_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Save mysql host config to sqlite db on disk to persist the configuration.</div>        </td></tr>
                <tr><td>schemaname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Filtering criteria matching schemaname. If <em>schemaname</em> is non-NULL, a query will match only if the connection uses schemaname as its default schema.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>When <code>present</code> - adds the rule, when <code>absent</code> - removes the rule.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The maximum timeout in milliseconds with which the matched or rewritten query should be executed. If a query run for longer than the specific threshold, the query is automatically killed. If timeout is not specified, the global variable mysql-default_query_timeout applies.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Filtering criteria matching username.  If <em>username</em> is non-NULL, a query will match only if the connection is made with the correct username.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # This example adds a rule to redirect queries from a specific user to another
    # hostgroup, it saves the mysql query rule config to disk, but avoids loading
    # the mysql query config config to runtime (this might be because several
    # rules are being added and the user wants to push the config to runtime in a
    # single batch using the M(proxysql_manage_config) module). It uses supplied
    # credentials to connect to the proxysql admin interface.
    
    - proxysql_backend_servers:
        login_user: admin
        login_password: admin
        username: 'guest_ro'
        destination_hostgroup: 1
        active: 1
        retries: 3
        state: present
        load_to_runtime: False
    
    # This example removes all rules that use the username 'guest_ro', saves the
    # mysql query rule config to disk, and dynamically loads the mysql query rule
    # config to runtime.  It uses credentials in a supplied config file to connect
    # to the proxysql admin interface.
    
    - proxysql_backend_servers:
        config_file: '~/proxysql.cnf'
        username: 'guest_ro'
        state: absent
        force_delete: true

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
        <td align=center> On create/update will return the newly modified rule, in all other cases will return a list of rules that match the supplied criteria. </td>
        <td align=center> dict </td>
        <td align=center> {'msg': 'Added rule to mysql_query_rules', 'rules': [{'comment': None, 'username': 'guest_ro', 'flagOUT': None, 'match_pattern': None, 'destination_hostgroup': 1, 'proxy_port': None, 'active': '0', 'reconnect': None, 'mirror_flagOUT': None, 'apply': '0', 'schemaname': None, 'replace_pattern': None, 'cache_ttl': None, 'digest': None, 'retries': None, 'match_digest': None, 'mirror_hostgroup': None, 'log': None, 'negate_match_pattern': '0', 'flagIN': '0', 'client_addr': None, 'error_msg': None, 'delay': None, 'proxy_addr': None, 'timeout': None, 'rule_id': '1'}], 'state': 'present', 'changed': True} </td>
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
