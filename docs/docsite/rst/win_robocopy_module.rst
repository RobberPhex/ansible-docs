.. _win_robocopy:


win_robocopy - Synchronizes the contents of two directories using Robocopy.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Synchronizes the contents of two directories on the remote machine. Under the hood this just calls out to RoboCopy, since that should be available on most modern Windows Systems.




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
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Destination file/directory to sync (Will receive contents of src).</div>        </td></tr>
                <tr><td>flags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Directly supply Robocopy flags. If set, purge and recurse will be ignored.</div>        </td></tr>
                <tr><td>purge<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Deletes any files/directories found in the destination that do not exist in the source (Toggles the `/purge` flag to RoboCopy). If "flags" is set, this will be ignored.</div>        </td></tr>
                <tr><td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Includes all subdirectories (Toggles the `/e` flag to RoboCopy). If "flags" is set, this will be ignored.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Source file/directory to sync.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Sync the contents of one directory to another
      win_robocopy:
        src: C:\DirectoryOne
        dest: C:\DirectoryTwo
    
    - name: Sync the contents of one directory to another, including subdirectories
      win_robocopy:
        src: C:\DirectoryOne
        dest: C:\DirectoryTwo
        recurse: True
    
    - name: Sync the contents of one directory to another, and remove any files/directories found in destination that do not exist in the source
      win_robocopy:
        src: C:\DirectoryOne
        dest: C:\DirectoryTwo
        purge: True
    
    - name: Sync content in recursive mode, removing any files/directories found in destination that do not exist in the source
      win_robocopy:
        src: C:\DirectoryOne
        dest: C:\DirectoryTwo
        recurse: True
        purge: True
    
    - name: Sync Two Directories in recursive and purging mode, specifying additional special flags
      win_robocopy:
        src: C:\DirectoryOne
        dest: C:\DirectoryTwo
        flags: /E /PURGE /XD SOME_DIR /XF SOME_FILE /MT:32

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> src </td>
        <td> The Source file/directory of the sync. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> c:\Some\Path </td>
    </tr>
            <tr>
        <td> dest </td>
        <td> The Destination file/directory of the sync. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> c:\Some\Path </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> Whether or not any changes were made. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> recurse </td>
        <td> Whether or not the recurse flag was toggled. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> purge </td>
        <td> Whether or not the purge flag was toggled. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> flags </td>
        <td> Any flags passed in by the user. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> /e /purge </td>
    </tr>
            <tr>
        <td> rc </td>
        <td> The return code retuned by robocopy. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1 </td>
    </tr>
            <tr>
        <td> msg </td>
        <td> Output intrepreted into a concise message. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> No files copied! </td>
    </tr>
            <tr>
        <td> output </td>
        <td> The output of running the robocopy command. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> -------------------------------------------------------------------------------
   ROBOCOPY     ::     Robust File Copy for Windows                              
-------------------------------------------------------------------------------
 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - This is not a complete port of the "synchronize" module. Unlike the "synchronize" module this only performs the sync/copy on the remote machine, not from the master to the remote machine.
    - This module does not currently support all Robocopy flags.
    - Works on Windows 7, Windows 8, Windows Server 2k8, and Windows Server 2k12



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
