.. _zabbix_maintenance:


zabbix_maintenance - Create Zabbix maintenance windows
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.8


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module will let you create Zabbix maintenance windows.


Requirements
------------

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
    <td>collect_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>true</td>
        <td><ul></ul></td>
        <td><div>Type of maintenance. With data collection, or without.</div></td></tr>
            <tr>
    <td>desc<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>Created by Ansible</td>
        <td><ul></ul></td>
        <td><div>Short description of maintenance window.</div></td></tr>
            <tr>
    <td>host_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Host groups to manage maintenance window for. Separate multiple groups with commas. <code>host_group</code> is an alias for <code>host_groups</code>. <b>Required</b> option when <code>state</code> is <em>present</em> and no <code>host_names</code> specified.</div></br>
        <div style="font-size: small;">aliases: host_group<div></td></tr>
            <tr>
    <td>host_names<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Hosts to manage maintenance window for. Separate multiple hosts with commas. <code>host_name</code> is an alias for <code>host_names</code>. <b>Required</b> option when <code>state</code> is <em>present</em> and no <code>host_groups</code> specified.</div></br>
        <div style="font-size: small;">aliases: host_name<div></td></tr>
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
        <td><div>Zabbix user name.</div></td></tr>
            <tr>
    <td>minutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Length of maintenance window in minutes.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Unique name of maintenance window.</div></td></tr>
            <tr>
    <td>server_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url of Zabbix server, with protocol (http or https). <code>url</code> is an alias for <code>server_url</code>.</div></br>
        <div style="font-size: small;">aliases: url<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or remove a maintenance window.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create maintenance window named "Update of www1"
    # for host www1.example.com for 90 minutes
    - zabbix_maintenance: name="Update of www1"
                          host_name=www1.example.com
                          state=present
                          minutes=90
                          server_url=https://monitoring.example.com
                          login_user=ansible
                          login_password=pAsSwOrD
    
    # Create maintenance window named "Mass update"
    # for host www1.example.com and host groups Office and Dev
    - zabbix_maintenance: name="Update of www1"
                          host_name=www1.example.com
                          host_groups=Office,Dev
                          state=present
                          server_url=https://monitoring.example.com
                          login_user=ansible
                          login_password=pAsSwOrD
    
    # Create maintenance window named "update"
    # for hosts www1.example.com and db1.example.com and without data collection.
    - zabbix_maintenance: name=update
                          host_names=www1.example.com,db1.example.com
                          state=present
                          collect_data=false
                          server_url=https://monitoring.example.com
                          login_user=ansible
                          login_password=pAsSwOrD
    
    # Remove maintenance window named "Test1"
    - zabbix_maintenance: name=Test1
                          state=absent
                          server_url=https://monitoring.example.com
                          login_user=ansible
                          login_password=pAsSwOrD


Notes
-----

.. note:: Useful for setting hosts in maintenance mode before big update, and removing maintenance window after update.
.. note:: Module creates maintenance window from now() to now() + minutes, so if Zabbix server's time and host's time are not synchronized, you will get strange results.
.. note:: Install required module with 'pip install zabbix-api' command.
.. note:: Checks existance only by maintenance name.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

