.. _ce_command:


ce_command - Run arbitrary command on HUAWEI CloudEngine devices
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Sends an arbitrary command to an HUAWEI CloudEngine node and returns the results read from the device.  The ce_command module includes an argument that will cause the module to wait for a specific condition before returning or timing out if the condition is not met.




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
        <td><div>The commands to send to the remote HUAWEI CloudEngine device over the configured provider.  The resulting output from the command is returned. If the <em>wait_for</em> argument is provided, the module is not returned until the condition is satisfied or the number of <em>retries</em> has been exceeded.</div>        </td></tr>
                <tr><td>interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Configures the interval in seconds to wait between retries of the command.  If the command does not pass the specified conditional, the interval indicates how to long to wait before trying the command again.</div>        </td></tr>
                <tr><td>match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td></td>
        <td><div>The <em>match</em> argument is used in conjunction with the <em>wait_for</em> argument to specify the match policy.  Valid values are <code>all</code> or <code>any</code>.  If the value is set to <code>all</code> then all conditionals in the <em>wait_for</em> must be satisfied.  If the value is set to <code>any</code> then only one of the values must be satisfied.</div>        </td></tr>
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
                <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate the CLI login. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                    <tr><td>host<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                    <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                    <tr><td>password<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for cli transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                    <tr><td>port<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>0 (use common port)</td>
                <td></td>
                <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>netconf</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, netconf=22).</div>        </td></tr>
                    <tr><td>transport<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td>cli</td>
                <td></td>
                <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh).</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the number of retries a command should by tried before it is considered failed.  The command is run on the target device every retry and evaluated against the <em>wait_for</em> conditionals.</div>        </td></tr>
                <tr><td>wait_for<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies what to evaluate from the output of the command and what conditionals to apply.  This argument will cause the task to wait for a particular conditional to be true before moving forward.   If the conditional is not true by the configured retries, the task fails.  See examples.</div></br>
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
        username: admin
        password: admin
        transport: cli
    
    ---
    - name: run display version on remote devices
      ce_command:
        commands: display version
        provider: "{{ cli }}"
    
    - name: run display version and check to see if output contains HUAWEI
      ce_command:
        commands: display version
        wait_for: result[0] contains HUAWEI
        provider: "{{ cli }}"
    
    - name: run multiple commands on remote nodes
      ce_command:
        commands:
          - display version
          - display device
        provider: "{{ cli }}"
    
    - name: run multiple commands and evaluate the output
      ce_command:
        commands:
          - display version
          - display device
        wait_for:
          - result[0] contains HUAWEI
          - result[1] contains Device
        provider: "{{ cli }}"
    
    - name: run commands and specify the output format
      ce_command:
        commands:
          - command: display version
            output: json
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




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
