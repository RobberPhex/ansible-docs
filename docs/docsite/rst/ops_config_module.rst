.. _ops_config:


ops_config - Manage OpenSwitch configuration using CLI
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* OpenSwitch configurations use a simple block indent file syntax for segmenting configuration into sections.  This module provides an implementation for working with ops configuration sections in a deterministic way.




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
                <tr><td>before<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands to push on to the command stack if a change needs to be made.  This allows the playbook designer the opportunity to perform configuration commands prior to pushing any changes without affecting how the set of commands are matched against the system.</div>        </td></tr>
                <tr><td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The module, by default, will connect to the remote device and retrieve the current running-config to use as a base for comparing against the contents of source.  There are times when it is not desirable to have the task get the current running-config for every task in a playbook.  The <em>config</em> argument allows the implementer to pass in the configuration to use as the base config for comparison.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The force argument instructs the module to not consider the current devices running-config.  When set to true, this will cause the module to push the contents of <em>src</em> into the device without first checking if already configured.</div><div>Note this argument should be considered deprecated.  To achieve the equivalent, set the <code>match=none</code> which is idempotent.  This argument will be removed in a future release.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.  Note this argument does not affect the SSH argument.</div>        </td></tr>
                <tr><td>lines<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands that should be configured in the section.  The commands must be the exact same commands as found in the device running-config.  Be sure to note the configuration command syntax as some commands are automatically modified by the device config parser.</div>        </td></tr>
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
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>rest</em> transports.  Note this argument does not affect the SSH transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>rest</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).  Note this argument does not affect the SSH transport.</div>        </td></tr>
                <tr><td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Convenience method that allows all <em>openswitch</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div>        </td></tr>
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
        <td><div>The <em>src</em> argument provides a path to the configuration file to load into the remote system.  The path can either be a full system path to the configuration file if the value starts with / or relative to the root of the implemented role or playbook. This argument is mutually exclusive with the <em>lines</em> and <em>parents</em> arguments.</div>        </td></tr>
                <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error.</div>        </td></tr>
                <tr><td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>ssh</td>
        <td><ul><li>ssh</li><li>cli</li><li>rest</li></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over ssh, cli or REST.</div>        </td></tr>
                <tr><td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <em>transport</em> argument is configured as rest.  If the transport argument is not <em>rest</em>, this value is ignored.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate either the CLI login or the eAPI authentication depending on which transport is used. Note this argument does not affect the SSH transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
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
        username: netop
        password: netop
    
    ---
    - name: configure hostname over cli
      ops_config:
        lines:
          - "hostname {{ inventory_hostname }}"
        provider: "{{ cli }}"
    
    
    - name: configure vlan 10 over cli
      ops_config:
        lines:
          - no shutdown
        parents:
          - vlan 10
        provider: "{{ cli }}"
    
    - name: load config from file
      ops_config:
        src: ops01.cfg
        backup: yes
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
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
            <tr>
        <td> backup_path </td>
        <td> The full path to the backup file </td>
        <td align=center> when backup is yes </td>
        <td align=center> path </td>
        <td align=center> /playbooks/ansible/backup/ops_config.2016-07-16@22:28:34 </td>
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
