.. _ordnance_config:


ordnance_config - Manage Ordnance configuration sections
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Ordnance router configurations use a simple block indent file syntax for segmenting configuration into sections.  This module provides an implementation for working with these configuration sections in a deterministic way.




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
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This argument will cause the module to create a full backup of the current <code>running-config</code> from the remote device before any changes are made.  The backup file is written to the <code>backup</code> folder in the playbook root directory.  If the directory does not exist, it is created.</div>        </td></tr>
                <tr><td>before<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands to push on to the command stack if a change needs to be made.  This allows the playbook designer the opportunity to perform configuration commands prior to pushing any changes without affecting how the set of commands are matched against the system.</div>        </td></tr>
                <tr><td>commands<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands that should be configured in the section.  The commands must be the exact same commands as found in the device running-config.  Be sure to note the configuration command syntax as some commands are automatically modified by the device config parser.</div></br>
    <div style="font-size: small;">aliases: commands<div>        </td></tr>
                <tr><td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The <code>config</code> argument allows the playbook designer to supply the base configuration to be used to validate configuration changes necessary.  If this argument is provided, the module will not download the running-config from the remote node.</div>        </td></tr>
                <tr><td>defaults<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This argument specifies whether or not to collect all defaults when getting the remote device running config.  When enabled, the module will get the current config by issuing the command <code>show running-config all</code>.</div>        </td></tr>
                <tr><td>match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>line</td>
        <td><ul><li>line</li><li>strict</li><li>exact</li><li>none</li></ul></td>
        <td><div>Instructs the module on the way to perform the matching of the set of commands against the current device config.  If match is set to <em>line</em>, commands are matched line by line.  If match is set to <em>strict</em>, command lines are matched with respect to position.  If match is set to <em>exact</em>, command lines must be an equal match.  Finally, if match is set to <em>none</em>, the module will not attempt to compare the source configuration with the running configuration on the remote device.</div>        </td></tr>
                <tr><td>multiline_delimiter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>@</td>
        <td></td>
        <td><div>This arugment is used when pushing a multiline configuration element to the Ordnance router.  It specifies the character to use as the delimiting character.  This only applies to the configuration action</div>        </td></tr>
                <tr><td>parents<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of parents that uniquely identify the section the commands should be checked against.  If the parents argument is omitted, the commands are checked against the set of top level or global commands.</div>        </td></tr>
                <tr><td>replace<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>line</td>
        <td><ul><li>line</li><li>block</li></ul></td>
        <td><div>Instructs the module on the way to perform the configuration on the device.  If the replace argument is set to <em>line</em> then the modified lines are pushed to the device in configuration mode.  If the replace argument is set to <em>block</em> then the entire command block is pushed to the device in configuration mode if any line is not correct.</div>        </td></tr>
                <tr><td>save<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>save</code> argument instructs the module to save the running- config to the startup-config at the conclusion of the module running.  If check mode is specified, this argument is ignored.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the source path to the file that contains the configuration or configuration template to load.  The path to the source file can either be the full path on the Ansible control host or a relative path from the playbook or role root directory.  This argument is mutually exclusive with <em>lines</em>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # Note: examples below use the following provider dict to handle
    #       transport and authentication to the node.
    vars:
      cli:
        host: "{{ inventory_hostname }}"
        username: RouterName
        password: password
        transport: cli
    
    ---
    - name: configure top level configuration
      ordnance_config:
        lines: hostname {{ inventory_hostname }}
        provider: "{{ cli }}"
    
    - name: configure interface settings
      ordnance_config:
        lines:
          - description test interface
          - ip address 172.31.1.1 255.255.255.0
        parents: interface Ethernet1
        provider: "{{ cli }}"
    
    - name: configure bgp router
      ordnance_config:
        lines:
          - neighbor 1.1.1.1 remote-as 1234
          - network 10.0.0.0/24
        parents: router bgp 65001
        provider: "{{ cli }}"
    

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
        <td> updates </td>
        <td> The set of commands that will be pushed to the remote device </td>
        <td align=center> Only when commands is specified. </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
            <tr>
        <td> backup_path </td>
        <td> The full path to the backup file </td>
        <td align=center> when backup is yes </td>
        <td align=center> path </td>
        <td align=center> /playbooks/ansible/backup/ordnance_config.2016-07-16@22:28:34 </td>
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
