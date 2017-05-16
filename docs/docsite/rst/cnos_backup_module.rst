.. _cnos_backup:


cnos_backup - Backup the current running or startup configuration to a remote server on devices running Lenovo CNOS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows you to work with switch configurations. It provides a way to back up the running or startup configurations of a switch to a remote server. This is achieved by periodically saving a copy of the startup or running configuration of the network device to a remote server using FTP, SFTP, TFTP, or SCP. The first step is to create a directory from where the remote server can be reached. The next step is to provide the full file path of the location where the configuration will be backed up. Authentication details required by the remote server must be provided as well. This module uses SSH to manage network device configuration. The results of the operation will be placed in a directory named 'results' that must be created by the user in their local directory to where the playbook is run. For more information about this module from Lenovo and customizing it usage for your use cases, please visit http://systemx.lenovofiles.com/help/index.jsp?topic=%2Fcom.lenovo.switchmgt.ansible.doc%2Fcnos_backup.html




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
                <tr><td>configType<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>running-config</li><li>startup-config</li></ul></td>
        <td><div>This specifies what type of configuration will be backed up. The choices are the running or startup configurations. There is no default value, so it will result in an error if the input is incorrect.</div>        </td></tr>
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
                <tr><td>protocol<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>SFTP</li><li>SCP</li><li>FTP</li><li>TFTP</li></ul></td>
        <td><div>This refers to the protocol used by the network device to interact with the remote server to where to upload the backup configuration. The choices are FTP, SFTP, TFTP, or SCP. Any other protocols will result in error. If this parameter is not specified, there is no default value to be used.</div>        </td></tr>
                <tr><td>rcpath<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This specifies the full file path where the configuration file will be copied on the remote server. In case the relative path is used as the variable value, the root folder for the user of the server needs to be specified.</div>        </td></tr>
                <tr><td>rcserverip<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>-This specifies the IP Address of the remote server to where the configuration will be backed up.</div>        </td></tr>
                <tr><td>serverpassword<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify the password for the server relating to the protocol used.</div>        </td></tr>
                <tr><td>serverusername<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify the username for the server relating to the protocol used.</div>        </td></tr>
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

    Tasks : The following are examples of using the module cnos_backup. These are written in the main.yml file of the tasks directory.
    ---
    - name: Test Running Config Backup
      cnos_backup:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_backup_{{ inventory_hostname }}_output.txt"
          configType: running-config
          protocol: "sftp"
          serverip: "10.241.106.118"
          rcpath: "/root/cnos/G8272-running-config.txt"
          serverusername: "root"
          serverpassword: "root123"
    
    - name: Test Startup Config Backup
      cnos_backup:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_backup_{{ inventory_hostname }}_output.txt"
          configType: startup-config
          protocol: "sftp"
          serverip: "10.241.106.118"
          rcpath: "/root/cnos/G8272-startup-config.txt"
          serverusername: "root"
          serverpassword: "root123"
    
    - name: Test Running Config Backup -TFTP
      cnos_backup:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_backup_{{ inventory_hostname }}_output.txt"
          configType: running-config
          protocol: "tftp"
          serverip: "10.241.106.118"
          rcpath: "/anil/G8272-running-config.txt"
          serverusername: "root"
          serverpassword: "root123"
    
    - name: Test Startup Config Backup - TFTP
      cnos_backup:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_backup_{{ inventory_hostname }}_output.txt"
          configType: startup-config
          protocol: "tftp"
          serverip: "10.241.106.118"
          rcpath: "/anil/G8272-startup-config.txt"
          serverusername: "root"
          serverpassword: "root123"
    

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
        <td align=center> Config file tranferred to server </td>
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
