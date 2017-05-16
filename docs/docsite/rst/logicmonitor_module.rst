.. _logicmonitor:


logicmonitor - Manage your LogicMonitor account through Ansible Playbooks
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* LogicMonitor is a hosted, full-stack, infrastructure monitoring platform.
* This module manages hosts, host groups, and collectors within your LogicMonitor account.


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
                <tr><td>action<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>add</li><li>remove</li><li>update</li><li>sdt</li></ul></td>
        <td><div>The action you wish to perform on target.</div><div>Add: Add an object to your LogicMonitor account.</div><div>Remove: Remove an object from your LogicMonitor account.</div><div>Update: Update properties, description, or groups (target=host) for an object in your LogicMonitor account.</div><div>SDT: Schedule downtime for an object in your LogicMonitor account.</div>        </td></tr>
                <tr><td>alertenable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>A boolean flag to turn alerting on or off for an object.</div><div>Optional for managing all hosts (action=add or action=update).</div>        </td></tr>
                <tr><td>collector<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The fully qualified domain name of a collector in your LogicMonitor account.</div><div>This is required for the creation of a LogicMonitor host (target=host action=add).</div><div>This is required for updating, removing or scheduling downtime for hosts if 'displayname' isn't specified (target=host action=update action=remove action=sdt).</div>        </td></tr>
                <tr><td>company<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The LogicMonitor account company name. If you would log in to your account at "superheroes.logicmonitor.com" you would use "superheroes."</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The long text description of the object in your LogicMonitor account.</div><div>Optional for managing hosts and host groups (target=host or target=hostgroup; action=add or action=update).</div>        </td></tr>
                <tr><td>displayname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>hostname -f</td>
        <td></td>
        <td><div>The display name of a host in your LogicMonitor account or the desired display name of a device to manage.</div><div>Optional for managing hosts (target=host).</div>        </td></tr>
                <tr><td>duration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>The duration (minutes) of the Scheduled Down Time (SDT).</div><div>Optional for putting an object into SDT (action=sdt).</div>        </td></tr>
                <tr><td>fullpath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The fullpath of the host group object you would like to manage.</div><div>Recommend running on a single Ansible host.</div><div>Required for management of LogicMonitor host groups (target=hostgroup).</div>        </td></tr>
                <tr><td>groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of groups that the host should be a member of.</div><div>Optional for managing hosts (target=host; action=add or action=update).</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>hostname -f</td>
        <td></td>
        <td><div>The hostname of a host in your LogicMonitor account, or the desired hostname of a device to manage.</div><div>Optional for managing hosts (target=host).</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>ID of the datasource to target.</div><div>Required for management of LogicMonitor datasources (target=datasource).</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password of the specified LogicMonitor user</div>        </td></tr>
                <tr><td>properties<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A dictionary of properties to set on the LogicMonitor host or host group.</div><div>Optional for managing hosts and host groups (target=host or target=hostgroup; action=add or action=update).</div><div>This parameter will add or update existing properties in your LogicMonitor account.</div>        </td></tr>
                <tr><td>starttime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Now</td>
        <td></td>
        <td><div>The time that the Scheduled Down Time (SDT) should begin.</div><div>Optional for managing SDT (action=sdt).</div><div>Y-m-d H:M</div>        </td></tr>
                <tr><td>target<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>collector</li><li>host</li><li>datsource</li><li>hostgroup</li></ul></td>
        <td><div>The type of LogicMonitor object you wish to manage.</div><div>Collector: Perform actions on a LogicMonitor collector.</div><div>NOTE You should use Ansible service modules such as <span class='module'>service</span> or <span class='module'>supervisorctl</span> for managing the Collector 'logicmonitor-agent' and 'logicmonitor-watchdog' services. Specifically, you'll probably want to start these services after a Collector add and stop these services before a Collector remove.</div><div>Host: Perform actions on a host device.</div><div>Hostgroup: Perform actions on a LogicMonitor host group.</div><div>NOTE Host and Hostgroup tasks should always be performed via delegate_to: localhost. There are no benefits to running these tasks on the remote host and doing so will typically cause problems.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A LogicMonitor user name. The module will authenticate and perform actions on behalf of this user.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # example of adding a new LogicMonitor collector to these devices
    ---
    - hosts: collectors
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Deploy/verify LogicMonitor collectors
        become: yes
        logicmonitor:
          target: collector
          action: add
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
    
    #example of adding a list of hosts into monitoring
    ---
    - hosts: hosts
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Deploy LogicMonitor Host
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: host
          action: add
          collector: mycompany-Collector
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          groups: /servers/production,/datacenter1
          properties:
            snmp.community: secret
            dc: 1
            type: prod
        delegate_to: localhost
    
    #example of putting a datasource in SDT
    ---
    - hosts: localhost
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: SDT a datasource
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: datasource
          action: sdt
          id: 123
          duration: 3000
          starttime: '2017-03-04 05:06'
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
    
    #example of creating a hostgroup
    ---
    - hosts: localhost
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Create a host group
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: hostgroup
          action: add
          fullpath: /servers/development
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          properties:
            snmp.community: commstring
            type: dev
    
    #example of putting a list of hosts into SDT
    ---
    - hosts: hosts
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: SDT hosts
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: host
          action: sdt
          duration: 3000
          starttime: '2016-11-10 09:08'
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          collector: mycompany-Collector
        delegate_to: localhost
    
    #example of putting a host group in SDT
    ---
    - hosts: localhost
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: SDT a host group
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: hostgroup
          action: sdt
          fullpath: /servers/development
          duration: 3000
          starttime: '2017-03-04 05:06'
          company=: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
    
    #example of updating a list of hosts
    ---
    - hosts: hosts
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Update a list of hosts
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: host
          action: update
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          collector: mycompany-Collector
          groups: /servers/production,/datacenter5
          properties:
            snmp.community: commstring
            dc: 5
        delegate_to: localhost
    
    #example of updating a hostgroup
    ---
    - hosts: hosts
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Update a host group
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: hostgroup
          action: update
          fullpath: /servers/development
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          properties:
            snmp.community: hg
            type: dev
            status: test
        delegate_to: localhost
    
    #example of removing a list of hosts from monitoring
    ---
    - hosts: hosts
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Remove LogicMonitor hosts
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: host
          action: remove
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          collector: mycompany-Collector
        delegate_to: localhost
    
    #example of removing a host group
    ---
    - hosts: hosts
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Remove LogicMonitor development servers hostgroup
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: hostgroup
          action: remove
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          fullpath: /servers/development
        delegate_to: localhost
      - name: Remove LogicMonitor servers hostgroup
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: hostgroup
          action: remove
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          fullpath: /servers
        delegate_to: localhost
      - name: Remove LogicMonitor datacenter1 hostgroup
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: hostgroup
          action: remove
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          fullpath: /datacenter1
        delegate_to: localhost
      - name: Remove LogicMonitor datacenter5 hostgroup
        # All tasks except for target=collector should use delegate_to: localhost
        logicmonitor:
          target: hostgroup
          action: remove
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          fullpath: /datacenter5
        delegate_to: localhost
    
    ### example of removing a new LogicMonitor collector to these devices
    ---
    - hosts: collectors
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Remove LogicMonitor collectors
        become: yes
        logicmonitor:
          target: collector
          action: remove
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
    
    #complete example
    ---
    - hosts: localhost
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Create a host group
        logicmonitor:
          target: hostgroup
          action: add
          fullpath: /servers/production/database
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          properties:
            snmp.community: commstring
      - name: SDT a host group
        logicmonitor:
          target: hostgroup
          action: sdt
          fullpath: /servers/production/web
          duration: 3000
          starttime: '2012-03-04 05:06'
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
    
    - hosts: collectors
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: Deploy/verify LogicMonitor collectors
        logicmonitor:
          target: collector
          action: add
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
      - name: Place LogicMonitor collectors into 30 minute Scheduled downtime
        logicmonitor:
          target: collector
          action: sdt
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
      - name: Deploy LogicMonitor Host
        logicmonitor:
          target: host
          action: add
          collector: agent1.ethandev.com
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          properties:
            snmp.community: commstring
            dc: 1
          groups: /servers/production/collectors, /datacenter1
        delegate_to: localhost
    
    - hosts: database-servers
      remote_user: '{{ username }}'
      vars:
        company: mycompany
        user: myusername
        password: mypassword
      tasks:
      - name: deploy logicmonitor hosts
        logicmonitor:
          target: host
          action: add
          collector: monitoring.dev.com
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
          properties:
            snmp.community: commstring
            type: db
            dc: 1
          groups: /servers/production/database, /datacenter1
        delegate_to: localhost
      - name: schedule 5 hour downtime for 2012-11-10 09:08
        logicmonitor:
          target: host
          action: sdt
          duration: 3000
          starttime: '2012-11-10 09:08'
          company: '{{ company }}'
          user: '{{ user }}'
          password: '{{ password }}'
        delegate_to: localhost

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
        <td> success </td>
        <td> flag indicating that execution was successful </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - You must have an existing LogicMonitor account for this module to function.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
