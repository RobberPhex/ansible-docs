.. _include_vars:


include_vars - Load variables from files, dynamically within a task.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Loads variables from a YAML/JSON file dynamically during task runtime.  It can work with conditionals, or use host specific variables to determine the path name to load from.




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
    <td>free-form<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The file name from which variables should be loaded, if called from a role it will look for the file in vars/ subdirectory of the role, otherwise the path would be relative to playbook. An absolute path can also be provided.</div></td></tr>
        </table>
    </br>



Examples
--------

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

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

