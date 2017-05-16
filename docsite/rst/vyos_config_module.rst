.. _vyos_config:


vyos_config - Manage VyOS configuration on remote device
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module provides configuration file management of VyOS devices.  It provides arguments for managing both the configuration file and state of the active configuration.   All configuration statements are based on `set` and `delete` commands in the device configuration.




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
            <tr>
    <td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>backup</code> argument will backup the current devices active configuration to the Ansible control host prior to making any changes.  The backup file will be located in the backup folder in the root of the playbook</div></td></tr>
            <tr>
    <td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>configured by vyos_config</td>
        <td><ul></ul></td>
        <td><div>Allows a commit description to be specified to be included when the configuration is committed.  If the configuration is not changed or committed, this argument is ignored.</div></td></tr>
            <tr>
    <td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>config</code> argument specifies the base configuration to use to compare against the desired configuration.  If this value is not specified, the module will automatically retrieve the current active configuration from the remote device.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>lines<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ordered set of configuration lines to be managed and compared with the existing configuration on the remote device.</div></td></tr>
            <tr>
    <td>match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>line</td>
        <td><ul><li>line</li><li>none</li></ul></td>
        <td><div>The <code>match</code> argument controls the method used to match against the current active configuration.  By default, the desired config is matched against the active config and the deltas are loaded.  If the <code>match</code> argument is set to <code>none</code> the active configuration is ignored and the configuration is always loaded.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.   The value of <em>password</em> is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>22</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when building the connection to the remote device.</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convenience method that allows all <em>vyos</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>save<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>save</code> argument controls whether or not changes made to the active configuration are saved to disk.  This is independent of committing the config.  When set to True, the active configuration is saved.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>src</code> argument specifies the path to the source config file to load.  The source config file can either be in bracket format or set format.  The source file can include Jinja2 template variables.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.   The value of <em>ssh_keyfile</em> is the path to the key used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Specifies idle timeout for the connection. Useful if the console freezes before continuing. For example when saving configurations.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: examples below use the following provider dict to handle
    #       transport and authentication to the node.
    vars:
      cli:
        host: "{{ inventory_hostname }}"
        username: vyos
        password: vyos
        transport: cli
    
    - name: configure the remote device
      vyos_config:
        lines:
          - set system host-name {{ inventory_hostname }}
          - set service lldp
          - delete service dhcp-server
        provider: "{{ cli }}"
    
    - name: backup and load from file
      vyos_config:
        src: vyos.cfg
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
        <td> filtered </td>
        <td> The list of configuration commands removed to avoid a load failure </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> The list of configuration commands sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

