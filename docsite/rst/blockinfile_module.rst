.. _blockinfile:


blockinfile - Insert/update/remove a text block surrounded by marker lines.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module will insert/update/remove a block of multi-line text surrounded by customizable marker lines.




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
    <td>block<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The text to insert inside the marker lines. If it's missing or an empty string, the block will be removed as if <code>state</code> were specified to <code>absent</code>.</div></br>
        <div style="font-size: small;">aliases: content<div></td></tr>
            <tr>
    <td>create<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Create a new file if it doesn't exist.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The file to modify.</div></br>
        <div style="font-size: small;">aliases: name, destfile<div></td></tr>
            <tr>
    <td>follow<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This flag indicates that filesystem links, if they exist, should be followed.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the group that should own the file/directory, as would be fed to <em>chown</em></div></td></tr>
            <tr>
    <td>insertafter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>EOF</td>
        <td><ul><li>EOF</li><li>*regex*</li></ul></td>
        <td><div>If specified, the block will be inserted after the last match of specified regular expression. A special value is available; <code>EOF</code> for inserting the block at the end of the file.  If specified regular expresion has no matches, <code>EOF</code> will be used instead.</div></td></tr>
            <tr>
    <td>insertbefore<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>BOF</li><li>*regex*</li></ul></td>
        <td><div>If specified, the block will be inserted before the last match of specified regular expression. A special value is available; <code>BOF</code> for inserting the block at the beginning of the file.  If specified regular expresion has no matches, the block will be inserted at the end of the file.</div></td></tr>
            <tr>
    <td>marker<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td># {mark} ANSIBLE MANAGED BLOCK</td>
        <td><ul></ul></td>
        <td><div>The marker line template. "{mark}" will be replaced with "BEGIN" or "END".</div></td></tr>
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
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the block should be there or not.</div></td></tr>
            <tr>
    <td>unsafe_writes<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Normally this module uses atomic operations to prevent data corruption or inconsistent reads from the target files, sometimes systems are configured or just broken in ways that prevent this. One example are docker mounted files, they cannot be updated atomically and can only be done in an unsafe manner.</div><div>This boolean option allows ansible to fall back to unsafe methods of updating files for those cases in which you do not have any other choice. Be aware that this is subject to race conditions and can lead to data corruption.</div></td></tr>
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

    - name: insert/update "Match User" configuation block in /etc/ssh/sshd_config
      blockinfile:
        dest: /etc/ssh/sshd_config
        block: |
          Match User ansible-agent
          PasswordAuthentication no
    
    - name: insert/update eth0 configuration stanza in /etc/network/interfaces
            (it might be better to copy files into /etc/network/interfaces.d/)
      blockinfile:
        dest: /etc/network/interfaces
        block: |
          iface eth0 inet static
              address 192.0.2.23
              netmask 255.255.255.0
    
    - name: insert/update HTML surrounded by custom markers after <body> line
      blockinfile:
        dest: /var/www/html/index.html
        marker: "<!-- {mark} ANSIBLE MANAGED BLOCK -->"
        insertafter: "<body>"
        content: |
          <h1>Welcome to {{ansible_hostname}}</h1>
          <p>Last updated on {{ansible_date_time.iso8601}}</p>
    
    - name: remove HTML as well as surrounding markers
      blockinfile:
        dest: /var/www/html/index.html
        marker: "<!-- {mark} ANSIBLE MANAGED BLOCK -->"
        content: ""
    
    - name: Add mappings to /etc/hosts
      blockinfile:
        dest: /etc/hosts
        block: |
          {{item.ip}} {{item.name}}
        marker: "# {mark} ANSIBLE MANAGED BLOCK {{item.name}}"
      with_items:
          - { name: host1, ip: 10.10.1.10 }
          - { name: host2, ip: 10.10.1.11 }
          - { name: host3, ip: 10.10.1.12 }


Notes
-----

.. note:: This module supports check mode.
.. note:: When using 'with_*' loops be aware that if you do not set a unique mark the block will be overwritten on each iteration.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

