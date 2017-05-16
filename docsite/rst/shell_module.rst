.. _shell:


shell - Execute commands in nodes.
++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


The ``shell`` module takes the command name followed by a list of space-delimited arguments. It is almost exactly like the ``command`` module but runs the command through a shell (``/bin/sh``) on the remote node.

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
        <td>The shell module takes a free form command to run, as a string.  There's not an actual option named "free form".  See the examples!</td>
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

.. note:: If you want to execute a command securely and predictably, it may be better to use the ``command`` module instead. Best practices when writing playbooks will follow the trend of using ``command`` unless ``shell`` is explicitly required. When running ad-hoc commands, use your best judgement.
.. note:: To sanitize any variables passed to the shell module, you should use "{{ var | quote }}" instead of just "{{ var }}" to make sure they don't include evil things like semicolons.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

