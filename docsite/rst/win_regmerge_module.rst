.. _win_regmerge:


win_regmerge - Merges the contents of a registry file into the windows registry
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Wraps the reg.exe command to import the contents of a registry file.
Suitable for use with registry files created using :ref:`win_template <win_template>`.
Windows registry files have a specific format and must be constructed correctly with carriage return and line feed line endings otherwise they will not be merged.
Exported registry files often start with a Byte Order Mark which must be removed if the file is to templated using :ref:`win_template <win_template>`.
Registry file format is described at https://support.microsoft.com/en-us/kb/310516
See also :ref:`win_template <win_template>`, :ref:`win_regedit <win_regedit>`




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
    <td>compare_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no default</td>
        <td><ul></ul></td>
        <td><div>The parent key to use when comparing the contents of the registry to the contents of the file.  Needs to be in HKLM or HKCU part of registry.  Use a PS-Drive style path for example HKLM:\SOFTWARE not HKEY_LOCAL_MACHINE\SOFTWARE If not supplied, or the registry key is not found, no comparison will be made, and the module will report changed.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>no default</td>
        <td><ul></ul></td>
        <td><div>The full path including file name to the registry file on the remote machine to be merged</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Merge in a registry file without comparing to current registry
      # Note that paths using / to separate are preferred as they require less special handling than \ 
      win_regmerge:
        path: C:/autodeploy/myCompany-settings.reg
      # Compare and merge registry file
      win_regmerge:
        path: C:/autodeploy/myCompany-settings.reg
        compare_to: HKLM:\SOFTWARE\myCompany

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
        <td> difference_count </td>
        <td> number of differences between the registry and the file </td>
        <td align=center> changed </td>
        <td align=center> integer </td>
        <td align=center> 1 </td>
    </tr>
            <tr>
        <td> compared </td>
        <td> whether a comparison has taken place between the registry and the file </td>
        <td align=center> when a comparison key has been supplied and comparison has been attempted </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> compare_to_key_found </td>
        <td> whether the parent registry key has been found for comparison </td>
        <td align=center> when comparison key not found in registry </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Organise your registry files so that they contain a single root registry key if you want to use the compare_to functionality. This module does not force registry settings to be in the state described in the file.  If registry settings have been modified externally the module will merge the contents of the file but continue to report differences on subsequent runs. To force registry change, use :ref:`win_regedit <win_regedit>` with state=absent before using :ref:`win_regmerge <win_regmerge>`.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

