.. _win_feature:


win_feature - Installs and uninstalls Windows Features on Windows Server
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Installs or uninstalls Windows Roles or Features on Windows Server. This module uses the Add/Remove-WindowsFeature Cmdlets on Windows 2008 and Install/Uninstall-WindowsFeature Cmdlets on Windows 2012, which are not available on client os machines.




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
                <tr><td>include_management_tools<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Adds the corresponding management tools to the specified feature.</div><div>Not supported in Windows 2008. If present when using Windows 2008 this option will be ignored.</div>        </td></tr>
                <tr><td>include_sub_features<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Adds all subfeatures of the specified feature</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Names of roles or features to install as a single feature or a comma-separated list of features</div>        </td></tr>
                <tr><td>restart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Restarts the computer automatically when installation is complete, if restarting is required by the roles or features installed.</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li> {driveletter}:\sources\sxs</li><li> {IP}\Share\sources\sxs</li></ul></td>
        <td><div>Specify a source to install the feature from.</div><div>Not supported in Windows 2008. If present when using Windows 2008 this option will be ignored.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the features or roles on the system</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Install IIS (Web-Server only)
      win_feature:
        name: Web-Server
        state: present
    
    - name: Install IIS (Web-Server and Web-Common-Http)
      win_feature:
        name: Web-Server,Web-Common-Http
        state: present
    
    - name: Install NET-Framework-Core from file
      win_feature:
        name: NET-Framework-Core
        source: C:\Temp\iso\sources\sxs
        state: present
    
    - name: Install IIS Web-Server with sub features and management tools
      win_feature:
        name: Web-Server
        state: present
        restart: True
        include_sub_features: True
        include_management_tools: True





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
