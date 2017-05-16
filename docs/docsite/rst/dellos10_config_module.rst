.. _dellos10_config:


dellos10_config - Manage Dell EMC Networking OS10 configuration sections
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* OS10 configurations use a simple block indent file syntax for segmenting configuration into sections.  This module provides an implementation for working with OS10 configuration sections in a deterministic way.




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
        <td><div>The ordered set of commands to append to the end of the command stack if a change needs to be made.  As with <em>before</em>, the playbook designer can use this argument  to append a set of commands to be executed after the command set.</div>        </td></tr>
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This argument causes the module to create a full backup of the current <code>running-config</code> from the remote device before any changes are made.  The backup file is written to the <code>backup</code> folder in the playbook root directory.  If the directory does not exist, it is created.</div>        </td></tr>
                <tr><td>before<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands to push on to the command stack if a change needs to be made.  The playbook designer can  use this argument to perform configuration commands prior to pushing any changes without affecting how the set of commands are matched against the system.</div>        </td></tr>
                <tr><td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The playbook designer can use the <code>config</code> argument to supply the base configuration to be used to validate necessary configuration changes.  If you specify this argument, the module does not download the running-config from the remote node.</div>        </td></tr>
                <tr><td>lines<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands that should be configured in the section.  The commands must be the exact same commands as found in the device running-config. Note the configuration command syntax as the device config parser automatically modifies some commands. This argument is mutually exclusive with <em>src</em>.</div></br>
    <div style="font-size: small;">aliases: commands<div>        </td></tr>
                <tr><td>match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>line</td>
        <td><ul><li>line</li><li>strict</li><li>exact</li><li>none</li></ul></td>
        <td><div>Instructs the module on the way to perform the matching of the set of commands against the current device config.  If you set match to <em>line</em>, commands match line by line.  If you set match to <em>strict</em>, command lines match by position.  If you set match to <em>exact</em>, command lines must be an equal match.  Finally, if you set match to <em>none</em>, the module does not attempt to compare the source configuration with the running configuration on the remote device.</div>        </td></tr>
                <tr><td>parents<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of parents that uniquely identify the section the commands should be checked against.  If you omit the parents argument, the commands are checked against the set of top level or global commands.</div>        </td></tr>
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
                <td><div>User to authenticate the SSH session to the remote device. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                    <tr><td>host<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                    <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Path to an ssh key used to authenticate the SSH session to the remote device.  If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                    <tr><td>timeout<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>10</td>
                <td></td>
                <td><div>Specifies idle timeout (in seconds) for the connection. Useful if the console freezes before continuing. For example when saving configurations.</div>        </td></tr>
                    <tr><td>password<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Password to authenticate the SSH session to the remote device. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
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
        <td><div>Instructs the module on the way to perform the configuration on the device. If you set the replace argument to <em>line</em>, then the modified lines push to the device in configuration mode.  If you set the replace argument to <em>block</em>, then the entire command block pushes to the device in configuration mode if any line is not correct.</div>        </td></tr>
                <tr><td>save<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>save</code> argument instructs the module to save the running- config to the startup-config at the conclusion of the module running.  If you specify check mode, this argument is ignored.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the source path to the file that contains the configuration or configuration template to load.  The path to the source file can either be the full path on the Ansible control host or a relative path from the playbook or role root dir.  This argument is mutually exclusive with <em>lines</em>.</div>        </td></tr>
                <tr><td>update<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>merge</td>
        <td><ul><li>merge</li><li>check</li></ul></td>
        <td><div>The <em>update</em> argument controls how the configuration statements are processed on the remote device.  Valid choices for the <em>update</em> argument are <em>merge</em> and <em>check</em>.  When you set the argument to <em>merge</em>, the configuration changes merge with the current device running configuration.  When you set the argument to <em>check</em>, the configuration updates are determined but not actually configured on the remote device.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - dellos10_config:
        lines: ['hostname {{ inventory_hostname }}']
        provider: "{{ cli }}"
    
    - dellos10_config:
        lines:
          - 10 permit ip host 1.1.1.1 any log
          - 20 permit ip host 2.2.2.2 any log
          - 30 permit ip host 3.3.3.3 any log
          - 40 permit ip host 4.4.4.4 any log
          - 50 permit ip host 5.5.5.5 any log
        parents: ['ip access-list test']
        before: ['no ip access-list test']
        match: exact
        provider: "{{ cli }}"
    
    - dellos10_config:
        lines:
          - 10 permit ip host 1.1.1.1 any log
          - 20 permit ip host 2.2.2.2 any log
          - 30 permit ip host 3.3.3.3 any log
          - 40 permit ip host 4.4.4.4 any log
        parents: ['ip access-list test']
        before: ['no ip access-list test']
        replace: block
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
        <td> saved </td>
        <td> Returns whether the configuration is saved to the startup configuration or not. </td>
        <td align=center> When not check_mode. </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> The set of commands pushed to the remote device. </td>
        <td align=center> Always. </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
            <tr>
        <td> responses </td>
        <td> The set of responses from issuing the commands on the device. </td>
        <td align=center> When not check_mode. </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
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
