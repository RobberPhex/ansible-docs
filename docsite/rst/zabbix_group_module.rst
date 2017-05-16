.. _zabbix_group:


zabbix_group - Zabbix host groups creates/deletes
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.8


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create host groups if they do not exist.
Delete existing host groups if they exist.


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
    <td>host_groups<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of host groups to create or delete.</div></br>
        <div style="font-size: small;">aliases: host_group<div></td></tr>
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
        <td><div>Create or delete host group.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>The timeout of API request(seconds).</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Base create host groups example
    - name: Create host groups
      local_action:
        module: zabbix_group
        server_url: http://monitor.example.com
        login_user: username
        login_password: password
        state: present
        host_groups:
          - Example group1
          - Example group2
    
    # Limit the Zabbix group creations to one host since Zabbix can return an error when doing concurent updates
    - name: Create host groups
      local_action:
        module: zabbix_group
        server_url: http://monitor.example.com
        login_user: username
        login_password: password
        state: present
        host_groups:
          - Example group1
          - Example group2
      when: inventory_hostname==groups['group_name'][0]


Notes
-----

.. note:: Too many concurrent updates to the same group may cause Zabbix to return errors, see examples for a workaround if needed.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

