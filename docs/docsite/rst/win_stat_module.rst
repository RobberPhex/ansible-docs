.. _win_stat:


win_stat - returns information about a Windows file
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Returns information about a Windows file




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
                <tr><td>checksum_algorithm<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>sha1</td>
        <td><ul><li>md5</li><li>sha1</li><li>sha256</li><li>sha384</li><li>sha512</li></ul></td>
        <td><div>Algorithm to determine checksum of file. Will throw an error if the host is unable to use specified algorithm.</div>        </td></tr>
                <tr><td>get_checksum<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Whether to return a checksum of the file (default sha1)</div>        </td></tr>
                <tr><td>get_md5<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Whether to return the checksum sum of the file. Between Ansible 1.9 and 2.2 this is no longer an MD5, but a SHA1 instead. As of Ansible 2.3 this is back to an MD5. Will return None if host is unable to use specified algorithm.</div><div>This option is deprecated in Ansible 2.3 and is replaced with <code>checksum_algorithm=md5</code>.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The full path of the file/object to get the facts of; both forward and back slashes are accepted.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Obtain information about a file
      win_stat:
        path: C:\foo.ini
      register: file_info
    
    # Obtain information about a folder
    - win_stat:
        path: C:\bar
      register: folder_info
    
    # Get MD5 checksum of a file
    - win_stat:
        path: C:\foo.ini
        get_checksum: yes
        checksum_algorithm: md5
      register: md5_checksum
    
    - debug:
        var: md5_checksum.stat.checksum
    
    # Get SHA1 checksum of file
    - win_stat:
        path: C:\foo.ini
        get_checksum: yes
      register: sha1_checksum
    
    - debug:
        var: sha1_checksum.stat.checksum
    
    # Get SHA256 checksum of file
    - win_stat:
        path: C:\foo.ini
        get_checksum: yes
        checksum_algorithm: sha256
      register: sha256_checksum
    
    - debug:
        var: sha256_checksum.stat.checksum

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
        <td> stat </td>
        <td> dictionary containing all the stat data </td>
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
        <td> isshared </td>
        <td> if the path is shared or not </td>
        <td align=center> success, path exists </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
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
        <td align=center> success, path exists, file is not a link </td>
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
        <td align=center> success, path exists, file is a directory and isshared == True </td>
        <td align=center> string </td>
        <td align=center> file-share </td>
        </tr>
                <tr>
        <td> checksum </td>
        <td> The checksum of a file based on checksum_algorithm specified </td>
        <td align=center> success, path exist, path is a file, get_checksum == True checksum_algorithm specified is supported </td>
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
        <td> md5 </td>
        <td> The MD5 checksum of a file (Between Ansible 1.9 and 2.2 this was returned as a SHA1 hash) </td>
        <td align=center> success, path exist, path is a file, get_md5 == True, md5 is supported </td>
        <td align=center> string </td>
        <td align=center> 09cb79e8fc7453c84a07f644e441fd81623b7f98 </td>
        </tr>
        
        </table>
    </td></tr>

            <tr>
        <td> changed </td>
        <td> Whether anything was changed </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
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
