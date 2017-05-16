.. _command:


command - Executes a command on a remote node
+++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


The ``command`` module takes the command name followed by a list of space-delimited arguments.
The given command will be executed on all selected nodes. It will not be processed through the shell, so variables like ``$HOME`` and operations like ``"<"``, ``">"``, ``"|"``, and ``"&"`` will not work (use the ``shell`` module if you need these features).

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
    <td>chdir</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>cd into this directory before running the command (added in Ansible 0.6)</td>
    </tr>
            <tr>
    <td>creates</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a filename, when it already exists, this step will <b>not</b> be run.</td>
    </tr>
            <tr>
    <td>executable</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>change the shell used to execute the command. Should be an absolute path to the executable. (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>free_form</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the command module takes a free form command to run.  There is no parameter actually named 'free form'. See the examples!</td>
    </tr>
            <tr>
    <td>removes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a filename, when it does not exist, this step will <b>not</b> be run. (added in Ansible 0.8)</td>
    </tr>
            <tr>
    <td>warn</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>if command warnings are on in ansible.cfg, do not warn about this particular line if set to no/false. (added in Ansible 1.8)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


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

.. note:: If you want to run a command through the shell (say you are using ``<``, ``>``, ``|``, etc), you actually want the ``shell`` module instead. The ``command`` module is much more secure as it's not affected by the user's environment.
.. note::  ``creates``, ``removes``, and ``chdir`` can be specified after the command. For instance, if you only want to run a command if a certain file does not exist, use this.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

