.. _dellos9_command:


dellos9_command - Run commands on remote devices running Dell OS9
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Sends arbitrary commands to a Dell OS9 node and returns the results read from the device. This  module includes an argument that will cause the module to wait for a specific condition before returning or timing out if the condition is not met.
This module does not support running commands in configuration mode. Please use :ref:`dellos9_config <dellos9_config>` to configure Dell OS9 devices.




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
    <td>auth_pass<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use if required to enter privileged mode on the remote device.  If <em>authorize</em> is false, then this argument does nothing. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_AUTH_PASS will be used instead.</div></td></tr>
            <tr>
    <td>authorize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Instructs the module to enter priviledged mode on the remote device before sending any commands.  If not specified, the device will attempt to excecute all commands in non-priviledged mode. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_AUTHORIZE will be used instead.</div></td></tr>
            <tr>
    <td>commands<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of commands to send to the remote dellos9 device over the configured provider. The resulting output from the command is returned. If the <em>wait_for</em> argument is provided, the module is not returned until the condition is satisfied or the number of retries has expired.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Configures the interval in seconds to wait between retries of the command. If the command does not pass the specified conditions, the interval indicates how long to wait before trying the command again.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password to authenticate the SSH session to the remote device. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_PASSWORD will be used instead.</div></td></tr>
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
        <td><div>Convenience method that allows all <span class='module'>dellos9</span> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Specifies the number of retries a command should be tried before it is considered failed. The command is run on the target device every retry and evaluated against the <em>wait_for</em> conditions.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to an ssh key used to authenticate the SSH session to the remote device.  If the value is not specified in the task, the value of environment variable ANSIBLE_NET_SSH_KEYFILE will be used instead.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Specifies idle timeout (in seconds) for the connection. Useful if the console freezes before continuing. For example when saving configurations.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>User to authenticate the SSH session to the remote device. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_USERNAME will be used instead.</div></td></tr>
            <tr>
    <td>wait_for<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of conditions to evaluate against the output of the command. The task will wait for each condition to be true before moving forward. If the conditional is not true within the configured number of <em>retries</em>, the task fails. See examples.</div></td></tr>
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
        username: admin
        password: admin
        transport: cli
    
    tasks:
      - name: run show version on remote devices
        dellos9_command:
          commands: show version
          provider: "{{ cli }}"
    
      - name: run show version and check to see if output contains OS9
        dellos9_command:
          commands: show version
          wait_for: result[0] contains OS9
          provider: "{{ cli }}"
    
      - name: run multiple commands on remote nodes
        dellos9_command:
          commands:
            - show version
            - show interfaces
          provider: "{{ cli }}"
    
      - name: run multiple commands and evaluate the output
        dellos9_command:
          commands:
            - show version
            - show interfaces
          wait_for:
            - result[0] contains OS9
            - result[1] contains Loopback
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
        <td> stdout_lines </td>
        <td> The value of stdout split into a list </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [['...', '...'], ['...'], ['...']] </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the commands </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
            <tr>
        <td> failed_conditions </td>
        <td> The list of conditionals that have failed </td>
        <td align=center> failed </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
            <tr>
        <td> warnings </td>
        <td> The list of warnings (if any) generated by module based on arguments </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: This module requires Dell OS9 version 9.10.0.1P13 or above.
.. note:: This module requires to increase the ssh connection rate limit. Use the following command *ip ssh connection-rate-limit 60* to configure the same. This can be done via :ref:`dnos_config <dnos_config>` module as well.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

