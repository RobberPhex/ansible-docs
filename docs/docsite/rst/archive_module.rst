.. _archive:


archive - Creates a compressed archive of one or more files or trees.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Packs an archive. It is the opposite of :ref:`unarchive <unarchive>`. By default, it assumes the compression source exists on the target. It will not copy the source file from the local system to the target before archiving. Source files can be deleted after archival by specifying *remove=True*.




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
                <tr><td>attributes<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Attributes the file or directory should have. To get supported flags look at the man page for <em>chattr</em> on the target system. This string should contain the attributes in the same order as the one displayed by <em>lsattr</em>.</div></br>
    <div style="font-size: small;">aliases: attr<div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The file name of the destination archive. This is required when <code>path</code> refers to multiple files by either specifying a glob, a directory or multiple paths in a list.</div>        </td></tr>
                <tr><td>format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>gz</td>
        <td><ul><li>gz</li><li>bz2</li><li>zip</li></ul></td>
        <td><div>The type of compression to use.</div>        </td></tr>
                <tr><td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the group that should own the file/directory, as would be fed to <em>chown</em>.</div>        </td></tr>
                <tr><td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Mode the file or directory should be. For those used to <em>/usr/bin/chmod</em> remember that modes are actually octal numbers (like 0644). Leaving off the leading zero will likely have unexpected results. As of version 1.8, the mode may be specified as a symbolic mode (for example, <code>u+rwx</code> or <code>u=rw,g=r,o=r</code>).</div>        </td></tr>
                <tr><td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the user that should own the file/directory, as would be fed to <em>chown</em>.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Remote absolute path, glob, or list of paths or globs for the file or files to compress or archive.</div>        </td></tr>
                <tr><td>remove<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Remove any added source files and trees after adding to archive.</div>        </td></tr>
                <tr><td>selevel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>s0</td>
        <td></td>
        <td><div>Level part of the SELinux file context. This is the MLS/MCS attribute, sometimes known as the <code>range</code>. <code>_default</code> feature works as for <em>seuser</em>.</div>        </td></tr>
                <tr><td>serole<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Role part of SELinux file context, <code>_default</code> feature works as for <em>seuser</em>.</div>        </td></tr>
                <tr><td>setype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Type part of SELinux file context, <code>_default</code> feature works as for <em>seuser</em>.</div>        </td></tr>
                <tr><td>seuser<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User part of SELinux file context. Will default to system policy, if applicable. If set to <code>_default</code>, it will use the <code>user</code> portion of the policy if available.</div>        </td></tr>
                <tr><td>unsafe_writes<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Normally this module uses atomic operations to prevent data corruption or inconsistent reads from the target files, sometimes systems are configured or just broken in ways that prevent this. One example are docker mounted files, they cannot be updated atomically and can only be done in an unsafe manner.</div><div>This boolean option allows ansible to fall back to unsafe methods of updating files for those cases in which you do not have any other choice. Be aware that this is subject to race conditions and can lead to data corruption.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Compress directory /path/to/foo/ into /path/to/foo.tgz
    - archive:
        path: /path/to/foo
        dest: /path/to/foo.tgz
    
    # Compress regular file /path/to/foo into /path/to/foo.gz and remove it
    - archive:
        path: /path/to/foo
        remove: True
    
    # Create a zip archive of /path/to/foo
    - archive:
        path: /path/to/foo
        format: zip
    
    # Create a bz2 archive of multiple files, rooted at /path
    - archive:
        path:
            - /path/to/foo
            - /path/wong/foo
        dest: /path/file.tar.bz2
        format: bz2

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
        <td> state </td>
        <td> The current state of the archived file. If 'absent', then no source files were found and the archive does not exist. If 'compress', then the file source file is in the compressed state. If 'archive', then the source file or paths are currently archived. If 'incomplete', then an archive was created, but not all source paths were found. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> missing </td>
        <td> Any files that were missing from the source. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> expanded_paths </td>
        <td> The list of matching paths from paths argument. </td>
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> archived </td>
        <td> Any files that were compressed or added to the archive. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> arcroot </td>
        <td> The archive root. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - requires tarfile, zipfile, gzip, and bzip2 packages on target host
    - can produce *gzip*, *bzip2* and *zip* compressed files or archives



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
