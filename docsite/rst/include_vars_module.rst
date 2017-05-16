.. _include_vars:


include_vars - Load variables from files, dynamically within a task.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Loads variables from a YAML/JSON files dynamically from within a file or from a directory recursively during task runtime. If loading a directory, the files are sorted alphabetically before being loaded.




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
    <td>depth<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>By default, this module will recursively go through each sub directory and load up the variables. By explicitly setting the depth, this module will only go as deep as the depth.</div></td></tr>
            <tr>
    <td>dir<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The directory name from which the variables should be loaded.</div><div>If the path is relative, it will look for the file in vars/ subdirectory of a role or relative to playbook.</div></td></tr>
            <tr>
    <td>file<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The file name from which variables should be loaded.</div><div>If the path is relative, it will look for the file in vars/ subdirectory of a role or relative to playbook.</div></td></tr>
            <tr>
    <td>files_matching<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Limit the variables that are loaded within any directory to this regular expression.</div></td></tr>
            <tr>
    <td>free-form<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>This module allows you to specify the 'file' option directly w/o any other options.</div></td></tr>
            <tr>
    <td>ignore_files<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of file names to ignore. The defaults can not be overridden, but can be extended.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of a variable into which assign the included vars, if omitted (null) they will be made top level vars.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Include vars of stuff.yml into the 'stuff' variable (2.2).
    - include_vars:
        file: stuff.yml
        name: stuff
    
    # Conditionally decide to load in variables into 'plans' when x is 0, otherwise do not. (2.2)
    - include_vars: file=contingency_plan.yml name=plans
      when: x == 0
    
    # Load a variable file based on the OS type, or a default if not found.
    - include_vars: "{{ item }}"
      with_first_found:
       - "{{ ansible_distribution }}.yml"
       - "{{ ansible_os_family }}.yml"
       - "default.yml"
    
    # bare include (free-form)
    - include_vars: myvars.yml
    
    # Include all yml files in vars/all and all nested directories
    - include_vars:
        dir: 'vars/all'
    
    # Include all yml files in vars/all and all nested directories and save the output in test.
    - include_vars:
        dir: 'vars/all'
        name: test
    
    # Include all yml files in vars/services
    - include_vars:
        dir: 'vars/services'
        depth: 1
    
    # Include only bastion.yml files
    - include_vars:
        dir: 'vars'
        files_matching: 'bastion.yml'
    
    # Include only all yml files exception bastion.yml
    - include_vars:
        dir: 'vars'
        ignore_files: 'bastion.yml'




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

