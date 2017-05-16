.. _proxysql_manage_config:


proxysql_manage_config - Writes the proxysql configuration settings between layers.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The :ref:`proxysql_global_variables <proxysql_global_variables>` module writes the proxysql configuration settings between layers. Currently this module will always report a changed state, so should typically be used with WHEN however this will change in a future version when the CHECKSUM table commands are available for all tables in proxysql.




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
                <tr><td>action<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>LOAD</li><li>SAVE</li></ul></td>
        <td><div>The supplied <em>action</em> combines with the supplied <em>direction</em> to provide the semantics of how we want to move the <em>config_settings</em> between the <em>config_layers</em>.</div>        </td></tr>
                <tr><td>config_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a config file from which login_user and login_password are to be read.</div>        </td></tr>
                <tr><td>config_layer<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>MEMORY</li><li>DISK</li><li>RUNTIME</li><li>CONFIG</li></ul></td>
        <td><div>RUNTIME - represents the in-memory data structures of ProxySQL used by the threads that are handling the requests. MEMORY - (sometimes also referred as main) represents the in-memory SQLite3 database. DISK - represents the on-disk SQLite3 database. CONFIG - is the classical config file. You can only LOAD FROM the config file.</div>        </td></tr>
                <tr><td>config_settings<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>MYSQL USERS</li><li>MYSQL SERVERS</li><li>MYSQL QUERY RULES</li><li>MYSQL VARIABLES</li><li>ADMIN VARIABLES</li><li>SCHEDULER</li></ul></td>
        <td><div>The <em>config_settings</em> specifies which configuration we're writing.</div>        </td></tr>
                <tr><td>direction<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>FROM</li><li>TO</li></ul></td>
        <td><div>FROM - denotes we're reading values FROM the supplied <em>config_layer</em> and writing to the next layer. TO - denotes we're reading from the previous layer and writing TO the supplied <em>config_layer</em>."</div>        </td></tr>
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
        </table>
    </br>



Examples
--------

 ::

    ---
    # This example saves the mysql users config from memory to disk. It uses
    # supplied credentials to connect to the proxysql admin interface.
    
    - proxysql_global_variables:
        login_user: 'admin'
        login_password: 'admin'
        action: "SAVE"
        config_settings: "MYSQL USERS"
        direction: "FROM"
        config_layer: "MEMORY"
    
    # This example loads the mysql query rules config from memory to to runtime. It
    # uses supplied credentials to connect to the proxysql admin interface.
    
    - proxysql_global_variables:
        config_file: '~/proxysql.cnf'
        action: "LOAD"
        config_settings: "MYSQL QUERY RULES"
        direction: "TO"
        config_layer: "RUNTIME"

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
        <td> Simply reports whether the action reported a change. </td>
        <td align=center> Currently the returned value with always be changed=True. </td>
        <td align=center> dict </td>
        <td align=center> {'changed': True} </td>
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
