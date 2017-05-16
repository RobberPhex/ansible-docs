.. _lineinfile:


lineinfile - Ensure a particular line is in a file, or replace an existing line using a back-referenced regular expression.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module will search a file for a line, and ensure that it is present or absent.
* This is primarily useful when you want to change a single line in a file only. See the :ref:`replace <replace>` module if you want to change multiple, similar lines or check :ref:`blockinfile <blockinfile>` if you want to insert/update/remove a block of lines in a file. For other cases, see the :ref:`copy <copy>` or :ref:`template <template>` modules.




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
                <tr><td>backrefs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Used with <code>state=present</code>. If set, line can contain backreferences (both positional and named) that will get populated if the <code>regexp</code> matches. This flag changes the operation of the module slightly; <code>insertbefore</code> and <code>insertafter</code> will be ignored, and if the <code>regexp</code> doesn't match anywhere in the file, the file will be left unchanged. If the <code>regexp</code> does match, the last matching line will be replaced by the expanded line parameter.</div>        </td></tr>
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Create a backup file including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.</div>        </td></tr>
                <tr><td>create<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the file will be created if it does not already exist. By default it will fail if the file is missing.</div>        </td></tr>
                <tr><td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the group that should own the file/directory, as would be fed to <em>chown</em>.</div>        </td></tr>
                <tr><td>insertafter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>EOF</td>
        <td><ul><li>EOF</li><li>*regex*</li></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the line will be inserted after the last match of specified regular expression. A special value is available; <code>EOF</code> for inserting the line at the end of the file. If specified regular expression has no matches, EOF will be used instead. May not be used with <code>backrefs</code>.</div>        </td></tr>
                <tr><td>insertbefore<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>BOF</li><li>*regex*</li></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the line will be inserted before the last match of specified regular expression. A value is available; <code>BOF</code> for inserting the line at the beginning of the file. If specified regular expression has no matches, the line will be inserted at the end of the file.  May not be used with <code>backrefs</code>.</div>        </td></tr>
                <tr><td>line<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Required for <code>state=present</code>. The line to insert/replace into the file. If <code>backrefs</code> is set, may contain backreferences that will get expanded with the <code>regexp</code> capture groups if the regexp matches.</div>        </td></tr>
                <tr><td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Mode the file or directory should be. For those used to <em>/usr/bin/chmod</em> remember that modes are actually octal numbers (like 0644). Leaving off the leading zero will likely have unexpected results. As of version 1.8, the mode may be specified as a symbolic mode (for example, <code>u+rwx</code> or <code>u=rw,g=r,o=r</code>).</div>        </td></tr>
                <tr><td>others<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>All arguments accepted by the <span class='module'>file</span> module also work here.</div>        </td></tr>
                <tr><td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the user that should own the file/directory, as would be fed to <em>chown</em>.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The file to modify.</div><div>Before 2.3 this option was only usable as <em>dest</em>, <em>destfile</em> and <em>name</em>.</div></br>
    <div style="font-size: small;">aliases: dest, destfile, name<div>        </td></tr>
                <tr><td>regexp<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The regular expression to look for in every line of the file. For <code>state=present</code>, the pattern to replace if found; only the last line found will be replaced. For <code>state=absent</code>, the pattern of the line to remove.  Uses Python regular expressions; see <a href='http://docs.python.org/2/library/re.html'>http://docs.python.org/2/library/re.html</a>.</div>        </td></tr>
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
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the line should be there or not.</div>        </td></tr>
                <tr><td>unsafe_writes<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Normally this module uses atomic operations to prevent data corruption or inconsistent reads from the target files, sometimes systems are configured or just broken in ways that prevent this. One example are docker mounted files, they cannot be updated atomically and can only be done in an unsafe manner.</div><div>This boolean option allows ansible to fall back to unsafe methods of updating files for those cases in which you do not have any other choice. Be aware that this is subject to race conditions and can lead to data corruption.</div>        </td></tr>
                <tr><td>validate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The validation command to run before copying into place. The path to the file to validate is passed in via '%s' which must be present as in the example below. The command is passed securely so shell features like expansion and pipes won't work.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Before 2.3, option 'dest', 'destfile' or 'name' was used instead of 'path'
    - lineinfile:
        path: /etc/selinux/config
        regexp: '^SELINUX='
        line: 'SELINUX=enforcing'
    
    - lineinfile:
        path: /etc/sudoers
        state: absent
        regexp: '^%wheel'
    
    - lineinfile:
        path: /etc/hosts
        regexp: '^127\.0\.0\.1'
        line: '127.0.0.1 localhost'
        owner: root
        group: root
        mode: 0644
    
    - lineinfile:
        path: /etc/httpd/conf/httpd.conf
        regexp: '^Listen '
        insertafter: '^#Listen '
        line: 'Listen 8080'
    
    - lineinfile:
        path: /etc/services
        regexp: '^# port for http'
        insertbefore: '^www.*80/tcp'
        line: '# port for http by default'
    
    # Add a line to a file if it does not exist, without passing regexp
    - lineinfile:
        path: /tmp/testfile
        line: '192.168.1.99 foo.lab.net foo'
    
    # Fully quoted because of the ': ' on the line. See the Gotchas in the YAML docs.
    - lineinfile:
        path: /etc/sudoers
        state: present
        regexp: '^%wheel\s'
        line: '%wheel ALL=(ALL) NOPASSWD: ALL'
    
    # Yaml requires escaping backslashes in double quotes but not in single quotes
    - lineinfile:
        path: /opt/jboss-as/bin/standalone.conf
        regexp: '^(.*)Xms(\\d+)m(.*)$'
        line: '\1Xms${xms}m\3'
        backrefs: yes
    
    # Validate the sudoers file before saving
    - lineinfile:
        path: /etc/sudoers
        state: present
        regexp: '^%ADMIN ALL='
        line: '%ADMIN ALL=(ALL) NOPASSWD: ALL'
        validate: 'visudo -cf %s'


Notes
-----

.. note::
    - As of Ansible 2.3, the *dest* option has been changed to *path* as default, but *dest* still works as well.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
