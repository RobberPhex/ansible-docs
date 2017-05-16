.. _zabbix_host:


zabbix_host - Zabbix host creates/updates/deletes
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows you to create, modify and delete Zabbix host entries and associated group and template data.


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
            <tr>
    <td>force<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Overwrite the host configuration, even if already present</div></td></tr>
            <tr>
    <td>host_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of host groups the host is part of.</div></td></tr>
            <tr>
    <td>host_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the host in Zabbix.</div><div>host_name is the unique identifier used and cannot be updated using this module.</div></td></tr>
            <tr>
    <td>http_login_password<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Basic Auth password</div></td></tr>
            <tr>
    <td>http_login_user<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Basic Auth login</div></td></tr>
            <tr>
    <td>interfaces<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of interfaces to be created for the host (see example below).</div><div>Available values are: dns, ip, main, port, type and useip.</div><div>Please review the interface documentation for more information on the supported properties</div><div>https://www.zabbix.com/documentation/2.0/manual/appendix/api/hostinterface/definitions#host_interface</div></td></tr>
            <tr>
    <td>inventory_mode<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>automatic</li><li>manual</li><li>disabled</li></ul></td>
        <td><div>Configure the inventory mode.</div></td></tr>
            <tr>
    <td>link_templates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>List of templates linked to the host.</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Zabbix user password.</div></td></tr>
            <tr>
    <td>login_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Zabbix user name, used to authenticate against the server.</div></td></tr>
            <tr>
    <td>proxy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the Zabbix Proxy to be used</div></td></tr>
            <tr>
    <td>server_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url of Zabbix server, with protocol (http or https).</div></br>
        <div style="font-size: small;">aliases: url<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the host.</div><div>On <code>present</code>, it will create if host does not exist or update the host if the associated data is different.</div><div>On <code>absent</code> will remove a host if it exists.</div></td></tr>
            <tr>
    <td>status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>enabled</td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>Monitoring status of the host.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>The timeout of API request (seconds).</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a new host or update an existing host's info
      local_action:
        module: zabbix_host
        server_url: http://monitor.example.com
        login_user: username
        login_password: password
        host_name: ExampleHost
        host_groups:
          - Example group1
          - Example group2
        link_templates:
          - Example template1
          - Example template2
        status: enabled
        state: present
        inventory_mode: automatic
        interfaces:
          - type: 1
            main: 1
            useip: 1
            ip: 10.xx.xx.xx
            dns: ""
            port: 10050
          - type: 4
            main: 1
            useip: 1
            ip: 10.xx.xx.xx
            dns: ""
            port: 12345
        proxy: a.zabbix.proxy




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

