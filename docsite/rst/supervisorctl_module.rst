.. _supervisorctl:


supervisorctl - Manage the state of a program or group of programs running via supervisord
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage the state of a program or group of programs running via supervisord


Requirements (on host that executes module)
-------------------------------------------

  * supervisorctl


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
    <td>config<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The supervisor configuration file path</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the supervisord program or group to manage.</div><div>The name will be taken as group name when it ends with a colon <em>:</em></div><div>Group support is only available in Ansible version 1.6 or later.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>password to use for authentication</div></td></tr>
            <tr>
    <td>server_url<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL on which supervisord server is listening</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>started</li><li>stopped</li><li>restarted</li><li>absent</li></ul></td>
        <td><div>The desired state of program/group.</div></td></tr>
            <tr>
    <td>supervisorctl_path<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to supervisorctl executable</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>username to use for authentication</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Manage the state of program to be in 'started' state.
    - supervisorctl: name=my_app state=started
    
    # Manage the state of program group to be in 'started' state.
    - supervisorctl: name='my_apps:' state=started
    
    # Restart my_app, reading supervisorctl configuration from a specified file.
    - supervisorctl: name=my_app state=restarted config=/var/opt/my_project/supervisord.conf
    
    # Restart my_app, connecting to supervisord with credentials and server URL.
    - supervisorctl: name=my_app state=restarted username=test password=testpass server_url=http://localhost:9001


Notes
-----

.. note:: When ``state`` = *present*, the module will call ``supervisorctl reread`` then ``supervisorctl add`` if the program/group does not exist.
.. note:: When ``state`` = *restarted*, the module will call ``supervisorctl update`` then call ``supervisorctl restart``.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

