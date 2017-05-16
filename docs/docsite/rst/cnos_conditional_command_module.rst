.. _cnos_conditional_command:


cnos_conditional_command - Execute a single command based on condition on devices running Lenovo CNOS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows you to modify the running configuration of a switch. It provides a way to execute a single CNOS command on a network device by evaluating the current running configuration and executing the command only if the specific settings have not been already configured. The CNOS command is passed as an argument of the method. This module functions the same as the cnos_command module. The only exception is that the following inventory variable can be specified [“condition = <flag string>”] When this inventory variable is specified as the variable of a task, the command is executed for the network element that matches the flag string. Usually, commands are executed across a group of network devices. When there is a requirement to skip the execution of the command on one or more devices, it is recommended to use this module. This module uses SSH to manage network device configuration. For more information about this module from Lenovo and customizing it usage for your use cases, please visit http://systemx.lenovofiles.com/help/index.jsp?topic=%2Fcom.lenovo.switchmgt.ansible.doc%2Fcnos_conditional_command.html




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
                <tr><td>clicommand<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This specifies the CLI command as an attribute to this method. The command is passed using double quotes. The variables can be placed directly on to the CLI commands or can be invoked from the vars directory.</div>        </td></tr>
                <tr><td>condition<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>If you specify condition=false in the inventory file against any device, the command execution is skipped for that device.</div>        </td></tr>
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
                <tr><td>flag<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>If a task needs to be executed, you have to set the flag the same as it is specified in the inventory for that device.</div>        </td></tr>
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
        </table>
    </br>



Examples
--------

 ::

    Tasks : The following are examples of using the module cnos_conditional_command. These are written in the main.yml file of the tasks directory.
    ---
    - name: Applying CLI template on VLAG Tier1 Leaf Switch1
      cnos_conditional_command:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_conditional_command_{{ inventory_hostname }}_output.txt"
          condition: "{{ hostvars[inventory_hostname]['condition']}}"
          flag: leaf_switch2
          command: "spanning-tree mode enable"
          enablePassword: "anil"
    

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
        <td align=center> Command Applied </td>
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
