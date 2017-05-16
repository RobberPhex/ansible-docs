.. _proxysql_scheduler:


proxysql_scheduler - Adds or removes schedules from proxysql admin interface.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The :ref:`proxysql_scheduler <proxysql_scheduler>` module adds or removes schedules using the proxysql admin interface.




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
    <td>True</td>
        <td></td>
        <td><div>A schedule with <em>active</em> set to <code>False</code> will be tracked in the database, but will be never loaded in the in-memory data structures.</div>        </td></tr>
                <tr><td>arg1<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Argument that can be passed to the job.</div>        </td></tr>
                <tr><td>arg2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Argument that can be passed to the job.</div>        </td></tr>
                <tr><td>arg3<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Argument that can be passed to the job.</div>        </td></tr>
                <tr><td>arg4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Argument that can be passed to the job.</div>        </td></tr>
                <tr><td>arg5<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Argument that can be passed to the job.</div>        </td></tr>
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
                <tr><td>filename<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Full path of the executable to be executed.</div>        </td></tr>
                <tr><td>force_delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>By default we avoid deleting more than one schedule in a single batch, however if you need this behaviour and you're not concerned about the schedules deleted, you can set <em>force_delete</em> to <code>True</code>.</div>        </td></tr>
                <tr><td>interval_ms<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10000</td>
        <td></td>
        <td><div>How often (in millisecond) the job will be started. The minimum value for <em>interval_ms</em> is 100 milliseconds.</div>        </td></tr>
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
                <tr><td>save_to_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Save mysql host config to sqlite db on disk to persist the configuration.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>When <code>present</code> - adds the schedule, when <code>absent</code> - removes the schedule.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # This example adds a schedule, it saves the scheduler config to disk, but
    # avoids loading the scheduler config to runtime (this might be because
    # several servers are being added and the user wants to push the config to
    # runtime in a single batch using the M(proxysql_manage_config) module).  It
    # uses supplied credentials to connect to the proxysql admin interface.
    
    - proxysql_scheduler:
        login_user: 'admin'
        login_password: 'admin'
        interval_ms: 1000
        filename: "/opt/maintenance.py"
        state: present
        load_to_runtime: False
    
    # This example removes a schedule, saves the scheduler config to disk, and
    # dynamically loads the scheduler config to runtime.  It uses credentials
    # in a supplied config file to connect to the proxysql admin interface.
    
    - proxysql_scheduler:
        config_file: '~/proxysql.cnf'
        filename: "/opt/old_script.py"
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
        <td> The schedule modified or removed from proxysql </td>
        <td align=center> On create/update will return the newly modified schedule, on delete it will return the deleted record. </td>
        <td align=center> dict </td>
        <td align=center> {'msg': 'Added schedule to scheduler', 'state': 'present', 'changed': True, 'filename': '/opt/test.py', 'schedules': [{'comment': '', 'arg1': None, 'arg2': None, 'arg3': None, 'arg4': None, 'arg5': None, 'filename': '/opt/test.py', 'interval_ms': '10000', 'active': '1', 'id': '1'}]} </td>
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
