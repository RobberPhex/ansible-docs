.. _win_file_version:


win_file_version - Get DLL or EXE file build version
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Get DLL or EXE file build version
* change state alway be false




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
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>File to get version(provide absolute path)</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Get acm instance version
      win_file_version:
        path: C:\Windows\System32\cmd.exe
      register: exe_file_version
    
    - debug:
        msg: '{{ exe_file_version }}'

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
        <td> win_file_version.file_major_part </td>
        <td> the major part of the version number. </td>
        <td align=center> no error </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> win_file_version.file_minor_part </td>
        <td> the minor part of the version number of the file. </td>
        <td align=center> no error </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> win_file_version.file_version </td>
        <td> file version number. </td>
        <td align=center> no error </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> win_file_version.product_version </td>
        <td> the version of the product this file is distributed with. </td>
        <td align=center> no error </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> win_file_version.file_private_part </td>
        <td> file private part number. </td>
        <td align=center> no error </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> win_file_version.path </td>
        <td> file path </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> win_file_version.file_build_part </td>
        <td> build number of the file. </td>
        <td align=center> no error </td>
        <td align=center> string </td>
        <td align=center>  </td>
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
