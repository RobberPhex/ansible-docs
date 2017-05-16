.. _unarchive:


unarchive - Unpacks an archive after (optionally) copying it from the local machine.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`unarchive <unarchive>` module unpacks an archive. By default, it will copy the source file from the local system to the target before unpacking - set copy=no to unpack an archive which already exists on the target..




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
    <td>copy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If true, the file is copied from local 'master' to the target machine, otherwise, the plugin will look for src archive at the target machine.</div></td></tr>
            <tr>
    <td>creates<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a filename, when it already exists, this step will <b>not</b> be run.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remote absolute path where the archive should be unpacked</div></td></tr>
            <tr>
    <td>exclude<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List the directory and file entries that you would like to exclude from the unarchive action.</div></td></tr>
            <tr>
    <td>extra_opts<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify additional options by passing in an array.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the group that should own the file/directory, as would be fed to <em>chown</em></div></td></tr>
            <tr>
    <td>keep_newer<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Do not replace existing files that are newer than files from the archive.</div></td></tr>
            <tr>
    <td>list_files<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set to True, return the list of files that are contained in the tarball.</div></td></tr>
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
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If copy=yes (default), local path to archive file to copy to the target server; can be absolute or relative. If copy=no, path on the target server to existing archive file to unpack.</div><div>If copy=no and src contains ://, the remote machine will download the file from the url first. (version_added 2.0)</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example from Ansible Playbooks
    - unarchive: src=foo.tgz dest=/var/lib/foo
    
    # Unarchive a file that is already on the remote machine
    - unarchive: src=/tmp/foo.zip dest=/usr/local/bin copy=no
    
    # Unarchive a file that needs to be downloaded (added in 2.0)
    - unarchive: src=https://example.com/example.zip dest=/usr/local/bin copy=no


Notes
-----

.. note:: requires ``gtar``/``unzip`` command on target host
.. note:: can handle *gzip*, *bzip2* and *xz* compressed as well as uncompressed tar files
.. note:: detects type of archive automatically
.. note:: uses gtar's ``--diff arg`` to calculate if changed or not. If this ``arg`` is not supported, it will always unpack the archive
.. note:: existing files/directories in the destination which are not in the archive are not touched.  This is the same behavior as a normal archive extraction
.. note:: existing files/directories in the destination which are not in the archive are ignored for purposes of deciding if the archive should be unpacked or not


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

