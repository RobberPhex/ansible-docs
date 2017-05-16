.. _junos_command:


junos_command - Execute arbitrary commands on a remote device running Junos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Network devices running the Junos operating system provide a command driven interface both over CLI and RPC.  This module provides an interface to execute commands using these functions and return the results to the Ansible playbook.  In addition, the :ref:`junos_command <junos_command>` module can specify a set of conditionals to be evaluated against the returned output, only returning control to the playbook once the entire set of conditionals has been met.


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
    <td>commands<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An ordered set of CLI commands to be executed on the remote device.  The output from the commands is then returned to the playbook in the task results.</div></td></tr>
            <tr>
    <td>format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>xml</td>
        <td><ul><li>xml</li><li>text</li></ul></td>
        <td><div>Configures the encoding scheme to use when serializing output from the device.  This handles how to properly understand the output and apply the conditionals path to the result set.</div></td></tr>
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
        <td><div>Configures the interval in seconds to wait between retries of the command.  If the command does not pass the specified conditional, the interval indicates how to long to wait before trying the command again.</div></td></tr>
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
    <td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Specifies the number of retries a command should by tried before it is considered failed.  The command is run on the target device every retry and evaluated against the waitfor conditionals</div></td></tr>
            <tr>
    <td>rpcs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>rpcs</code> argument accepts a list of RPCs to be executed over a netconf session and the results from the RPC execution is return to the playbook via the modules results dictionary.</div></td></tr>
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
    <td>waitfor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies what to evaluate from the output of the command and what conditionals to apply.  This argument will cause the task to wait for a particular conditional or set of considitonals to be true before moving forward.   If the conditional is not true by the configured retries, the task fails.  See examples.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # the required set of connection arguments have been purposely left off
    # the examples for brevity
    
    - name: run a set of commands
      junos_command:
        commands: ['show version', 'show ip route']
    
    - name: run a command with a conditional applied to the second command
      junos_command:
        commands:
          - show version
          - show interfaces fxp0
        waitfor:
          - "result[1].interface-information.physical-interface.name eq fxp0"
    
    - name: collect interface information using rpc
      junos_command:
        rpcs:
          - "get_interface_information interface=em0 media=True"
          - "get_interface_information interface=fxp0 media=True"

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
        <td> xml </td>
        <td> The raw XML reply from the device </td>
        <td align=center> when format is xml </td>
        <td align=center> list </td>
        <td align=center> [['...', '...'], ['...', '...']] </td>
    </tr>
            <tr>
        <td> stdout_lines </td>
        <td> The output read from the device split into lines </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [['...', '...'], ['...', '...']] </td>
    </tr>
            <tr>
        <td> failed_conditionals </td>
        <td> the conditionals that failed </td>
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The output from the commands read from the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: This module requires the netconf system service be enabled on the remote device being managed


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

