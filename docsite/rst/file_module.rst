.. _file:


file - Sets attributes of files
+++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Sets attributes of files, symlinks, and directories, or removes files/symlinks/directories. Many other modules support the same options as the :ref:`file <file>` module - including :ref:`copy <copy>`, :ref:`template <template>`, and :ref:`assemble <assemble>`.




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
    <td>follow<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This flag indicates that filesystem links, if they exist, should be followed.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>force the creation of the symlinks in two cases: the source file does not exist (but will appear later); the destination exists and is a file (so, we need to unlink the "path" file and create symlink to the "src" file in place of it).</div></td></tr>
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
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the file being managed.  Aliases: <em>dest</em>, <em>name</em></div></br>
        <div style="font-size: small;">aliases: dest, name<div></td></tr>
            <tr>
    <td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>recursively set the specified file attributes (applies only to state=directory)</div></td></tr>
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
        <td><div>path of the file to link to (applies only to <code>state=link</code>). Will accept absolute, relative and nonexisting paths. Relative paths are not expanded.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>link</li><li>directory</li><li>hard</li><li>touch</li><li>absent</li></ul></td>
        <td><div>If <code>directory</code>, all immediate subdirectories will be created if they do not exist, since 1.7 they will be created with the supplied permissions. If <code>file</code>, the file will NOT be created if it does not exist, see the <span class='module'>copy</span> or <span class='module'>template</span> module if you want that behavior.  If <code>link</code>, the symbolic link will be created or changed. Use <code>hard</code> for hardlinks. If <code>absent</code>, directories will be recursively deleted, and files or symlinks will be unlinked. Note that <span class='module'>file</span> will not fail if the <code>path</code> does not exist as the state did not change. If <code>touch</code> (new in 1.4), an empty file will be created if the <code>path</code> does not exist, while an existing file or directory will receive updated file access and modification times (similar to the way `touch` works from the command line).</div></td></tr>
            <tr>
    <td>unsafe_writes<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Normally this module uses atomic operations to prevent data corruption or inconsistent reads from the target files, sometimes systems are configured or just broken in ways that prevent this. One example are docker mounted files, they cannot be updated atomically and can only be done in an unsafe manner.</div><div>This boolean option allows ansible to fall back to unsafe methods of updating files for those cases in which you do not have any other choice. Be aware that this is subject to race conditions and can lead to data corruption.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # change file ownership, group and mode. When specifying mode using octal numbers, first digit should always be 0.
    - file: path=/etc/foo.conf owner=foo group=foo mode=0644
    - file: src=/file/to/link/to dest=/path/to/symlink owner=foo group=foo state=link
    - file: src=/tmp/{{ item.src }} dest={{ item.dest }} state=link
      with_items:
        - { src: 'x', dest: 'y' }
        - { src: 'z', dest: 'k' }
    
    # touch a file, using symbolic modes to set the permissions (equivalent to 0644)
    - file: path=/etc/foo.conf state=touch mode="u=rw,g=r,o=r"
    
    # touch the same file, but add/remove some permissions
    - file: path=/etc/foo.conf state=touch mode="u+rw,g-wx,o-rwx"
    
    # create a directory if it doesn't exist
    - file: path=/etc/some_directory state=directory mode=0755
    


Notes
-----

.. note:: See also :ref:`copy <copy>`, :ref:`template <template>`, :ref:`assemble <assemble>`


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

