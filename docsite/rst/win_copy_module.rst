.. _win_copy:


win_copy - Copies files to remote locations on windows hosts.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`win_copy <win_copy>` module copies a file on the local box to remote windows locations.




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
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remote absolute path where the file should be copied to. If src is a directory, this must be a directory too. Use \ for path separators.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Local path to a file to copy to the remote server; can be absolute or relative. If path is a directory, it is copied recursively. In this case, if path ends with "/", only inside contents of that directory are copied to destination. Otherwise, if it does not end with "/", the directory itself with all contents is copied. This behavior is similar to Rsync.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Copy a single file
    - win_copy: src=/srv/myfiles/foo.conf dest=c:\TEMP\foo.conf
    
    # Copy the contents of files/temp_files dir into c:	emp\.  Includes any sub dirs under files/temp_files
    # Note the use of unix style path in the dest.  
    # This is necessary because \ is yaml escape sequence
    - win_copy: src=files/temp_files/ dest=c:/temp/
    
    # Copy the files/temp_files dir and any files or sub dirs into c:	emp
    # Copies the folder because there is no trailing / on 'files/temp_files'
    - win_copy: src=files/temp_files dest=c:/temp/
    

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
        <td> source file used for the copy on the target machine </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> /home/httpd/.ansible/tmp/ansible-tmp-1423796390.97-147729857856000/source </td>
    </tr>
            <tr>
        <td> original_basename </td>
        <td> basename of the copied file </td>
        <td align=center> changed (single files only) </td>
        <td align=center> string </td>
        <td align=center> foo.txt </td>
    </tr>
            <tr>
        <td> dest </td>
        <td> destination file/path </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> c:/temp/ </td>
    </tr>
            <tr>
        <td> checksum </td>
        <td> checksum of the file after running copy </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 6e642bb8dd5c2e027bf21dd923337cbb4214f827 </td>
    </tr>
            <tr>
        <td> operation </td>
        <td> whether a single file copy took place or a folder copy </td>
        <td align=center> changed (single files only) </td>
        <td align=center> string </td>
        <td align=center> file_copy </td>
    </tr>
            <tr>
        <td> size </td>
        <td> size of the target, after execution </td>
        <td align=center> changed (single files only) </td>
        <td align=center> int </td>
        <td align=center> 1220 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: The "win_copy" module is best used for small files only. This module should **not** be used for files bigger than 3Mb as this will result in a 500 response from the winrm host and it will not be possible to connect via winrm again until the windows remote management service has been restarted on the windows host. Files larger than 1Mb will take minutes to transfer. The recommended way to transfer large files is using win_get_url or collecting from a windows file share folder.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

