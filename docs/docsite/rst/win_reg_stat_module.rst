.. _win_reg_stat:


win_reg_stat - returns information about a Windows registry key or property of a key
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Like :ref:`win_file <win_file>`, :ref:`win_reg_stat <win_reg_stat>` will return whether the key/property exists.
* It also returns the sub keys and properties of the key specified.
* If specifying a property name through *property*, it will return the information specific for that property.




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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The registry property name to get information for, the return json will not include the sub_keys and properties entries for the <em>key</em> specified.</div></br>
    <div style="font-size: small;">aliases: entry, value, property<div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The full registry key path including the hive to search for.</div></br>
    <div style="font-size: small;">aliases: key<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Obtain information about a registry key using short form
    - win_reg_stat:
        path: HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
      register: current_version
    
    # Obtain information about a registry key property
    - win_reg_stat:
        path: HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
        name: CommonFilesDir
      register: common_files_dir

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
        <td> raw_value </td>
        <td> Returns the raw value of the registry property, REG_EXPAND_SZ has no string expansion, REG_BINARY or REG_NONE is in hex 0x format. REG_NONE, this value is a hex string in the 0x format. </td>
        <td align=center> success, path/property exists and property specified </td>
        <td align=center> string </td>
        <td align=center> %ProgramDir%\\Common Files </td>
    </tr>
            <tr>
        <td> sub_keys </td>
        <td> A list of all the sub keys of the key specified. </td>
        <td align=center> success, path exists and property not specified </td>
        <td align=center> list </td>
        <td align=center> ['AppHost', 'Casting', 'DateTime'] </td>
    </tr>
            <tr>
        <td> exists </td>
        <td> States whether the registry key/property exists. </td>
        <td align=center> success and path/property exists </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> Whether anything was changed. </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> type </td>
        <td> The property type. </td>
        <td align=center> success, path/property exists and property specified </td>
        <td align=center> string </td>
        <td align=center> REG_EXPAND_SZ </td>
    </tr>
            <tr>
        <td> properties </td>
        <td> A list of all the properties and their values in the key. </td>
        <td align=center> success, path exists and property not specified </td>
        <td align=center> list </td>
        <td align=center> [{'binary_property': {'raw_value': ['0x01', '0x16'], 'type': 'REG_BINARY', 'value': [1, 22]}}, {'multi_string_property': {'raw_value': ['a', 'b'], 'type': 'REG_MULTI_SZ', 'value': ['a', 'b']}}] </td>
    </tr>
            <tr>
        <td> value </td>
        <td> The value of the property. </td>
        <td align=center> success, path/property exists and property specified </td>
        <td align=center> string </td>
        <td align=center> C:\\Program Files\\Common Files </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
