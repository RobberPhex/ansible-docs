.. _win_msi:


win_msi - Installs and uninstalls Windows MSI files
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Installs or uninstalls a Windows MSI file that is already located on the target server




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
    <td>creates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to a file created by installing the MSI to prevent from attempting to reinstall the package on every run</div></td></tr>
            <tr>
    <td>extra_args<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Additional arguments to pass to the msiexec.exe command</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File system path to the MSI file to install</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the MSI file should be installed or uninstalled</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>True</li><li>False</li><li>False</li></ul></td>
        <td><div>Specify whether to wait for install or uninstall to complete before continuing.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install an MSI file
    - win_msi: path=C:\\7z920-x64.msi
    
    # Install an MSI, and wait for it to complete before continuing
    - win_msi: path=C:\\7z920-x64.msi wait=true
    
    # Uninstall an MSI file
    - win_msi: path=C:\\7z920-x64.msi state=absent




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

