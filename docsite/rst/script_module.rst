.. _script:


script - Runs a local script on a remote node after transferring it
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


The ``script`` module takes the script name followed by a list of space-delimited arguments. 
The local script at path will be transferred to the remote node and then executed. 
The given script will be processed through the shell environment on the remote node. 
This module does not require python on the remote system, much like the ``raw`` module. 

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
    <td>creates</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a filename, when it already exists, this step will <b>not</b> be run. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>free_form</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to the local script file followed by optional arguments.</td>
    </tr>
            <tr>
    <td>removes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a filename, when it does not exist, this step will <b>not</b> be run. (added in Ansible 1.5)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example from Ansible Playbooks
    - script: /some/local/script.sh --some-arguments 1234
    
    # Run a script that creates a file, but only if the file is not yet created
    - script: /some/local/create_file.sh --some-arguments 1234 creates=/the/created/file.txt
    
    # Run a script that removes a file, but only if the file is not yet removed
    - script: /some/local/remove_file.sh --some-arguments 1234 removes=/the/removed/file.txt

.. note:: It is usually preferable to write Ansible modules than pushing scripts. Convert your script to an Ansible module for bonus points!


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

