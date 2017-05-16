.. _win_package:


win_package - Installs/Uninstalls a installable package, either from local file system or url
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Installs or uninstalls a package




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
    <td>arguments<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Any arguments the installer needs</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the package. Just for logging reasons, will use the value of path if name isn't specified</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Location of the package to be installed (either on file system, network share or url)</div></td></tr>
            <tr>
    <td>product_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>product id of the installed package (used for checking if already installed)</div></br>
        <div style="font-size: small;">aliases: productid<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Install or Uninstall</div></br>
        <div style="font-size: small;">aliases: ensure<div></td></tr>
            <tr>
    <td>user_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username of an account with access to the package if its located on a file share. Only needed if the winrm user doesn't have access to the package. Also specify user_password for this to function properly.</div></td></tr>
            <tr>
    <td>user_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password of an account with access to the package if its located on a file share. Only needed if the winrm user doesn't have access to the package. Also specify user_name for this to function properly.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Playbook example
      - name: Install the vc thingy
        win_package:
          name="Microsoft Visual C thingy"
          path="http://download.microsoft.com/download/1/6/B/16B06F60-3B20-4FF2-B699-5E9B7962F9AE/VSU_4/vcredist_x64.exe"
          Product_Id="{CF2BEA3C-26EA-32F8-AA9B-331F7E34BA97}"
          Arguments="/install /passive /norestart"
    
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

