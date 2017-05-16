.. _junos_config:


junos_config - Manage configuration on remote devices running Junos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`junos_config <junos_config>` module provides an abstraction for working with the configuration running on remote devices.  It can perform operations that influence the configuration state.
This module provides an implementation for configuring Juniper JUNOS devices.  The configuration statements must start with either `set` or `delete` and are compared against the current device configuration and only changes are pushed to the device.


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
            <tr>
    <td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>configured by junos_config</td>
        <td><ul></ul></td>
        <td><div>The <code>comment</code> argument specifies a text string to be used when committing the configuration.  If the <code>confirm</code> argument is set to False, this argument is silently ignored.</div></td></tr>
            <tr>
    <td>confirm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>confirm</code> argument will configure a time out value for the commit to be confirmed before it is automatically rolled back.  If the <code>confirm</code> argument is set to False, this argument is silently ignored.  If the value for this argument is set to 0, the commit is confirmed immediately.</div></td></tr>
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
        <td><div>The path to the config source.  The source can be either a file with config or a template that will be merged during runtime.  By default the task will search for the source file in role or playbook root folder in templates directory.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.   The value of <em>password</em> is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_PASSWORD will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>22</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when buiding the connection to the remote device.  The port value will default to the well known SSH port of 22</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convience method that allows all <span class='module'>ios</span> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>replace<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>replace</code> argument will instruct the remote device to replace the current configuration hierarchy with the one specified in the corresponding hierarchy of the source configuraiton loaded from this module.</div></td></tr>
            <tr>
    <td>rollback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>rollback</code> argument instructs the module to rollback the current configuration to the identifier specified in the argument.  If the specified rollback identifier does not exist on the remote device, the module will fail.  To rollback to the most recent commit, set the <code>rollback</code> argument to 0</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.   The value of <em>ssh_keyfile</em> is the path to the key used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_SSH_KEYFILE will be used instead.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the usename to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_USERNAME will be used instead.</div></td></tr>
            <tr>
    <td>zeroize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>zeroize</code> argument is used to completely ssantaize the remote device configuration back to initial defaults.  This argument will effectively remove all current configuration statements on the remote device</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: load configuration lines in device
      junos_config:
        lines:
          - set system host-name {{ inventory_hostname }}
          - delete interfaces ge-0/0/0 description
        comment: update config
    
    - name: rollback the configuration to id 10
      junos_config:
        rollback: 10
    
    - name: zero out the current configuration
      junos_config:
        zeroize: yes
    
    - name: confirm a candidate configuration
      junos_config:


Notes
-----

.. note:: This module requires the netconf system service be enabled on the remote device being managed


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

