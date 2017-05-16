.. _cnos_vlan:


cnos_vlan - Manage VLAN resources and attributes on devices running Lenovo CNOS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows you to work with VLAN related configurations. The operators used are overloaded to ensure control over switch VLAN configurations. The first level of VLAN configuration allows to set up the VLAN range, the VLAN tag persistence, a VLAN access map and access map filter. After passing this level, there are five VLAN arguments that will perform further configurations. They are vlanArg1, vlanArg2, vlanArg3, vlanArg4, and vlanArg5. The value of vlanArg1 will determine the way following arguments will be evaluated. For more details on how to use these arguments, see [Overloaded Variables]. This module uses SSH to manage network device configuration. The results of the operation will be placed in a directory named 'results' that must be created by the user in their local directory to where the playbook is run. For more information about this module from Lenovo and customizing it usage for your use cases, please visit http://systemx.lenovofiles.com/help/index.jsp?topic=%2Fcom.lenovo.switchmgt.ansible.doc%2Fcnos_vlan.html




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
                <tr><td>deviceType<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>g8272_cnos</li><li>g8296_cnos</li><li>g8332_cnos</li></ul></td>
        <td><div>This specifies the type of device where the method is executed.</div>        </td></tr>
                <tr><td>enablePassword<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configures the password used to enter Global Configuration command mode on the switch. If the switch does not request this password, the parameter is ignored.While generally the value should come from the inventory file, you can also specify it as a variable. This parameter is optional. If it is not specified, no default value will be used.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This is the variable used to search the hosts file at /etc/ansible/hosts and identify the IP address of the device on which the template is going to be applied. Usually the Ansible keyword {{ inventory_hostname }} is specified in the playbook as an abstraction of the group of network elements that need to be configured.</div>        </td></tr>
                <tr><td>outputfile<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This specifies the file path where the output of each command execution is saved. Each command that is specified in the merged template file and each response from the device are saved here. Usually the location is the results folder, but you can choose another location based on your write permission.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Configures the password used to authenticate the connection to the remote device. The value of the password parameter is used to authenticate the SSH session. While generally the value should come from the inventory file, you can also specify it as a variable. This parameter is optional. If it is not specified, no default value will be used.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Configures the username used to authenticate the connection to the remote device. The value of the username parameter is used to authenticate the SSH session. While generally the value should come from the inventory file, you can also specify it as a variable. This parameter is optional. If it is not specified, no default value will be used.</div>        </td></tr>
                <tr><td>vlanArg1<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>access-map</li><li>dot1q</li><li>filter</li><li><1-3999> VLAN ID 1-3999 or range</li></ul></td>
        <td><div>This is an overloaded vlan first argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>vlanArg2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>VLAN Access Map name</li><li>egress-only</li><li>name</li><li>flood</li><li>state</li><li>ip</li></ul></td>
        <td><div>This is an overloaded vlan second argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>vlanArg3<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>action</li><li>match</li><li>statistics</li><li>enter VLAN id or range of vlan</li><li>ascii name for the VLAN</li><li>ipv4 or ipv6</li><li>active or suspend</li><li>fast-leave</li><li>last-member-query-interval</li><li>mrouter</li><li>querier</li><li>querier-timeout</li><li>query-interval</li><li>query-max-response-time</li><li>report-suppression</li><li>robustness-variable</li><li>startup-query-count</li><li>startup-query-interval</li><li>static-group</li></ul></td>
        <td><div>This is an overloaded vlan third argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>vlanArg4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>drop or forward or redirect</li><li>ip or mac</li><li>Interval in seconds</li><li>ethernet</li><li>port-aggregation</li><li>Querier IP address</li><li>Querier Timeout in seconds</li><li>Query Interval in seconds</li><li>Query Max Response Time in seconds</li><li>Robustness Variable value</li><li>Number of queries sent at startup</li><li>Query Interval at startup</li></ul></td>
        <td><div>This is an overloaded vlan fourth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>vlanArg5<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>access-list name</li><li>Slot/chassis number</li><li>Port Aggregation Number</li></ul></td>
        <td><div>This is an overloaded vlan fifth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    Tasks: The following are examples of using the module cnos_vlan. These are written in the main.yml file of the tasks directory.
    ---
    - name: Test Vlan - Create a vlan, name it
      cnos_vlan:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_vlan_{{ inventory_hostname }}_output.txt"
          vlanArg1: 13
          vlanArg2: "name"
          vlanArg3: "Anil"
    
    - name: Test Vlan - Create a vlan, Flood configuration
      cnos_vlan:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_vlan_{{ inventory_hostname }}_output.txt"
          vlanArg1: 13
          vlanArg2: "flood"
          vlanArg3: "ipv4"
    
    - name: Test Vlan - Create a vlan, State configuration
      cnos_vlan:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_vlan_{{ inventory_hostname }}_output.txt"
          vlanArg1: 13
          vlanArg2: "state"
          vlanArg3: "active"
    
    - name: Test Vlan - VLAN Access map1
      cnos_vlan:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_vlan_{{ inventory_hostname }}_output.txt"
          vlanArg1: "access-map"
          vlanArg2: "Anil"
          vlanArg3: "statistics"
    
    - name: Test Vlan - VLAN Accep Map2
      cnos_vlan:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_vlan_{{ inventory_hostname }}_output.txt"
          vlanArg1: "access-map"
          vlanArg2: "Anil"
          vlanArg3: "action"
          vlanArg4: "forward"
    
    - name: Test Vlan - ip igmp snooping query interval
      cnos_vlan:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_vlan_{{ inventory_hostname }}_output.txt"
          vlanArg1: 13
          vlanArg2: "ip"
          vlanArg3: "query-interval"
          vlanArg4: 1313
    
    - name: Test Vlan - ip igmp snooping mrouter interface port-aggregation 23
      cnos_vlan:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_vlan_{{ inventory_hostname }}_output.txt"
          vlanArg1: 13
          vlanArg2: "ip"
          vlanArg3: "mrouter"
          vlanArg4: "port-aggregation"
          vlanArg5: 23
    

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
        <td> msg </td>
        <td> Success or failure message </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> VLAN configuration is accomplished </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
