.. _zabbix_screen:


zabbix_screen - Zabbix screen creates/updates/deletes
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows you to create, modify and delete Zabbix screens and associated graph data.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * zabbix-api


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
                <tr><td>http_login_password<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Basic Auth password</div>        </td></tr>
                <tr><td>http_login_user<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Basic Auth login</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Zabbix user password.</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Zabbix user name.</div>        </td></tr>
                <tr><td>screens<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>List of screens to be created/updated/deleted(see example).</div><div>If the screen(s) already been added, the screen(s) name won't be updated.</div><div>When creating or updating screen(s), <code>screen_name</code>, <code>host_group</code> are required.</div><div>When deleting screen(s), the <code>screen_name</code> is required.</div><div>The available states are: <code>present</code> (default) and <code>absent</code>. If the screen(s) already exists, and the state is not <code>absent</code>, the screen(s) will just be updated as needed.</div>        </td></tr>
                <tr><td>server_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Url of Zabbix server, with protocol (http or https).</div></br>
    <div style="font-size: small;">aliases: url<div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>The timeout of API request (seconds).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create/update a screen.
    - name: Create a new screen or update an existing screen's items
      local_action:
        module: zabbix_screen
        server_url: http://monitor.example.com
        login_user: username
        login_password: password
        screens:
          - screen_name: ExampleScreen1
            host_group: Example group1
            state: present
            graph_names:
              - Example graph1
              - Example graph2
            graph_width: 200
            graph_height: 100
    
    # Create/update multi-screen
    - name: Create two of new screens or update the existing screens' items
      local_action:
        module: zabbix_screen
        server_url: http://monitor.example.com
        login_user: username
        login_password: password
        screens:
          - screen_name: ExampleScreen1
            host_group: Example group1
            state: present
            graph_names:
              - Example graph1
              - Example graph2
            graph_width: 200
            graph_height: 100
          - screen_name: ExampleScreen2
            host_group: Example group2
            state: present
            graph_names:
              - Example graph1
              - Example graph2
            graph_width: 200
            graph_height: 100
    
    # Limit the Zabbix screen creations to one host since Zabbix can return an error when doing concurent updates
    - name: Create a new screen or update an existing screen's items
      local_action:
        module: zabbix_screen
        server_url: http://monitor.example.com
        login_user: username
        login_password: password
        state: present
        screens:
          - screen_name: ExampleScreen
            host_group: Example group
            state: present
            graph_names:
              - Example graph1
              - Example graph2
            graph_width: 200
            graph_height: 100
      when: inventory_hostname==groups['group_name'][0]


Notes
-----

.. note::
    - Too many concurrent updates to the same screen may cause Zabbix to return errors, see examples for a workaround if needed.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
