.. _include_vars:


include_vars - Load variables from files, dynamically within a task.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Loads variables from a YAML file dynamically during task runtime.  It can work with conditionals, or use host specific variables to determine the path name to load from.

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
    <td>free-form</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The file name from which variables should be loaded, if called from a role it will look for the file in vars/ subdirectory of the role, otherwise the path would be relative to playbook. An absolute path can also be provided.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Conditionally decide to load in variables when x is 0, otherwise do not.
    - include_vars: contingency_plan.yml
      when: x == 0
    
    # Load a variable file based on the OS type, or a default if not found.
    - include_vars: "{{ item }}"
      with_first_found:
       - "{{ ansible_distribution }}.yml"
       - "{{ ansible_os_family }}.yml"
       - "default.yml"
    



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

