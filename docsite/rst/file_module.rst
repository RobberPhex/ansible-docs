.. _file:


file - Sets attributes of files
+++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Sets attributes of files, symlinks, and directories, or removes files/symlinks/directories. Many other modules support the same options as the ``file`` module - including ``copy``, ``template``, and ``assemble``.

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
    <td>follow</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>This flag indicates that filesystem links, if they exist, should be followed. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>force the creation of the symlinks in two cases: the source file does not exist (but will appear later); the destination exists and is a file (so, we need to unlink the "path" file and create symlink to the "src" file in place of it).</td>
    </tr>
            <tr>
    <td>group</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the group that should own the file/directory, as would be fed to <em>chown</em></td>
    </tr>
            <tr>
    <td>mode</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>mode the file or directory should be, such as 0644 as would be fed to <em>chmod</em>. As of version 1.8, the mode may be specified as a symbolic mode (for example, <code>u+rwx</code> or <code>u=rw,g=r,o=r</code>).</td>
    </tr>
            <tr>
    <td>owner</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the user that should own the file/directory, as would be fed to <em>chown</em></td>
    </tr>
            <tr>
    <td>path</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to the file being managed.  Aliases: <em>dest</em>, <em>name</em></td>
    </tr>
            <tr>
    <td>recurse</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>recursively set the specified file attributes (applies only to state=directory) (added in Ansible 1.1)</td>
    </tr>
            <tr>
    <td>selevel</td>
    <td>no</td>
    <td>s0</td>
        <td><ul></ul></td>
        <td>level part of the SELinux file context. This is the MLS/MCS attribute, sometimes known as the <code>range</code>. <code>_default</code> feature works as for <em>seuser</em>.</td>
    </tr>
            <tr>
    <td>serole</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>role part of SELinux file context, <code>_default</code> feature works as for <em>seuser</em>.</td>
    </tr>
            <tr>
    <td>setype</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>type part of SELinux file context, <code>_default</code> feature works as for <em>seuser</em>.</td>
    </tr>
            <tr>
    <td>seuser</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>user part of SELinux file context. Will default to system policy, if applicable. If set to <code>_default</code>, it will use the <code>user</code> portion of the policy if available</td>
    </tr>
            <tr>
    <td>src</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path of the file to link to (applies only to <code>state=link</code>). Will accept absolute, relative and nonexisting paths. Relative paths are not expanded.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>link</li><li>directory</li><li>hard</li><li>touch</li><li>absent</li></ul></td>
        <td>If <code>directory</code>, all immediate subdirectories will be created if they do not exist, since 1.7 they will be created with the supplied permissions. If <code>file</code>, the file will NOT be created if it does not exist, see the <span class='module'>copy</span> or <span class='module'>template</span> module if you want that behavior.  If <code>link</code>, the symbolic link will be created or changed. Use <code>hard</code> for hardlinks. If <code>absent</code>, directories will be recursively deleted, and files or symlinks will be unlinked. If <code>touch</code> (new in 1.4), an empty file will be created if the c(path) does not exist, while an existing file or directory will receive updated file access and modification times (similar to the way `touch` works from the command line).</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - file: path=/etc/foo.conf owner=foo group=foo mode=0644
    - file: src=/file/to/link/to dest=/path/to/symlink owner=foo group=foo state=link
    - file: src=/tmp/{{ item.path }} dest={{ item.dest }} state=link
      with_items:
        - { path: 'x', dest: 'y' }
        - { path: 'z', dest: 'k' }
    
    # touch a file, using symbolic modes to set the permissions (equivalent to 0644)
    - file: path=/etc/foo.conf state=touch mode="u=rw,g=r,o=r"
    
    # touch the same file, but add/remove some permissions
    - file: path=/etc/foo.conf state=touch mode="u+rw,g-wx,o-rwx"
    

.. note:: See also ``copy``, ``template``, ``assemble``


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

