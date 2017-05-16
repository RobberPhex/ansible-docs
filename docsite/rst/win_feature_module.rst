.. _win_feature:


win_feature - Installs and uninstalls Windows Features
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.7

Installs or uninstalls Windows Roles or Features

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
    <td>include_management_tools</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>Adds the corresponding management tools to the specified feature</td>
    </tr>
            <tr>
    <td>include_sub_features</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>Adds all subfeatures of the specified feature</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Names of roles or features to install as a single feature or a comma-separated list of features</td>
    </tr>
            <tr>
    <td>restart</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>Restarts the computer automatically when installation is complete, if restarting is required by the roles or features installed.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>State of the features or roles on the system</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # This installs IIS.
    # The names of features available for install can be run by running the following Powershell Command:
    # PS C:\Users\Administrator> Import-Module ServerManager; Get-WindowsFeature
    $ ansible -i hosts -m win_feature -a "name=Web-Server" all
    $ ansible -i hosts -m win_feature -a "name=Web-Server,Web-Common-Http" all
    
    
    # Playbook example
    ---
    - name: Install IIS
      hosts: all
      gather_facts: false
      tasks:
        - name: Install IIS
          win_feature:
            name: "Web-Server"
            state: absent
            restart: yes
            include_sub_features: yes
            include_management_tools: yes
    
    



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

