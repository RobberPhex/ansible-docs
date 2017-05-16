.. _win_find:


win_find - return a list of files based on specific criteria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Return a list of files based on specified criteria.
* Multiple criteria are AND'd together.




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
                <tr><td>age<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Select files or folders whose age is equal to or greater than the specified time. Use a negative age to find files equal to or less than the specified time. You can choose seconds, minutes, hours, days or weeks by specifying the first letter of an of those words (e.g., "2s", "10d", 1w").</div>        </td></tr>
                <tr><td>age_stamp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>mtime</td>
        <td><ul><li>atime</li><li>mtime</li><li>ctime</li></ul></td>
        <td><div>Choose the file property against which we compare <code>age</code>. The default attribute we compare with is the last modification time.</div>        </td></tr>
                <tr><td>checksum_algorithm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>sha1</td>
        <td><ul><li>md5</li><li>sha1</li><li>sha256</li><li>sha384</li><li>sha512</li></ul></td>
        <td><div>Algorithm to determine the checksum of a file. Will throw an error if the host is unable to use specified algorithm.</div>        </td></tr>
                <tr><td>file_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>directory</li></ul></td>
        <td><div>Type of file to search for</div>        </td></tr>
                <tr><td>follow<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Set this to true to follow symlinks in the path. This needs to be used in conjunction with <code>recurse</code>.</div>        </td></tr>
                <tr><td>get_checksum<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Whether to return a checksum of the file in the return info (default sha1), use <code>checksum_algorithm</code> to change from the default.</div>        </td></tr>
                <tr><td>hidden<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Set this to include hidden files or folders</div>        </td></tr>
                <tr><td>paths<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>List of paths of directories to search for files or folders in. This can be supplied as a single path or a list of paths.</div>        </td></tr>
                <tr><td>patterns<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>One or more (powershell or regex) patterns to compare filenames with. The type of pattern matching is controlled by <code>use_regex</code> option. The patterns retrict the list of files or folders to be returned based on the filenames. For a file to be matched it only has to match with one pattern in a list provided.</div>        </td></tr>
                <tr><td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Will recursively descend into the directory looking for files or folders</div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Select files or folders whose size is equal to or greater than the specified size. Use a negative value to find files equal to or less than the specified size. You can specify the size with a suffix of the byte type i.e. kilo = k, mega = m... Size is not evaluated for symbolic links.</div>        </td></tr>
                <tr><td>use_regex<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Will set patterns to run as a regex check if true</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Find files in path
    - win_find:
        paths: D:\temp
    
    # Find hidden files in path
    - win_find:
        paths: D:\temp
        hidden: True
    
    # Find files in multiple paths
    - win_find:
        paths: ['C:\temp', 'D:\temp']
    
    # Find files in directory while searching recursively
    - win_find:
        paths: D:\temp
        recurse: True
    
    # Find files in directory while following symlinks
    - win_find:
        paths: D:\temp
        recurse: True
        follow: True
    
    # Find files with .log and .out extension using powershell wildcards
    - win_find:
        paths: D:\temp
        patterns: ['*.log', '*.out']
    
    # Find files in path based on regex pattern
    - win_find:
        paths: D:\temp
        patterns: 'out_\d{8}-\d{6}.log'
    
    # Find files older than 1 day
    - win_find:
        paths: D:\temp
        age: 86400
    
    # Find files older than 1 day based on create time
    - win_find:
        paths: D:\temp
        age: 86400
        age_stamp: ctime
    
    # Find files older than 1 day with unit syntax
    - win_find:
        paths: D:\temp
        age: 1d
    
    # Find files newer than 1 hour
    - win_find:
        paths: D:\temp
        age: -3600
    
    # Find files newer than 1 hour with unit syntax
    - win_find:
        paths: D:\temp
        age: -1h
    
    # Find files larger than 1MB
    - win_find:
        paths: D:\temp
        size: 1048576
    
    # Find files larger than 1GB with unit syntax
    - win_find:
        paths: D:\temp
        size: 1g
    
    # Find files smaller than 1MB
    - win_find:
        paths: D:\temp
        size: -1048576
    
    # Find files smaller than 1GB with unit syntax
    - win_find:
        paths: D:\temp
        size: -1g
    
    # Find folders/symlinks in multiple paths
    - win_find:
        paths: ['C:\temp', 'D:\temp']
        file_type: directory
    
    # Find files and return SHA256 checksum of files found
    - win_find:
        paths: C:\temp
        get_checksum: True
        checksum_algorithm: sha256
    
    # Find files and do not return the checksum
    - win_find:
        path: C:\temp
        get_checksum: False

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
        <td> files </td>
        <td> Information on the files/folders that match the criteria returned as a list of dictionary elements for each file matched </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> lastwritetime </td>
        <td> the last modification time of the file represented in seconds since epoch </td>
        <td align=center> success, path exists </td>
        <td align=center> float </td>
        <td align=center> 1477984205.15 </td>
        </tr>
                <tr>
        <td> creationtime </td>
        <td> the create time of the file represented in seconds since epoch </td>
        <td align=center> success, path exists </td>
        <td align=center> float </td>
        <td align=center> 1477984205.15 </td>
        </tr>
                <tr>
        <td> lastaccesstime </td>
        <td> the last access time of the file represented in seconds since epoch </td>
        <td align=center> success, path exists </td>
        <td align=center> float </td>
        <td align=center> 1477984205.15 </td>
        </tr>
                <tr>
        <td> owner </td>
        <td> the owner of the file </td>
        <td align=center> success, path exists </td>
        <td align=center> string </td>
        <td align=center> BUILTIN\Administrators </td>
        </tr>
                <tr>
        <td> path </td>
        <td> the full absolute path to the file </td>
        <td align=center> success, path exists </td>
        <td align=center> string </td>
        <td align=center> BUILTIN\Administrators </td>
        </tr>
                <tr>
        <td> isarchive </td>
        <td> if the path is ready for archiving or not </td>
        <td align=center> success, path exists </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> ishidden </td>
        <td> if the path is hidden or not </td>
        <td align=center> success, path exists </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> lnk_source </td>
        <td> the target of the symbolic link, will return null if not a link or the link is broken </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> C:\temp </td>
        </tr>
                <tr>
        <td> size </td>
        <td> the size in bytes of a file or folder </td>
        <td align=center> success, path exists, path is not a link </td>
        <td align=center> int </td>
        <td align=center> 1024 </td>
        </tr>
                <tr>
        <td> isdir </td>
        <td> if the path is a directory or not </td>
        <td align=center> success, path exists </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> extension </td>
        <td> the extension of the file at path </td>
        <td align=center> success, path exists, path is a file </td>
        <td align=center> string </td>
        <td align=center> .ps1 </td>
        </tr>
                <tr>
        <td> isreadonly </td>
        <td> if the path is read only or not </td>
        <td align=center> success, path exists </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> sharename </td>
        <td> the name of share if folder is shared </td>
        <td align=center> success, path exists, path is a directory and isshared == True </td>
        <td align=center> string </td>
        <td align=center> file-share </td>
        </tr>
                <tr>
        <td> checksum </td>
        <td> The checksum of a file based on checksum_algorithm specified </td>
        <td align=center> success, path exists, path is a file, get_checksum == True </td>
        <td align=center> string </td>
        <td align=center> 09cb79e8fc7453c84a07f644e441fd81623b7f98 </td>
        </tr>
                <tr>
        <td> islnk </td>
        <td> if the path is a symbolic link or junction or not </td>
        <td align=center> success, path exists </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> attributes </td>
        <td> attributes of the file at path in raw form </td>
        <td align=center> success, path exists </td>
        <td align=center> string </td>
        <td align=center> Archive, Hidden </td>
        </tr>
                <tr>
        <td> isshared </td>
        <td> if the path is shared or not </td>
        <td align=center> success, path exists </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
        
        </table>
    </td></tr>

            <tr>
        <td> changed </td>
        <td> Whether anything was chagned </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> examined </td>
        <td> The number of files/folders that was checked </td>
        <td align=center> always </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
    </tr>
            <tr>
        <td> matched </td>
        <td> The number of files/folders that match the criteria </td>
        <td align=center>  </td>
        <td align=center> int </td>
        <td align=center> 2 </td>
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
