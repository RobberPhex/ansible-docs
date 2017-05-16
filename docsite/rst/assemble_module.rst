.. _assemble:


assemble - Assembles a configuration file from fragments
++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Assembles a configuration file from fragments. Often a particular program will take a single configuration file and does not support a ``conf.d`` style structure where it is easy to build up the configuration from multiple sources. :ref:`assemble <assemble>` will take a directory of files that can be local or have already been transferred to the system, and concatenate them together to produce a destination file. Files are assembled in string sorting order. Puppet calls this idea *fragments*.




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
        <td><div>Create a backup file (if <code>yes</code>), including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.</div></td></tr>
            <tr>
    <td>delimiter<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A delimiter to separate the file contents.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A file to create using the concatenation of all of the source files.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the group that should own the file/directory, as would be fed to <em>chown</em></div></td></tr>
            <tr>
    <td>ignore_hidden<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A boolean that controls if files that start with a '.' will be included or not.</div></td></tr>
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
    <td>regexp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Assemble files only if <code>regex</code> matches the filename. If not set, all files are assembled. All "\" (backslash) must be escaped as "\\" to comply yaml syntax. Uses Python regular expressions; see <a href='http://docs.python.org/2/library/re.html'>http://docs.python.org/2/library/re.html</a>.</div></td></tr>
            <tr>
    <td>remote_src<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If False, it will search for src at originating/master machine, if True it will go to the remote/target machine for the src. Default is True.</div></td></tr>
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
        <td><div>An already existing directory full of source files.</div></td></tr>
            <tr>
    <td>unsafe_writes<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Normally this module uses atomic operations to prevent data corruption or inconsistent reads from the target files, sometimes systems are configured or just broken in ways that prevent this. One example are docker mounted files, they cannot be updated atomically and can only be done in an unsafe manner.</div><div>This boolean option allows ansible to fall back to unsafe methods of updating files for those cases in which you do not have any other choice. Be aware that this is subject to race conditions and can lead to data corruption.</div></td></tr>
            <tr>
    <td>validate<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The validation command to run before copying into place.  The path to the file to validate is passed in via '%s' which must be present as in the sshd example below. The command is passed securely so shell features like expansion and pipes won't work.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example from Ansible Playbooks
    - assemble: src=/etc/someapp/fragments dest=/etc/someapp/someapp.conf
    
    # When a delimiter is specified, it will be inserted in between each fragment
    - assemble: src=/etc/someapp/fragments dest=/etc/someapp/someapp.conf delimiter='### START FRAGMENT ###'
    
    # Copy a new "sshd_config" file into place, after passing validation with sshd
    - assemble: src=/etc/ssh/conf.d/ dest=/etc/ssh/sshd_config validate='/usr/sbin/sshd -t -f %s'




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

