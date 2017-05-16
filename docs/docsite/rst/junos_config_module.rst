.. _junos_config:


junos_config - Manage configuration on devices running Juniper JUNOS
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module provides an implementation for working with the active configuration running on Juniper JUNOS devices.  It provides a set of arguments for loading configuration, performing rollback operations and zeroing the active configuration on the device.


Requirements (on host that executes module)
-------------------------------------------

  * junos-eznc


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
                <tr><td>backup<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This argument will cause the module to create a full backup of the current <code>running-config</code> from the remote device before any changes are made.  The backup file is written to the <code>backup</code> folder in the playbook root directory.  If the directory does not exist, it is created.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>configured by junos_config</td>
        <td></td>
        <td><div>The <code>comment</code> argument specifies a text string to be used when committing the configuration.  If the <code>confirm</code> argument is set to False, this argument is silently ignored.</div>        </td></tr>
                <tr><td>confirm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The <code>confirm</code> argument will configure a time out value for the commit to be confirmed before it is automatically rolled back.  If the <code>confirm</code> argument is set to False, this argument is silently ignored.  If the value for this argument is set to 0, the commit is confirmed immediately.</div>        </td></tr>
                <tr><td>lines<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This argument takes a list of <code>set</code> or <code>delete</code> configuration lines to push into the remote device.  Each line must start with either <code>set</code> or <code>delete</code>.  This argument is mutually exclusive with the <em>src</em> argument.</div>        </td></tr>
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
                <td><div>Specifies the port to use when building the connection to the remote device.  The port value will default to the well known SSH port of 22 (for <code>transport=cli</code>) or port 830 (for <code>transport=netconf</code>) device.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>replace<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>replace</code> argument will instruct the remote device to replace the current configuration hierarchy with the one specified in the corresponding hierarchy of the source configuration loaded from this module.</div><div>Note this argument should be considered deprecated.  To achieve the equivalent, set the <em>update</em> argument to <code>replace</code>. This argument will be removed in a future release. The <code>replace</code> and <code>update</code> argument is mutually exclusive.</div>        </td></tr>
                <tr><td>rollback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The <code>rollback</code> argument instructs the module to rollback the current configuration to the identifier specified in the argument.  If the specified rollback identifier does not exist on the remote device, the module will fail.  To rollback to the most recent commit, set the <code>rollback</code> argument to 0.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The <em>src</em> argument provides a path to the configuration file to load into the remote system.  The path can either be a full system path to the configuration file if the value starts with / or relative to the root of the implemented role or playbook. This argument is mutually exclusive with the <em>lines</em> argument.</div>        </td></tr>
                <tr><td>src_format<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>xml</li><li>set</li><li>text</li><li>json</li></ul></td>
        <td><div>The <em>src_format</em> argument specifies the format of the configuration found int <em>src</em>.  If the <em>src_format</em> argument is not provided, the module will attempt to determine the format of the configuration file specified in <em>src</em>.</div>        </td></tr>
                <tr><td>update<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>merge</td>
        <td><ul><li>merge</li><li>override</li><li>replace</li></ul></td>
        <td><div>This argument will decide how to load the configuration data particulary when the candidate configuration and loaded configuration contain conflicting statements. Following are accepted values. <code>merge</code> combines the data in the loaded configuration with the candidate configuration. If statements in the loaded configuration conflict with statements in the candidate configuration, the loaded statements replace the candidate ones. <code>override</code> discards the entire candidate configuration and replaces it with the loaded configuration. <code>replace</code> substitutes each hierarchy level in the loaded configuration for the corresponding level.</div>        </td></tr>
                <tr><td>zeroize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The <code>zeroize</code> argument is used to completely sanitize the remote device configuration back to initial defaults.  This argument will effectively remove all current configuration statements on the remote device.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: load configure file into device
      junos_config:
        src: srx.cfg
        comment: update config
        provider: "{{ netconf }}"
    
    - name: rollback the configuration to id 10
      junos_config:
        rollback: 10
        provider: "{{ netconf }}"
    
    - name: zero out the current configuration
      junos_config:
        zeroize: yes
        provider: "{{ netconf }}"
    
    - name: confirm a previous commit
      junos_config:
        provider: "{{ netconf }}"

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
        <td> backup_path </td>
        <td> The full path to the backup file </td>
        <td align=center> when backup is yes </td>
        <td align=center> path </td>
        <td align=center> /playbooks/ansible/backup/config.2016-07-16@22:28:34 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - This module requires the netconf system service be enabled on the remote device being managed.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
