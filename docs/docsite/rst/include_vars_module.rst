.. _include_vars:


include_vars - Load variables from files, dynamically within a task.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Loads variables from a YAML/JSON files dynamically from within a file or from a directory recursively during task runtime. If loading a directory, the files are sorted alphabetically before being loaded.




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
                <tr><td>depth<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When using <code>dir</code>, this module will, by default, recursively go through each sub directory and load up the variables. By explicitly setting the depth, this module will only go as deep as the depth.</div>        </td></tr>
                <tr><td>dir<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The directory name from which the variables should be loaded.</div><div>If the path is relative, it will look for the file in vars/ subdirectory of a role or relative to playbook.</div>        </td></tr>
                <tr><td>extensions<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>[u'yaml', u'yml', u'json']</td>
        <td></td>
        <td><div>List of file extensions to read when using <code>dir</code>.</div>        </td></tr>
                <tr><td>file<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The file name from which variables should be loaded.</div><div>If the path is relative, it will look for the file in vars/ subdirectory of a role or relative to playbook.</div>        </td></tr>
                <tr><td>files_matching<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Limit the files that are loaded within any directory to this regular expression.</div>        </td></tr>
                <tr><td>free-form<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This module allows you to specify the 'file' option directly w/o any other options. There is no 'free-form' option, this is just an indicator, see example below.</div>        </td></tr>
                <tr><td>ignore_files<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of file names to ignore.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of a variable into which assign the included vars, if omitted (null) they will be made top level vars.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Include vars of stuff.yml into the 'stuff' variable (2.2).
      include_vars:
        file: stuff.yml
        name: stuff
    
    - name: Conditionally decide to load in variables into 'plans' when x is 0, otherwise do not. (2.2)
      include_vars:
        file: contingency_plan.yml
        name: plans
      when: x == 0
    
    - name: Load a variable file based on the OS type, or a default if not found. Using free-form to specify the file.
      include_vars: "{{ item }}"
      with_first_found:
        - "{{ ansible_distribution }}.yml"
        - "{{ ansible_os_family }}.yml"
        - "default.yml"
    
    - name: bare include (free-form)
      include_vars: myvars.yml
    
    - name: Include all .json and .jsn files in vars/all and all nested directories (2.3)
      include_vars:
        dir: 'vars/all'
        extensions:
            - json
            - jsn
    
    - name: Include all default extension files in vars/all and all nested directories and save the output in test. (2.2)
      include_vars:
        dir: 'vars/all'
        name: test
    
    - name: Include default extension files in vars/services (2.2)
      include_vars:
        dir: 'vars/services'
        depth: 1
    
    - name: Include only files matching bastion.yml (2.2)
      include_vars:
        dir: 'vars'
        files_matching: 'bastion.yml'
    
    - name: Include all .yml files except bastion.yml (2.3)
      include_vars:
        dir: 'vars'
        ignore_files: 'bastion.yml'
        extensions: ['yml']





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
