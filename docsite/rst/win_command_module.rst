.. _win_command:


win_command - Executes a command on a remote Windows node
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`win_command <win_command>` module takes the command name followed by a list of space-delimited arguments.
The given command will be executed on all selected nodes. It will not be processed through the shell, so variables like ``$env:HOME`` and operations like ``"<"``, ``">"``, ``"|"``, and ``";"`` will not work (use the :ref:`win_shell <win_shell>` module if you need these features).




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
    <td>chdir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>set the specified path as the current working directory before executing a command</div></td></tr>
            <tr>
    <td>creates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a path or path filter pattern; when the referenced path exists on the target host, the task will be skipped.</div></td></tr>
            <tr>
    <td>free_form<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the win_command module takes a free form command to run.  There is no parameter actually named 'free form'. See the examples!</div></td></tr>
            <tr>
    <td>removes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a path or path filter pattern; when the referenced path <b>does not</b> exist on the target host, the task will be skipped.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example from Ansible Playbooks.
    - win_command: whoami
      register: whoami_out
    
    # Run the command only if the specified file does not exist.
    - win_command: wbadmin -backupTarget:c:\backup\ creates=c:\backup\
    
    # You can also use the 'args' form to provide the options. This command
    # will change the working directory to c:\somedir\ and will only run when
    # c:\backup\ doesn't exist.
    - win_command: wbadmin -backupTarget:c:\backup\ creates=c:\backup\
      args:
        chdir: c:\somedir\
        creates: c:\backup\

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

.. note:: If you want to run a command through a shell (say you are using ``<``, ``>``, ``|``, etc), you actually want the :ref:`win_shell <win_shell>` module instead. The :ref:`win_command <win_command>` module is much more secure as it's not affected by the user's environment.
.. note::  ``creates``, ``removes``, and ``chdir`` can be specified after the command. For instance, if you only want to run a command if a certain file does not exist, use this.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

