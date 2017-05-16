.. _win_shell:


win_shell - Execute shell commands on target hosts.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``win_shell`` module takes the command name followed by a list of space-delimited arguments. It is similar to the :ref:`win_command <win_command>` module, but runs the command via a shell (defaults to PowerShell) on the target host.




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
                <tr><td>chdir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>set the specified path as the current working directory before executing a command</div>        </td></tr>
                <tr><td>creates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a path or path filter pattern; when the referenced path exists on the target host, the task will be skipped.</div>        </td></tr>
                <tr><td>executable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>change the shell used to execute the command (eg, <code>cmd</code>). The target shell must accept a <code>/c</code> parameter followed by the raw command line to be executed.</div>        </td></tr>
                <tr><td>free_form<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the win_shell module takes a free form command to run.  There is no parameter actually named 'free form'. See the examples!</div>        </td></tr>
                <tr><td>removes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a path or path filter pattern; when the referenced path <b>does not</b> exist on the target host, the task will be skipped.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Execute a command in the remote shell; stdout goes to the specified
    # file on the remote.
    - win_shell: C:\somescript.ps1 >> c:\somelog.txt
    
    # Change the working directory to somedir/ before executing the command.
    - win_shell: C:\somescript.ps1 >> c:\somelog.txt chdir=c:\somedir
    
    # You can also use the 'args' form to provide the options. This command
    # will change the working directory to somedir/ and will only run when
    # somedir/somelog.txt doesn't exist.
    - win_shell: C:\somescript.ps1 >> c:\somelog.txt
      args:
        chdir: c:\somedir
        creates: c:\somelog.txt
    
    # Run a command under a non-Powershell interpreter (cmd in this case)
    - win_shell: echo %HOMEDIR%
      args:
        executable: cmd
      register: homedir_out

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
        <td> end </td>
        <td> The command execution end time </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2016-02-25 09:18:26.755339 </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The command standard output </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> Clustering node rabbit@slave1 with rabbit@master ... </td>
    </tr>
            <tr>
        <td> cmd </td>
        <td> The command executed by the task </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> rabbitmqctl join_cluster rabbit@master </td>
    </tr>
            <tr>
        <td> start </td>
        <td> The command execution start time </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2016-02-25 09:18:26.429568 </td>
    </tr>
            <tr>
        <td> delta </td>
        <td> The command execution delta time </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 0:00:00.325771 </td>
    </tr>
            <tr>
        <td> stderr </td>
        <td> The command standard error </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> ls: cannot access foo: No such file or directory </td>
    </tr>
            <tr>
        <td> rc </td>
        <td> The command return code (0 means success) </td>
        <td align=center> always </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
    </tr>
            <tr>
        <td> msg </td>
        <td> changed </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> stdout_lines </td>
        <td> The command standard output split in lines </td>
        <td align=center> always </td>
        <td align=center> list of strings </td>
        <td align=center> ["u'Clustering node rabbit@slave1 with rabbit@master ...'"] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - If you want to run an executable securely and predictably, it may be better to use the :ref:`win_command <win_command>` module instead. Best practices when writing playbooks will follow the trend of using :ref:`win_command <win_command>` unless ``win_shell`` is explicitly required. When running ad-hoc commands, use your best judgement.
    - WinRM will not return from a command execution until all child processes created have exited. Thus, it is not possible to use win_shell to spawn long-running child or background processes. Consider creating a Windows service for managing background processes.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
