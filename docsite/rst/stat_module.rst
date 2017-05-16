.. _stat:


stat - retrieve file or file system status
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Retrieves facts for a file similar to the linux/unix 'stat' command.




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
    <td>checksum_algorithm<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>sha1</td>
        <td><ul><li>sha1</li><li>sha224</li><li>sha256</li><li>sha384</li><li>sha512</li></ul></td>
        <td><div>Algorithm to determine checksum of file. Will throw an error if the host is unable to use specified algorithm.</div></br>
        <div style="font-size: small;">aliases: checksum_algo, checksum<div></td></tr>
            <tr>
    <td>follow<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether to follow symlinks</div></td></tr>
            <tr>
    <td>get_checksum<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether to return a checksum of the file (default sha1)</div></td></tr>
            <tr>
    <td>get_md5<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether to return the md5 sum of the file.  Will return None if we're unable to use md5 (Common for FIPS-140 compliant systems)</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The full path of the file/object to get the facts of</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Obtain the stats of /etc/foo.conf, and check that the file still belongs
    # to 'root'. Fail otherwise.
    - stat: path=/etc/foo.conf
      register: st
    - fail: msg="Whoops! file ownership has changed"
      when: st.stat.pw_name != 'root'
    
    # Determine if a path exists and is a symlink. Note that if the path does
    # not exist, and we test sym.stat.islnk, it will fail with an error. So
    # therefore, we must test whether it is defined.
    # Run this to understand the structure, the skipped ones do not pass the
    # check performed by 'when'
    - stat: path=/path/to/something
      register: sym
    - debug: msg="islnk isn't defined (path doesn't exist)"
      when: sym.stat.islnk is not defined
    - debug: msg="islnk is defined (path must exist)"
      when: sym.stat.islnk is defined
    - debug: msg="Path exists and is a symlink"
      when: sym.stat.islnk is defined and sym.stat.islnk
    - debug: msg="Path exists and isn't a symlink"
      when: sym.stat.islnk is defined and sym.stat.islnk == False
    
    
    # Determine if a path exists and is a directory.  Note that we need to test
    # both that p.stat.isdir actually exists, and also that it's set to true.
    - stat: path=/path/to/something
      register: p
    - debug: msg="Path exists and is a directory"
      when: p.stat.isdir is defined and p.stat.isdir
    
    # Don't do md5 checksum
    - stat: path=/path/to/myhugefile get_md5=no
    
    # Use sha256 to calculate checksum
    - stat: path=/path/to/something checksum_algorithm=sha256

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
        <td> uid </td>
        <td> Numeric id representing the file owner </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> int </td>
        <td align=center> 1003 </td>
        </tr>
                <tr>
        <td> exists </td>
        <td> if the destination path actually exists or not </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> checksum_algorithm </td>
        <td> hash of the path </td>
        <td align=center> success, path exists, user can read stats, path supports hashing and supplied checksum algorithm is available </td>
        <td align=center> string </td>
        <td align=center> 50ba294cdf28c0d5bcde25708df53346825a429f </td>
        </tr>
                <tr>
        <td> woth </td>
        <td> Tells you if others have write permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> mtime </td>
        <td> Time of last modification </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> float </td>
        <td align=center> 1424348972.58 </td>
        </tr>
                <tr>
        <td> inode </td>
        <td> Inode number of the path </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> int </td>
        <td align=center> 12758 </td>
        </tr>
                <tr>
        <td> isgid </td>
        <td> Tells you if the invoking user's group id matches the owner's group id </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> size </td>
        <td> Size in bytes for a plain file, ammount of data for some special files </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> int </td>
        <td align=center> 203 </td>
        </tr>
                <tr>
        <td> wgrp </td>
        <td> Tells you if the owner's group has write permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> isuid </td>
        <td> Tells you if the invoking user's id matches the owner's id </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> isreg </td>
        <td> Tells you if the path is a regular file </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> pw_name </td>
        <td> User name of owner </td>
        <td align=center> success, path exists and user can read stats and installed python supports it </td>
        <td align=center> string </td>
        <td align=center> httpd </td>
        </tr>
                <tr>
        <td> gid </td>
        <td> Numeric id representing the group of the owner </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> int </td>
        <td align=center> 1003 </td>
        </tr>
                <tr>
        <td> ischr </td>
        <td> Tells you if the path is a character device </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> wusr </td>
        <td> Tells you if the owner has write permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> xoth </td>
        <td> Tells you if others have execute permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> rusr </td>
        <td> Tells you if the owner has read permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> nlink </td>
        <td> Number of links to the inode (hard links) </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> int </td>
        <td align=center> 1 </td>
        </tr>
                <tr>
        <td> issock </td>
        <td> Tells you if the path is a unix domain socket </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> rgrp </td>
        <td> Tells you if the owner's group has read permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> gr_name </td>
        <td> Group name of owner </td>
        <td align=center> success, path exists and user can read stats and installed python supports it </td>
        <td align=center> string </td>
        <td align=center> www-data </td>
        </tr>
                <tr>
        <td> path </td>
        <td> The full path of the file/object to get the facts of </td>
        <td align=center> success and if path exists </td>
        <td align=center> string </td>
        <td align=center> /path/to/file </td>
        </tr>
                <tr>
        <td> xusr </td>
        <td> Tells you if the owner has execute permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> atime </td>
        <td> Time of last access </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> float </td>
        <td align=center> 1424348972.58 </td>
        </tr>
                <tr>
        <td> lnk_source </td>
        <td> Original path </td>
        <td align=center> success, path exists and user can read stats and the path is a symbolic link </td>
        <td align=center> string </td>
        <td align=center> /home/foobar/21102015-1445431274-908472971 </td>
        </tr>
                <tr>
        <td> md5 </td>
        <td> md5 hash of the path </td>
        <td align=center> success, path exists and user can read stats and path supports hashing and md5 is supported </td>
        <td align=center> string </td>
        <td align=center> f88fa92d8cf2eeecf4c0a50ccc96d0c0 </td>
        </tr>
                <tr>
        <td> isdir </td>
        <td> Tells you if the path is a directory </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> ctime </td>
        <td> Time of last metadata update or creation (depends on OS) </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> float </td>
        <td align=center> 1424348972.58 </td>
        </tr>
                <tr>
        <td> isblk </td>
        <td> Tells you if the path is a block device </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> xgrp </td>
        <td> Tells you if the owner's group has execute permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> dev </td>
        <td> Device the inode resides on </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> int </td>
        <td align=center> 33 </td>
        </tr>
                <tr>
        <td> roth </td>
        <td> Tells you if others have read permission </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> isfifo </td>
        <td> Tells you if the path is a named pipe </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> mode </td>
        <td> Unix permissions of the file in octal </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> octal </td>
        <td align=center> 1755 </td>
        </tr>
                <tr>
        <td> islnk </td>
        <td> Tells you if the path is a symbolic link </td>
        <td align=center> success, path exists and user can read stats </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

