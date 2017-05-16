.. _iosxr_command:


iosxr_command - Run arbitrary commands on ios devices.
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Sends arbitrary commands to an IOSXR node and returns the results read from the device. The :ref:`iosxr_command <iosxr_command>` module includes an argument that will cause the module to wait for a specific condition before returning or timing out if the condition is not met.




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
        <td><div>List of commands to send to the remote ios device over the configured provider. The resulting output from the command is returned. If the <em>waitfor</em> argument is provided, the module is not returned until the condition is satisfied or the number of retires as expired.</div></td></tr>
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
        <td><div>Convience method that allows all <span class='module'>iosxr</span> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Specifies the number of retries a command should by tried before it is considered failed. The command is run on the target device every retry and evaluated against the waitfor conditions.</div></td></tr>
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
        <td><div>List of conditions to evaluate against the output of the command. The task will wait for a each condition to be true before moving forward. If the conditional is not true within the configured number of retries, the task fails. See examples.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - iosxr_command:
        commands:
          - show version
      register: output
    
    - iosxr_command:
        commands:
          - show version
        waitfor:
          - "result[0] contains 6.0.0"
    
    - iosxr_command:
      commands:
        - show version
        - show interfaces
      waitfor:
        - "result[1] contains MgmtEth0/0/CPU0/0"
        - "result[0] contains 6.0.0"
    

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
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

