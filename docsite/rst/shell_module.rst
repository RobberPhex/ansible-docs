.. _shell:


shell - Execute commands in nodes.
++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`shell <shell>` module takes the command name followed by a list of space-delimited arguments. It is almost exactly like the :ref:`command <command>` module but runs the command through a shell (``/bin/sh``) on the remote node.




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
        <td><div>cd into this directory before running the command</div></td></tr>
            <tr>
    <td>creates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a filename, when it already exists, this step will <b>not</b> be run.</div></td></tr>
            <tr>
    <td>executable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>change the shell used to execute the command. Should be an absolute path to the executable.</div></td></tr>
            <tr>
    <td>free_form<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The shell module takes a free form command to run, as a string.  There's not an actual option named "free form".  See the examples!</div></td></tr>
            <tr>
    <td>removes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a filename, when it does not exist, this step will <b>not</b> be run.</div></td></tr>
            <tr>
    <td>warn<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>if command warnings are on in ansible.cfg, do not warn about this particular line if set to no/false.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Execute the command in remote shell; stdout goes to the specified
    # file on the remote.
    - shell: somescript.sh >> somelog.txt
    
    # Change the working directory to somedir/ before executing the command.
    - shell: somescript.sh >> somelog.txt chdir=somedir/
    
    # You can also use the 'args' form to provide the options. This command
    # will change the working directory to somedir/ and will only run when
    # somedir/somelog.txt doesn't exist.
    - shell: somescript.sh >> somelog.txt
      args:
        chdir: somedir/
        creates: somelog.txt
    
    # Run a command that uses non-posix shell-isms (in this example /bin/sh
    # doesn't handle redirection and wildcards together but bash does)
    - shell: cat < /tmp/*txt
      args:
        executable: /bin/bash

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

.. note:: If you want to execute a command securely and predictably, it may be better to use the :ref:`command <command>` module instead. Best practices when writing playbooks will follow the trend of using :ref:`command <command>` unless :ref:`shell <shell>` is explicitly required. When running ad-hoc commands, use your best judgement.
.. note:: To sanitize any variables passed to the shell module, you should use "{{ var | quote }}" instead of just "{{ var }}" to make sure they don't include evil things like semicolons.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

