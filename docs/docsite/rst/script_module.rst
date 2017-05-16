.. _script:


script - Runs a local script on a remote node after transferring it
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``script`` module takes the script name followed by a list of space-delimited arguments. 
* The local script at path will be transferred to the remote node and then executed. 
* The given script will be processed through the shell environment on the remote node. 
* This module does not require python on the remote system, much like the :ref:`raw <raw>` module. 




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
                <tr><td>creates<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a filename, when it already exists, this step will <b>not</b> be run.</div>        </td></tr>
                <tr><td>free_form<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>path to the local script file followed by optional arguments. There is no parameter actually named 'free form'; see the examples!</div>        </td></tr>
                <tr><td>removes<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a filename, when it does not exist, this step will <b>not</b> be run.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example from Ansible Playbooks
    - script: /some/local/script.sh --some-arguments 1234
    
    # Run a script that creates a file, but only if the file is not yet created
    - script: /some/local/create_file.sh --some-arguments 1234
      args:
        creates: /the/created/file.txt
    
    # Run a script that removes a file, but only if the file is not yet removed
    - script: /some/local/remove_file.sh --some-arguments 1234
      args:
        removes: /the/removed/file.txt


Notes
-----

.. note::
    - It is usually preferable to write Ansible modules than pushing scripts. Convert your script to an Ansible module for bonus points!
    - The ssh connection plugin will force psuedo-tty allocation via -tt when scripts are executed. psuedo-ttys do not have a stderr channel and all stderr is sent to stdout. If you depend on separated stdout and stderr result keys, please switch to a copy+command set of tasks instead of using script.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
