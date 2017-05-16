.. _logicmonitor_facts:


logicmonitor_facts - Collect facts about LogicMonitor objects
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

LogicMonitor is a hosted, full-stack, infrastructure monitoring platform.
This module collects facts about hosts abd host groups within your LogicMonitor account.


Requirements (on host that executes module)
-------------------------------------------

  * An existing LogicMonitor account
  * Linux


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
    <td>collector<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The fully qualified domain name of a collector in your LogicMonitor account.</div><div>This is optional for querying a LogicMonitor host when a displayname is specified.</div><div>This is required for querying a LogicMonitor host when a displayname is not specified.</div></td></tr>
            <tr>
    <td>company<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The LogicMonitor account company name. If you would log in to your account at "superheroes.logicmonitor.com" you would use "superheroes".</div></td></tr>
            <tr>
    <td>displayname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>hostname -f</td>
        <td><ul></ul></td>
        <td><div>The display name of a host in your LogicMonitor account or the desired display name of a device to add into monitoring.</div></td></tr>
            <tr>
    <td>fullpath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The fullpath of the hostgroup object you would like to manage.</div><div>Recommend running on a single ansible host.</div><div>Required for management of LogicMonitor host groups (target=hostgroup).</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>hostname -f</td>
        <td><ul></ul></td>
        <td><div>The hostname of a host in your LogicMonitor account, or the desired hostname of a device to add into monitoring.</div><div>Required for managing hosts (target=host).</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password for the chosen LogicMonitor User.</div><div>If an md5 hash is used, the digest flag must be set to true.</div></td></tr>
            <tr>
    <td>target<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>host</li><li>hostgroup</li></ul></td>
        <td><div>The LogicMonitor object you wish to manage.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A LogicMonitor user name. The module will authenticate and perform actions on behalf of this user.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    #example of querying a list of hosts
    ```
    ---
    - hosts: hosts
      user: root
      vars:
        company: 'yourcompany'
        user: 'Luigi'
        password: 'ImaLuigi,number1!'
      tasks:
      - name: query a list of hosts
        # All tasks should use local_action
        local_action:
          logicmonitor_facts:
            target: host
            company: '{{ company }}'
            user: '{{ user }}'
            password: '{{ password }}'
    ```
    
    #example of querying a hostgroup
    ```
    ---
    - hosts: somemachine.superheroes.com
      user: root
      vars:
        company: 'yourcompany'
        user: 'mario'
        password: 'itsame.Mario!'
      tasks:
      - name: query a host group
        # All tasks should use local_action
        local_action:
          logicmonitor_facts:
            target: hostgroup
            fullpath: '/servers/production'
            company: '{{ company }}'
            user: '{{ user }}'
            password: '{{ password }}'
    ```

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
        <td> ansible_facts </td>
        <td> LogicMonitor properties set for the specified object </td>
        <td align=center> success </td>
        <td align=center> list of dicts containing name/value pairs </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: You must have an existing LogicMonitor account for this module to function.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

