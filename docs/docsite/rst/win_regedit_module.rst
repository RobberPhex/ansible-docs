.. _win_regedit:


win_regedit - Add, change, or remove registry keys and values
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add, modify or remove registry keys and values.
* More information about the windows registry from Wikipedia (https://en.wikipedia.org/wiki/Windows_Registry).




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
                <tr><td>data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Value of the registry entry <code>name</code> in <code>path</code>.</div><div>Binary data should be expressed a yaml byte array or as comma separated hex values.  An easy way to generate this is to run <code>regedit.exe</code> and use the <em>Export</em> option to save the registry values to a file.  In the exported file binary values will look like <code>hex:be,ef,be,ef</code>.  The <code>hex:</code> prefix is optional.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of registry entry in <code>path</code>.</div><div>This is an entry in the above <code>key</code> parameter.</div><div>If not provided, or empty we use the default name '(default)'</div></br>
    <div style="font-size: small;">aliases: entry<div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of registry path.</div><div>Should be in one of the following registry hives: HKCC, HKCR, HKCU, HKLM, HKU.</div></br>
    <div style="font-size: small;">aliases: key<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of registry entry.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>string</td>
        <td><ul><li>binary</li><li>dword</li><li>expandstring</li><li>multistring</li><li>string</li><li>qword</li></ul></td>
        <td><div>Registry value data type.</div></br>
    <div style="font-size: small;">aliases: datatype<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create registry path MyCompany
      win_regedit:
        path: HKCU:\Software\MyCompany
    
    - name: Add or update registry path MyCompany, with entry 'hello', and containing 'world'
      win_regedit:
        path: HKCU:\Software\MyCompany
        name: hello
        data: world
    
    - name: Add or update registry path MyCompany, with entry 'hello', and containing 1337
      win_regedit:
        path: HKCU:\Software\MyCompany
        name: hello
        data: 1337
        type: dword
    
    - name: Add or update registry path MyCompany, with entry 'hello', and containing binary data in hex-string format
      win_regedit:
        path: HKCU:\Software\MyCompany
        name: hello
        data: hex:be,ef,be,ef,be,ef,be,ef,be,ef
        type: binary
    
    - name: Add or update registry path MyCompany, with entry 'hello', and containing binary data in yaml format
      win_regedit:
        path: HKCU:\Software\MyCompany
        name: hello
        data: [0xbe,0xef,0xbe,0xef,0xbe,0xef,0xbe,0xef,0xbe,0xef]
        type: binary
    
    - name: Disable keyboard layout hotkey for all users (changes existing)
      win_regedit:
        path: HKU:\.DEFAULT\Keyboard Layout\Toggle
        name: Layout Hotkey
        data: 3
        type: dword
    
    - name: Disable language hotkey for current users (adds new)
      win_regedit:
        path: HKCU:\Keyboard Layout\Toggle
        name: Language Hotkey
        data: 3
        type: dword
    
    - name: Remove registry path MyCompany (including all entries it contains)
      win_regedit:
        path: HKCU:\Software\MyCompany
        state: absent
    
    - name: Remove entry 'hello' from registry path MyCompany
      win_regedit:
        path: HKCU:\Software\MyCompany
        name: hello
        state: absent

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
        <td> data_changed </td>
        <td> whether this invocation changed the data in the registry value </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> data_type_changed </td>
        <td> whether this invocation changed the datatype of the registry value </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Check-mode ``-C/--check`` and diff output (-D/--diff) are supported, so that you can test every change against the active configuration before applying changes.
    - Beware that some registry hives (HKEY_USERS in particular) do not allow to create new registry paths.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
