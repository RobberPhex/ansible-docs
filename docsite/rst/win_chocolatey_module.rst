.. _win_chocolatey:


win_chocolatey - Installs packages using chocolatey
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Installs packages using Chocolatey (http://chocolatey.org/). If Chocolatey is missing from the system, the module will install it. List of packages can be found at http://chocolatey.org/packages




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
    <td>allow_empty_checksums<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Allow empty Checksums to be used</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Forces install of the package (even if it already exists). Using Force will cause ansible to always report that a change was made</div></td></tr>
            <tr>
    <td>ignore_checksums<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Ignore Checksums</div></td></tr>
            <tr>
    <td>ignore_dependencies<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Ignore dependencies, only install/upgrade the package itself</div></td></tr>
            <tr>
    <td>install_args<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Arguments to pass to the native installer</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the package to be installed</div></td></tr>
            <tr>
    <td>params<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Parameters to pass to the package</div></td></tr>
            <tr>
    <td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify source rather than using default chocolatey repository</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the package on the system</div></td></tr>
            <tr>
    <td>upgrade<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If package is already installed it, try to upgrade to the latest version or to the specified version</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specific version of the package to be installed</div><div>Ignored when state == 'absent'</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Install git
      win_chocolatey:
        name: git
    
      # Install notepadplusplus version 6.6
      win_chocolatey:
        name: notepadplusplus.install
        version: 6.6
    
      # Uninstall git
      win_chocolatey:
        name: git
        state: absent
    
      # Install git from specified repository
      win_chocolatey:
        name: git
        source: https://someserver/api/v2/




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

