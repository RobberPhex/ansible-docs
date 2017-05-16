.. _win_package:


win_package - Installs/Uninstalls an installable package, either from local file system or url
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Installs or uninstalls a package.
* Optionally uses a product_id to check if the package needs installing. You can find product ids for installed programs in the windows registry either in ``HKLM:Software\Microsoft\Windows\CurrentVersion\Uninstall`` or for 32 bit programs ``HKLM:Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall``




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
                <tr><td>arguments<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Any arguments the installer needs</div>        </td></tr>
                <tr><td>expected_return_code<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>One or more return codes from the package installation that indicates success.</div><div>If not provided, defaults to 0</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the package, if name isn't specified the path will be used for log messages</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Location of the package to be installed (either on file system, network share or url)</div>        </td></tr>
                <tr><td>product_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Product id of the installed package (used for checking if already installed)</div><div>You can find product ids for installed programs in the windows registry either in <code>HKLM:Software\Microsoft\Windows\CurrentVersion\Uninstall</code> or for 32 bit programs <code>HKLM:Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall</code>'</div></br>
    <div style="font-size: small;">aliases: productid<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Install or Uninstall</div></br>
    <div style="font-size: small;">aliases: ensure<div>        </td></tr>
                <tr><td>user_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username of an account with access to the package if it's located on a file share. Only needed if the winrm user doesn't have access to the package. Also specify user_password for this to function properly.</div>        </td></tr>
                <tr><td>user_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of an account with access to the package if it's located on a file share. Only needed if the winrm user doesn't have access to the package. Also specify user_name for this to function properly.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Install the Visual C thingy
      win_package:
        name: Microsoft Visual C thingy
        path: http://download.microsoft.com/download/1/6/B/16B06F60-3B20-4FF2-B699-5E9B7962F9AE/VSU_4/vcredist_x64.exe
        product_id: '{CF2BEA3C-26EA-32F8-AA9B-331F7E34BA97}'
        arguments: /install /passive /norestart
    
    - name: Install Remote Desktop Connection Manager from msi
      win_package:
        path: https://download.microsoft.com/download/A/F/0/AF0071F3-B198-4A35-AA90-C68D103BDCCF/rdcman.msi
        product_id: '{0240359E-6A4C-4884-9E94-B397A02D893C}'
    
    - name: Uninstall Remote Desktop Connection Manager installed from msi
      win_package:
        path: https://download.microsoft.com/download/A/F/0/AF0071F3-B198-4A35-AA90-C68D103BDCCF/rdcman.msi
        product_id: '{0240359E-6A4C-4884-9E94-B397A02D893C}'
        state: absent
    
    # Specify the expected non-zero return code when successful
    # In this case 3010 indicates 'reboot required'
    - name: 'Microsoft .NET Framework 4.5.1'
      win_package:
        path: https://download.microsoft.com/download/1/6/7/167F0D79-9317-48AE-AEDB-17120579F8E2/NDP451-KB2858728-x86-x64-AllOS-ENU.exe
        productid: '{7DEBE4EB-6B40-3766-BB35-5CBBC385DA37}'
        arguments: '/q /norestart'
        ensure: present
        expected_return_code: 3010
    
    # Specify multiple non-zero return codes when successful
    # In this case we can say that both 0 (SUCCESSFUL) and 3010 (REBOOT REQUIRED) codes are acceptable
    - name: 'Microsoft .NET Framework 4.5.1'
      win_package:
        path: https://download.microsoft.com/download/1/6/7/167F0D79-9317-48AE-AEDB-17120579F8E2/NDP451-KB2858728-x86-x64-AllOS-ENU.exe
        productid: '{7DEBE4EB-6B40-3766-BB35-5CBBC385DA37}'
        arguments: '/q /norestart'
        ensure: present
        expected_return_code: [0,3010]





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
