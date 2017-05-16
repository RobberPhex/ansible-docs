.. _vyos_command:


vyos_command - Run one or more commands on VyOS devices
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The command module allows running one or more commands on remote devices running VyOS.  This module can also be introspected to validate key parameters before returning successfully.  If the conditional statements are not met in the wait period, the task fails.
* Certain ``show`` commands in VyOS produce many lines of output and use a custom pager that can cause this module to hang.  If the value of the environment variable ``ANSIBLE_VYOS_TERMINAL_LENGTH`` is not set, the default number of 10000 is used.




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
                <tr><td>commands<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The ordered set of commands to execute on the remote device running VyOS.  The output from the command execution is returned to the playbook.  If the <em>wait_for</em> argument is provided, the module is not returned until the condition is satisfied or the number of retries has been exceeded.</div>        </td></tr>
                <tr><td>interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Configures the interval in seconds to wait between <em>retries</em> of the command. If the command does not pass the specified conditions, the interval indicates how long to wait before trying the command again.</div>        </td></tr>
                <tr><td>match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>any</li><li>all</li></ul></td>
        <td><div>The <em>match</em> argument is used in conjunction with the <em>wait_for</em> argument to specify the match policy. Valid values are <code>all</code> or <code>any</code>.  If the value is set to <code>all</code> then all conditionals in the wait_for must be satisfied.  If the value is set to <code>any</code> then only one of the values must be satisfied.</div>        </td></tr>
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
                <td><div>Specifies the port to use when building the connection to the remote device.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the number of retries a command should be tried before it is considered failed. The command is run on the target device every retry and evaluated against the <em>wait_for</em> conditionals.</div>        </td></tr>
                <tr><td>wait_for<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies what to evaluate from the output of the command and what conditionals to apply.  This argument will cause the task to wait for a particular conditional to be true before moving forward.  If the conditional is not true by the configured <em>retries</em>, the task fails. See examples.</div></br>
    <div style="font-size: small;">aliases: waitfor<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    tasks:
      - name: show configuration on ethernet devices eth0 and eth1
        vyos_command:
          commands:
            - show interfaces ethernet {{ item }}
        with_items:
          - eth0
          - eth1
    
      - name: run multiple commands and check if version output contains specific version string
        vyos_command:
          commands:
            - show version
            - show hardware cpu
          wait_for:
            - "result[0] contains 'VyOS 1.1.7'"

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
        <td align=center> always apart from low level errors (such as action plugin) </td>
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

.. note::
    - Running ``show system boot-messages all`` will cause the module to hang since VyOS is using a custom pager setting to display the output of that command.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
