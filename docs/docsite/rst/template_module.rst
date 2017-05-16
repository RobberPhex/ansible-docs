.. _template:


template - Templates a file out to a remote server.
+++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Templates are processed by the Jinja2 templating language (http://jinja.pocoo.org/docs/) - documentation on the template formatting can be found in the Template Designer Documentation (http://jinja.pocoo.org/docs/templates/).
* Six additional variables can be used in templates: ``ansible_managed`` (configurable via the ``defaults`` section of ``ansible.cfg``) contains a string which can be used to describe the template name, host, modification time of the template file and the owner uid. ``template_host`` contains the node name of the template's machine. ``template_uid`` the numeric user id of the owner. ``template_path`` the path of the template. ``template_fullpath`` is the absolute path of the template. ``template_run_date`` is the date that the template was rendered.




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
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Create a backup file including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.</div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Location to render the template to on the remote machine.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>the default is <code>yes</code>, which will replace the remote file when contents are different than the source.  If <code>no</code>, the file will only be transferred if the destination does not exist.</div>        </td></tr>
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
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Path of a Jinja2 formatted template on the Ansible controller. This can be a relative or absolute path.</div>        </td></tr>
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

    # Example from Ansible Playbooks
    - template:
        src: /mytemplates/foo.j2
        dest: /etc/file.conf
        owner: bin
        group: wheel
        mode: 0644
    
    # The same example, but using symbolic modes equivalent to 0644
    - template:
        src: /mytemplates/foo.j2
        dest: /etc/file.conf
        owner: bin
        group: wheel
        mode: "u=rw,g=r,o=r"
    
    # Copy a new "sudoers" file into place, after passing validation with visudo
    - template:
        src: /mine/sudoers
        dest: /etc/sudoers
        validate: 'visudo -cf %s'
    
    # Update sshd configuration safely, avoid locking yourself out
    - template:
        src: etc/ssh/sshd_config.j2
        dest: /etc/ssh/sshd_config
        owner: root
        group: root
        mode: '0600'
        validate: /usr/sbin/sshd -t -f %s
        backup: yes


Notes
-----

.. note::
    - Including a string that uses a date in the template will result in the template being marked 'changed' each time
    - Since Ansible version 0.9, templates are loaded with ``trim_blocks=True``.
    - Also, you can override jinja2 settings by adding a special header to template file. i.e. ``#jinja2:variable_start_string:'[%' , variable_end_string:'%]', trim_blocks: False`` which changes the variable interpolation markers to  [% var %] instead of  {{ var }}. This is the best way to prevent evaluation of things that look like, but should not be Jinja2. raw/endraw in Jinja2 will not work as you expect because templates in Ansible are recursively evaluated.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
