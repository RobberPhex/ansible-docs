.. _cnos_vlag:


cnos_vlag - Manage VLAG resources and attributes on devices running Lenovo CNOS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows you to work with virtual Link Aggregation Groups (vLAG) related configurations. The operators used are overloaded to ensure control over switch vLAG configurations. Apart from the regular device connection related attributes, there are four vLAG arguments which are overloaded variables that will perform further configurations. They are vlagArg1, vlagArg2, vlagArg3, and vlagArg4. For more details on how to use these arguments, see [Overloaded Variables]. This module uses SSH to manage network device configuration. The results of the operation will be placed in a directory named 'results' that must be created by the user in their local directory to where the playbook is run. For more information about this module from Lenovo and customizing it usage for your use cases, please visit http://systemx.lenovofiles.com/help/index.jsp?topic=%2Fcom.lenovo.switchmgt.ansible.doc%2Fcnos_vlag.html




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
                <tr><td>vlagArg1<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>enable</li><li>auto-recovery</li><li>config-consistency</li><li>isl</li><li>mac-address-table</li><li>peer-gateway</li><li>priority</li><li>startup-delay</li><li>tier-id</li><li>vrrp</li><li>instance</li><li>hlthchk</li></ul></td>
        <td><div>This is an overloaded vlag first argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>vlagArg2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Interval in seconds</li><li>disable or strict</li><li>Port Aggregation Number</li><li>VLAG priority</li><li>Delay time in seconds</li><li>VLAG tier-id value</li><li>VLAG instance number</li><li>keepalive-attempts</li><li>keepalive-interval</li><li>retry-interval</li><li>peer-ip</li></ul></td>
        <td><div>This is an overloaded vlag second argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>vlagArg3<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable or port-aggregation</li><li>Number of keepalive attempts</li><li>Interval in seconds</li><li>Interval in seconds</li><li>VLAG health check peer IP4 address</li></ul></td>
        <td><div>This is an overloaded vlag third argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>vlagArg4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Port Aggregation Number</li><li>default or management</li></ul></td>
        <td><div>This is an overloaded vlag fourth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    Tasks : The following are examples of using the module cnos_vlag. These are written in the main.yml file of the tasks directory.
    ---
    - name: Test Vlag  - enable
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "enable"
    
    - name: Test Vlag - autorecovery
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "auto-recovery"
          vlagArg2: 266
    
    - name: Test Vlag - config-consistency
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "config-consistency"
          vlagArg2: "strict"
    
    - name: Test Vlag - isl
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "isl"
          vlagArg2: 23
    
    - name: Test Vlag  - mac-address-table
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "mac-address-table"
    
    - name: Test Vlag - peer-gateway
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "peer-gateway"
    
    - name: Test Vlag - priority
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "priority"
          vlagArg2: 1313
    
    - name: Test Vlag - startup-delay
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "startup-delay"
          vlagArg2: 323
    
    - name: Test Vlag  - tier-id
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "tier-id"
          vlagArg2: 313
    
    - name: Test Vlag - vrrp
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "vrrp"
    
    - name: Test Vlag - instance
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "instance"
          vlagArg2: 33
          vlagArg3: 333
    
    - name: Test Vlag - instance2
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "instance"
          vlagArg2: "33"
    
    - name: Test Vlag  - keepalive-attempts
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "hlthchk"
          vlagArg2: "keepalive-attempts"
          vlagArg3: 13
    
    - name: Test Vlag - keepalive-interval
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "hlthchk"
          vlagArg2: "keepalive-interval"
          vlagArg3: 131
    
    - name: Test Vlag - retry-interval
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "hlthchk"
          vlagArg2: "retry-interval"
          vlagArg3: 133
    
    - name: Test Vlag - peer ip
      cnos_vlag:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username']}}"
          password: "{{ hostvars[inventory_hostname]['password']}}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType']}}"
          outputfile: "./results/cnos_vlag_{{ inventory_hostname }}_output.txt"
          vlagArg1: "hlthchk"
          vlagArg2: "peer-ip"
          vlagArg3: "1.2.3.4"
    

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
        <td align=center> vLAG configurations accomplished </td>
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
