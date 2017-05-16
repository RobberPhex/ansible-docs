.. _win_feature:


win_feature - Installs and uninstalls Windows Features on Windows Server
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Installs or uninstalls Windows Roles or Features on Windows Server. This module uses the Add/Remove-WindowsFeature Cmdlets, which is not available on client os machines.




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
    <td>include_management_tools<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Adds the corresponding management tools to the specified feature</div></td></tr>
            <tr>
    <td>include_sub_features<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Adds all subfeatures of the specified feature</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Names of roles or features to install as a single feature or a comma-separated list of features</div></td></tr>
            <tr>
    <td>restart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Restarts the computer automatically when installation is complete, if restarting is required by the roles or features installed.</div></td></tr>
            <tr>
    <td>source<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li> {driveletter}:\sources\sxs</li><li> {IP}\Share\sources\sxs</li></ul></td>
        <td><div>Specify a source to install the feature from</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the features or roles on the system</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # This installs IIS.
    # The names of features available for install can be run by running the following Powershell Command:
    # PS C:\Users\Administrator> Import-Module ServerManager; Get-WindowsFeature
    $ ansible -i hosts -m win_feature -a "name=Web-Server" all
    $ ansible -i hosts -m win_feature -a "name=Web-Server,Web-Common-Http" all
    ansible -m "win_feature" -a "name=NET-Framework-Core source=C:/Temp/iso/sources/sxs" windows
    
    
    # Playbook example
    ---
    - name: Install IIS
      hosts: all
      gather_facts: false
      tasks:
        - name: Install IIS
          win_feature:
            name: "Web-Server"
            state: present
            restart: yes
            include_sub_features: yes
            include_management_tools: yes




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

