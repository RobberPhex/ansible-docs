.. _win_stat:


win_stat - returns information about a Windows file
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Returns information about a Windows file




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
    <td>get_checksum<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether to return a checksum of the file (only sha1 currently supported)</div></td></tr>
            <tr>
    <td>get_md5<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether to return the checksum sum of the file. As of Ansible 1.9 this is no longer a MD5, but a SHA1 instead.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The full path of the file/object to get the facts of; both forward and back slashes are accepted.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Obtain information about a file
    
    - win_stat: path=C:\foo.ini
      register: file_info
    
    - debug: var=file_info




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

