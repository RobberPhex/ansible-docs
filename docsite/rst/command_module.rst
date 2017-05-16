.. _command:


command - Executes a command on a remote node
+++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`command <command>` module takes the command name followed by a list of space-delimited arguments.
The given command will be executed on all selected nodes. It will not be processed through the shell, so variables like ``$HOME`` and operations like ``"<"``, ``">"``, ``"|"``, ``";"`` and ``"&"`` will not work (use the :ref:`shell <shell>` module if you need these features).




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
        <td><div>a filename or (since 2.0) glob pattern, when it already exists, this step will <b>not</b> be run.</div></td></tr>
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
        <td><div>the command module takes a free form command to run.  There is no parameter actually named 'free form'. See the examples!</div></td></tr>
            <tr>
    <td>removes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a filename or (since 2.0) glob pattern, when it does not exist, this step will <b>not</b> be run.</div></td></tr>
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

    # Example from Ansible Playbooks.
    - command: /sbin/shutdown -t now
    
    # Run the command if the specified file does not exist.
    - command: /usr/bin/make_database.sh arg1 arg2 creates=/path/to/database
    
    # You can also use the 'args' form to provide the options. This command
    # will change the working directory to somedir/ and will only run when
    # /path/to/database doesn't exist.
    - command: /usr/bin/make_database.sh arg1 arg2
      args:
        chdir: somedir/
        creates: /path/to/database


Notes
-----

.. note:: If you want to run a command through the shell (say you are using ``<``, ``>``, ``|``, etc), you actually want the :ref:`shell <shell>` module instead. The :ref:`command <command>` module is much more secure as it's not affected by the user's environment.
.. note::  ``creates``, ``removes``, and ``chdir`` can be specified after the command. For instance, if you only want to run a command if a certain file does not exist, use this.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

