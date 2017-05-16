.. _zabbix_hostmacro:


zabbix_hostmacro - Zabbix host macro creates/updates/deletes
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

manages Zabbix host macros, it can create, update or delete them.


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
    <td>host_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the host.</div></td></tr>
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
    <td>macro_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the host macro.</div></td></tr>
            <tr>
    <td>macro_value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Value of the host macro.</div></td></tr>
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
        <td><div>State of the macro.</div><div>On <code>present</code>, it will create if macro does not exist or update the macro if the associated data is different.</div><div>On <code>absent</code> will remove a macro if it exists.</div></td></tr>
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

    - name: Create a new host macro or update an existing macro's value
      local_action:
        module: zabbix_hostmacro
        server_url: http://monitor.example.com
        login_user: username
        login_password: password
        host_name: ExampleHost
        macro_name:Example macro
        macro_value:Example value
        state: present




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

