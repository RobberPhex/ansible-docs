.. _win_copy:


win_copy - Copies files to remote locations on windows hosts.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``win_copy`` module copies a file on the local box to remote windows locations.




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
                <tr><td>content<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When used instead of <code>src</code>, sets the contents of a file directly to the specified value. This is for simple values, for anything complex or with formatting please switch to the template module.</div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Remote absolute path where the file should be copied to. If src is a directory, this must be a directory too.</div><div>Use \ for path separators or \\ when in "double quotes".</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If set to <code>yes</code>, the remote file will be replaced when content is different than the source.</div><div>If set to <code>no</code>, the remote file will only be transferred if the destination does not exist.</div>        </td></tr>
                <tr><td>remote_src<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If False, it will search for src at originating/master machine, if True it will go to the remote/target machine for the src.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Local path to a file to copy to the remote server; can be absolute or relative. If path is a directory, it is copied recursively. In this case, if path ends with "/", only inside contents of that directory are copied to destination. Otherwise, if it does not end with "/", the directory itself with all contents is copied. This behavior is similar to Rsync.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Copy a single file
      win_copy:
        src: /srv/myfiles/foo.conf
        dest: c:\Temp\foo.conf
    - name: Copy files/temp_files to c:\temp
      win_copy:
        src: files/temp_files/
        dest: c:\Temp
    - name: Copy a single file where the source is on the remote host
      win_copy:
        src: C:\temp\foo.txt
        dest: C:\ansible\foo.txt
        remote_src: True
    - name: Copy a folder recursively where the source is on the remote host
      win_copy:
        src: C:\temp
        dest: C:\ansible
        remote_src: True
    - name: Set the contents of a file
      win_copy:
        dest: C:\temp\foo.txt
        content: abc123

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
        <td align=center> changed, src is a file </td>
        <td align=center> string </td>
        <td align=center> foo.txt </td>
    </tr>
            <tr>
        <td> dest </td>
        <td> destination file/path </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> C:\Temp\ </td>
    </tr>
            <tr>
        <td> checksum </td>
        <td> sha1 checksum of the file after running copy </td>
        <td align=center> success, src is a file </td>
        <td align=center> string </td>
        <td align=center> 6e642bb8dd5c2e027bf21dd923337cbb4214f827 </td>
    </tr>
            <tr>
        <td> operation </td>
        <td> whether a single file copy took place or a folder copy </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> file_copy </td>
    </tr>
            <tr>
        <td> size </td>
        <td> size of the target, after execution </td>
        <td align=center> changed (src is a file or remote_src == True) </td>
        <td align=center> int </td>
        <td align=center> 1220 </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
