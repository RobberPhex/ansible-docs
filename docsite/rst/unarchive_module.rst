.. _unarchive:


unarchive - Unpacks an archive after (optionally) copying it from the local machine.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

The ``unarchive`` module unpacks an archive. By default, it will copy the source file from the local system to the target before unpacking - set copy=no to unpack an archive which already exists on the target..

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
    <td>copy</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If true, the file is copied from local 'master' to the target machine, otherwise, the plugin will look for src archive at the target machine.</td>
    </tr>
            <tr>
    <td>creates</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a filename, when it already exists, this step will <b>not</b> be run. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Remote absolute path where the archive should be unpacked</td>
    </tr>
            <tr>
    <td>follow</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>This flag indicates that filesystem links, if they exist, should be followed. (added in Ansible 1.8)</td>
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
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>If copy=yes (default), local path to archive file to copy to the target server; can be absolute or relative. If copy=no, path on the target server to existing archive file to unpack.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example from Ansible Playbooks
    - unarchive: src=foo.tgz dest=/var/lib/foo
    
    # Unarchive a file that is already on the remote machine
    - unarchive: src=/tmp/foo.zip dest=/usr/local/bin copy=no

.. note:: requires ``tar``/``unzip`` command on target host
.. note:: can handle *gzip*, *bzip2* and *xz* compressed as well as uncompressed tar files
.. note:: detects type of archive automatically
.. note:: uses tar's ``--diff arg`` to calculate if changed or not. If this ``arg`` is not supported, it will always unpack the archive
.. note:: does not detect if a .zip file is different from destination - always unzips
.. note:: existing files/directories in the destination which are not in the archive are not touched.  This is the same behavior as a normal archive extraction
.. note:: existing files/directories in the destination which are not in the archive are ignored for purposes of deciding if the archive should be unpacked or not


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

