.. _asa_command:


asa_command - Run arbitrary commands on Cisco ASA devices
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Sends arbitrary commands to an ASA node and returns the results read from the device. The ``asa_command`` module includes an argument that will cause the module to wait for a specific condition before returning or timing out if the condition is not met.




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
                <tr><td>authorize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Instructs the module to enter privileged mode on the remote device before sending any commands.  If not specified, the device will attempt to execute all commands in non-privileged mode. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_AUTHORIZE</code> will be used instead.</div>        </td></tr>
                <tr><td>commands<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>List of commands to send to the remote device over the configured provider. The resulting output from the command is returned. If the <em>wait_for</em> argument is provided, the module is not returned until the condition is satisfied or the number of retires as expired.</div>        </td></tr>
                <tr><td>context<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies which context to target if you are running in the ASA in multiple context mode. Defaults to the current context you login to.</div>        </td></tr>
                <tr><td>interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Configures the interval in seconds to wait between retries of the command. If the command does not pass the specified conditions, the interval indicates how long to wait before trying the command again.</div>        </td></tr>
                <tr><td>match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>any</li><li>all</li></ul></td>
        <td><div>The <em>match</em> argument is used in conjunction with the <em>wait_for</em> argument to specify the match policy.  Valid values are <code>all</code> or <code>any</code>.  If the value is set to <code>all</code> then all conditionals in the wait_for must be satisfied.  If the value is set to <code>any</code> then only one of the values must be satisfied.</div>        </td></tr>
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
                    <tr><td>authorize<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td><ul><li>yes</li><li>no</li></ul></td>
                <td><div>Instructs the module to enter privileged mode on the remote device before sending any commands.  If not specified, the device will attempt to execute all commands in non-privileged mode. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_AUTHORIZE</code> will be used instead.</div>        </td></tr>
                    <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.   This value is the path to the key used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                    <tr><td>auth_pass<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>none</td>
                <td></td>
                <td><div>Specifies the password to use if required to enter privileged mode on the remote device.  If <em>authorize</em> is false, then this argument does nothing. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_AUTH_PASS</code> will be used instead.</div>        </td></tr>
                    <tr><td>host<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                    <tr><td>timeout<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>10</td>
                <td></td>
                <td><div>Specifies idle timeout in seconds for the connection, in seconds. Useful if the console freezes before continuing. For example when saving configurations.</div>        </td></tr>
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
                <tr><td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the number of retries a command should by tried before it is considered failed. The command is run on the target device every retry and evaluated against the <em>wait_for</em> conditions.</div>        </td></tr>
                <tr><td>wait_for<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of conditions to evaluate against the output of the command. The task will wait for each condition to be true before moving forward. If the conditional is not true within the configured number of retries, the task fails. See examples.</div></br>
    <div style="font-size: small;">aliases: waitfor<div>        </td></tr>
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
        username: cisco
        password: cisco
        authorize: yes
        auth_pass: cisco
        transport: cli
    
    ---
    - asa_command:
        commands:
          - show version
        provider: "{{ cli }}"
    
    - asa_command:
        commands:
          - show asp drop
          - show memory
        provider: "{{ cli }}"
    
    - asa_command:
        commands:
          - show version
        provider: "{{ cli }}"
        context: system

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
        <td> the set of responses from the commands </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
            <tr>
        <td> failed_conditions </td>
        <td> the conditionals that failed </td>
        <td align=center> failed </td>
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
