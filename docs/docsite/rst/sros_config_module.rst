.. _sros_config:


sros_config - Manage Nokia SR OS device configuration
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Nokia SR OS configurations use a simple block indent file syntax for segmenting configuration into sections.  This module provides an implementation for working with SR OS configuration sections in a deterministic way.




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
                <tr><td>after<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands to append to the end of the command stack if a change needs to be made.  Just like with <em>before</em> this allows the playbook designer to append a set of commands to be executed after the command set.</div>        </td></tr>
                <tr><td>backup<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This argument will cause the module to create a full backup of the current <code>running-config</code> from the remote device before any changes are made.  The backup file is written to the <code>backup</code> folder in the playbook root directory.  If the directory does not exist, it is created.</div>        </td></tr>
                <tr><td>before<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands to push on to the command stack if a change needs to be made.  This allows the playbook designer the opportunity to perform configuration commands prior to pushing any changes without affecting how the set of commands are matched against the system.</div>        </td></tr>
                <tr><td>config<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The <code>config</code> argument allows the playbook designer to supply the base configuration to be used to validate configuration changes necessary.  If this argument is provided, the module will not download the running-config from the remote node.</div>        </td></tr>
                <tr><td>defaults<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This argument specifies whether or not to collect all defaults when getting the remote device running config.  When enabled, the module will get the current config by issuing the command <code>show running-config all</code>.</div></br>
    <div style="font-size: small;">aliases: detail<div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>The force argument instructs the module to not consider the current devices running-config.  When set to true, this will cause the module to push the contents of <em>src</em> into the device without first checking if already configured.</div><div>Note this argument should be considered deprecated.  To achieve the equivalent, set the <code>match=none</code> which is idempotent.  This argument will be removed in a future release.</div>        </td></tr>
                <tr><td>lines<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands that should be configured in the section.  The commands must be the exact same commands as found in the device running-config.  Be sure to note the configuration command syntax as some commands are automatically modified by the device config parser.</div></br>
    <div style="font-size: small;">aliases: commands<div>        </td></tr>
                <tr><td>match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>line</td>
        <td><ul><li>line</li><li>strict</li><li>exact</li><li>none</li></ul></td>
        <td><div>Instructs the module on the way to perform the matching of the set of commands against the current device config.  If match is set to <em>line</em>, commands are matched line by line.  If match is set to <em>strict</em>, command lines are matched with respect to position.  If match is set to <em>exact</em>, command lines must be an equal match.  Finally, if match is set to <em>none</em>, the module will not attempt to compare the source configuration with the running configuration on the remote device.</div>        </td></tr>
                <tr><td>parents<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of parents that uniquely identify the section the commands should be checked against.  If the parents argument is omitted, the commands are checked against the set of top level or global commands.</div>        </td></tr>
                <tr><td rowspan="2">provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td><td></td>
    <td> <div>A dict object containing connection details.</div>    </tr>
    <tr>
    <td colspan="5">
    <table border=1 cellpadding=4>
    <caption><b>Dictionary object provider</b></caption>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                    <tr><td>username<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                    <tr><td>host<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                    <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.   This value is the path to the key used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                    <tr><td>timeout<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>10</td>
                <td></td>
                <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error.</div>        </td></tr>
                    <tr><td>password<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the password to use to authenticate the connection to the remote device.   This value is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                    <tr><td>port<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>22</td>
                <td></td>
                <td><div>Specifies the port to use when building the connection to the remote device.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>replace<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>line</td>
        <td><ul><li>line</li><li>block</li></ul></td>
        <td><div>Instructs the module on the way to perform the configuration on the device.  If the replace argument is set to <em>line</em> then the modified lines are pushed to the device in configuration mode.  If the replace argument is set to <em>block</em> then the entire command block is pushed to the device in configuration mode if any line is not correct.</div>        </td></tr>
                <tr><td>save<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>save</code> argument instructs the module to save the running- config to the startup-config at the conclusion of the module running.  If check mode is specified, this argument is ignored.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the source path to the file that contains the configuration or configuration template to load.  The path to the source file can either be the full path on the Ansible control host or a relative path from the playbook or role root directory.  This argument is mutually exclusive with <em>lines</em>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: examples below use the following provider dict to handle
    #       transport and authentication to the node.
    ---
    vars:
      cli:
        host: "{{ inventory_hostname }}"
        username: admin
        password: admin
        transport: cli
    
    ---
    - name: enable rollback location
      sros_config:
        lines: configure system rollback rollback-location "cf3:/ansible"
        provider: "{{ cli }}"
    
    - name: set system name to {{ inventory_hostname }} using one line
      sros_config:
        lines:
            - configure system name "{{ inventory_hostname }}"
        provider: "{{ cli }}"
    
    - name: set system name to {{ inventory_hostname }} using parents
      sros_config:
        lines:
            - 'name "{{ inventory_hostname }}"'
        parents:
            - configure
            - system
        provider: "{{ cli }}"
        backup: yes
    
    - name: load config from file
      sros_config:
          src: "{{ inventory_hostname }}.cfg"
          provider: "{{ cli }}"
          save: yes

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
        <td> commands </td>
        <td> The set of commands that will be pushed to the remote device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['config system name "sros01"'] </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> The set of commands that will be pushed to the remote device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['config system name "sros01"'] </td>
    </tr>
            <tr>
        <td> backup_path </td>
        <td> The full path to the backup file </td>
        <td align=center> when backup is yes </td>
        <td align=center> path </td>
        <td align=center> /playbooks/ansible/backup/sros_config.2016-07-16@22:28:34 </td>
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
