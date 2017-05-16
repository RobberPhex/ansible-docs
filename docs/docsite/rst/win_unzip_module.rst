.. _win_unzip:


win_unzip - Unzips compressed files and archives on the Windows node
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Unzips compressed files and archives.
* Supports .zip files natively
* Supports other formats supported by the Powershell Community Extensions (PSCX) module (basically everything 7zip supports)


Requirements (on host that executes module)
-------------------------------------------

  * PSCX


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
                <tr><td>creates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If this file or directory exists the specified src will not be extracted.</div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Destination of zip file (provide absolute path of directory). If it does not exist, the directory will be created.</div>        </td></tr>
                <tr><td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li><li>True</li><li>False</li></ul></td>
        <td><div>Recursively expand zipped files within the src file.</div>        </td></tr>
                <tr><td>rm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li><li>True</li><li>False</li></ul></td>
        <td><div>Remove the zip file, after unzipping</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>File to be unzipped (provide absolute path)</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # This unzips a library that was downloaded with win_get_url, and removes the file after extraction
    # $ ansible -i hosts -m win_unzip -a "src=C:\\LibraryToUnzip.zip dest=C:\\Lib rm=true" all
    # Playbook example
    
    # Simple unzip
    ---
    - name: Unzip a bz2 (BZip) file
      win_unzip:
        src: C:\Users\Phil\Logs.bz2
        dest: C:\Users\Phil\OldLogs
        creates: C:\Users\Phil\OldLogs
    
    # This playbook example unzips a .zip file and recursively decompresses the contained .gz files and removes all unneeded compressed files after completion.
    - name: Unzip ApplicationLogs.zip and decompress all GZipped log files
      hosts: all
      gather_facts: false
      tasks:
        - name: Recursively decompress GZ files in ApplicationLogs.zip
          win_unzip:
            src: C:\Downloads\ApplicationLogs.zip
            dest: C:\Application\Logs
            recurse: yes
            rm: true
    
    # Install PSCX to use for extracting a gz file
    - name: Grab PSCX msi
      win_get_url:
        url: http://download-codeplex.sec.s-msft.com/Download/Release?ProjectName=pscx&DownloadId=923562&FileTime=130585918034470000&Build=20959
        dest: C:\pscx.msi
    - name: Install PSCX
      win_msi:
        path: C:\pscx.msi
    - name: Unzip gz log
      win_unzip:
        src: C:\Logs\application-error-logs.gz
        dest: C:\ExtractedLogs\application-error-logs


Notes
-----

.. note::
    - For extracting any compression types other than .zip, the PowerShellCommunityExtensions (PSCX) Module is required.  This module (in conjunction with PSCX) has the ability to recursively unzip files within the src zip file provided and also functionality for many other compression types. If the destination directory does not exist, it will be created before unzipping the file.  Specifying rm parameter will force removal of the src file after extraction.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
