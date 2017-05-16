.. _copy:


copy - Copies files to remote locations.
++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`copy <copy>` module copies a file on the local box to remote locations. Use the :ref:`fetch <fetch>` module to copy files from remote locations to the local box. If you need variable interpolation in copied files, use the :ref:`template <template>` module.




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
    <td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Create a backup file including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.</div></td></tr>
            <tr>
    <td>content<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When used instead of 'src', sets the contents of a file directly to the specified value. This is for simple values, for anything complex or with formatting please switch to the template module.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remote absolute path where the file should be copied to. If src is a directory, this must be a directory too.</div></td></tr>
            <tr>
    <td>directory_mode<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When doing a recursive copy set the mode for the directories. If this is not set we will use the system defaults. The mode is only set on directories which are newly created, and will not affect those that already existed.</div></td></tr>
            <tr>
    <td>follow<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This flag indicates that filesystem links, if they exist, should be followed.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>the default is <code>yes</code>, which will replace the remote file when contents are different than the source. If <code>no</code>, the file will only be transferred if the destination does not exist.</div></br>
        <div style="font-size: small;">aliases: thirsty<div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the group that should own the file/directory, as would be fed to <em>chown</em></div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>mode the file or directory should be. For those used to <em>/usr/bin/chmod</em> remember that modes are actually octal numbers (like 0644). Leaving off the leading zero will likely have unexpected results. As of version 1.8, the mode may be specified as a symbolic mode (for example, <code>u+rwx</code> or <code>u=rw,g=r,o=r</code>).</div></td></tr>
            <tr>
    <td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the user that should own the file/directory, as would be fed to <em>chown</em></div></td></tr>
            <tr>
    <td>remote_src<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>False</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If False, it will search for src at originating/master machine, if True it will go to the remote/target machine for the src. Default is False.</div><div>Currently remote_src does not support recursive copying.</div></td></tr>
            <tr>
    <td>selevel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>s0</td>
        <td><ul></ul></td>
        <td><div>level part of the SELinux file context. This is the MLS/MCS attribute, sometimes known as the <code>range</code>. <code>_default</code> feature works as for <em>seuser</em>.</div></td></tr>
            <tr>
    <td>serole<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>role part of SELinux file context, <code>_default</code> feature works as for <em>seuser</em>.</div></td></tr>
            <tr>
    <td>setype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>type part of SELinux file context, <code>_default</code> feature works as for <em>seuser</em>.</div></td></tr>
            <tr>
    <td>seuser<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>user part of SELinux file context. Will default to system policy, if applicable. If set to <code>_default</code>, it will use the <code>user</code> portion of the policy if available</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Local path to a file to copy to the remote server; can be absolute or relative. If path is a directory, it is copied recursively. In this case, if path ends with "/", only inside contents of that directory are copied to destination. Otherwise, if it does not end with "/", the directory itself with all contents is copied. This behavior is similar to Rsync.</div></td></tr>
            <tr>
    <td>validate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The validation command to run before copying into place. The path to the file to validate is passed in via '%s' which must be present as in the example below. The command is passed securely so shell features like expansion and pipes won't work.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example from Ansible Playbooks
    - copy: src=/srv/myfiles/foo.conf dest=/etc/foo.conf owner=foo group=foo mode=0644
    
    # The same example as above, but using a symbolic mode equivalent to 0644
    - copy: src=/srv/myfiles/foo.conf dest=/etc/foo.conf owner=foo group=foo mode="u=rw,g=r,o=r"
    
    # Another symbolic mode example, adding some permissions and removing others
    - copy: src=/srv/myfiles/foo.conf dest=/etc/foo.conf owner=foo group=foo mode="u+rw,g-wx,o-rwx"
    
    # Copy a new "ntp.conf file into place, backing up the original if it differs from the copied version
    - copy: src=/mine/ntp.conf dest=/etc/ntp.conf owner=root group=root mode=644 backup=yes
    
    # Copy a new "sudoers" file into place, after passing validation with visudo
    - copy: src=/mine/sudoers dest=/etc/sudoers validate='visudo -cf %s'

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
        <td> backup_file </td>
        <td> name of backup file created </td>
        <td align=center> changed and if backup=yes </td>
        <td align=center> string </td>
        <td align=center> /path/to/file.txt.2015-02-12@22:09~ </td>
    </tr>
            <tr>
        <td> uid </td>
        <td> owner id of the file, after execution </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 100 </td>
    </tr>
            <tr>
        <td> dest </td>
        <td> destination file/path </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> /path/to/file.txt </td>
    </tr>
            <tr>
        <td> checksum </td>
        <td> checksum of the file after running copy </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 6e642bb8dd5c2e027bf21dd923337cbb4214f827 </td>
    </tr>
            <tr>
        <td> md5sum </td>
        <td> md5 checksum of the file after running copy </td>
        <td align=center> when supported </td>
        <td align=center> string </td>
        <td align=center> 2a5aeecc61dc98c4d780b14b330e3282 </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of the target, after execution </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> file </td>
    </tr>
            <tr>
        <td> gid </td>
        <td> group id of the file, after execution </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 100 </td>
    </tr>
            <tr>
        <td> mode </td>
        <td> permissions of the target, after execution </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 0644 </td>
    </tr>
            <tr>
        <td> owner </td>
        <td> owner of the file, after execution </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> httpd </td>
    </tr>
            <tr>
        <td> group </td>
        <td> group of the file, after execution </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> httpd </td>
    </tr>
            <tr>
        <td> size </td>
        <td> size of the target, after execution </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1220 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: The "copy" module recursively copy facility does not scale to lots (>hundreds) of files. For alternative, see synchronize module, which is a wrapper around rsync.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

