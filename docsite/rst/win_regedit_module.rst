.. _win_regedit:


win_regedit - Add, Edit, or Remove Registry Keys and Values
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add, Edit, or Remove Registry Keys and Values using ItemProperties Cmdlets




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
    <td>data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Registry Value Data</div></td></tr>
            <tr>
    <td>datatype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>string</td>
        <td><ul><li>binary</li><li>dword</li><li>expandstring</li><li>multistring</li><li>string</li><li>qword</li></ul></td>
        <td><div>Registry Value Data Type</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of Registry Key</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of Registry Value</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of Registry Value</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Creates Registry Key called MyCompany.
      win_regedit:
        key: HKCU:\Software\MyCompany
        
      # Creates Registry Key called MyCompany,
      # a value within MyCompany Key called "hello", and
      # data for the value "hello" containing "world".
      win_regedit:
        key: HKCU:\Software\MyCompany
        value: hello
        data: world
    
      # Creates Registry Key called MyCompany,
      # a value within MyCompany Key called "hello", and
      # data for the value "hello" containing "1337" as type "dword".
      win_regedit:
        key: HKCU:\Software\MyCompany
        value: hello
        data: 1337
        datatype: dword
    
      # Delete Registry Key MyCompany
      # NOTE: Not specifying a value will delete the root key which means
      # all values will be deleted
      win_regedit:
        key: HKCU:\Software\MyCompany
        state: absent
        
      # Delete Registry Value "hello" from MyCompany Key
      win_regedit:
        key: HKCU:\Software\MyCompany
        value: hello
        state: absent




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

