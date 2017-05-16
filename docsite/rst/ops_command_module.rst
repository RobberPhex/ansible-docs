.. _ops_command:


ops_command - Run arbitrary commands on OpenSwitch devices.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Sends arbitrary commands to an OpenSwitch node and returns the results read from the device. This module includes an argument that will cause the module to wait for a specific condition before returning or timing out if the condition is not met.




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
    <td>commands<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of commands to send to the remote ops device over the configured provider. The resulting output from the command is returned. If the <em>wait_for</em> argument is provided, the module is not returned until the condition is satisfied or the number of retires as expired.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.  Note this argument does not affect the SSH argument.</div></td></tr>
            <tr>
    <td>interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Configures the interval in seconds to wait between <em>retries</em> of the command. If the command does not pass the specified conditions, the interval indicates how long to wait before trying the command again.</div></td></tr>
            <tr>
    <td>match<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>any</li><li>all</li></ul></td>
        <td><div>The <em>match</em> argument is used in conjunction with the <em>wait_for</em> argument to specify the match policy.  Valid values are <code>all</code> or <code>any</code>.  If the value is set to <code>all</code> then all conditionals in the <em>wait_for</em> must be satisfied.  If the value is set to <code>any</code> then only one of the values must be satisfied.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>rest</em> transports.  Note this argument does not affect the SSH transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>rest</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).  Note this argument does not affect the SSH transport.</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convenience method that allows all <em>openswitch</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Specifies the number of retries a command should by tried before it is considered failed. The command is run on the target device every retry and evaluated against the <em>wait_for</em> conditions.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>ssh</td>
        <td><ul><li>ssh</li><li>cli</li><li>rest</li></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over ssh, cli or REST.</div></td></tr>
            <tr>
    <td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <em>transport</em> argument is configured as rest.  If the transport argument is not <em>rest</em>, this value is ignored.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate either the CLI login or the eAPI authentication depending on which transport is used. Note this argument does not affect the SSH transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div></td></tr>
            <tr>
    <td>wait_for<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of conditions to evaluate against the output of the command. The task will wait for each condition to be true before moving forward. If the conditional is not true within the configured number of retries, the task fails. See examples.</div></br>
        <div style="font-size: small;">aliases: waitfor<div></td></tr>
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
        username: netop
        password: netop
        transport: cli
    
    - ops_command:
        commands:
          - show version
        provider: "{{ cli }}"
    
    - ops_command:
        commands:
          - show version
        wait_for:
          - "result[0] contains OpenSwitch"
        provider: "{{ cli }}"
    
    - ops_command:
        commands:
          - show version
          - show interfaces
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



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

