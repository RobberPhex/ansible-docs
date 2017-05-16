.. _template:


template - Templates a file out to a remote server.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Templates are processed by the Jinja2 templating language (http://jinja.pocoo.org/docs/) - documentation on the template formatting can be found in the Template Designer Documentation (http://jinja.pocoo.org/docs/templates/).
Six additional variables can be used in templates: ``ansible_managed`` (configurable via the ``defaults`` section of ``ansible.cfg``) contains a string which can be used to describe the template name, host, modification time of the template file and the owner uid, ``template_host`` contains the node name of the template's machine, ``template_uid`` the owner, ``template_path`` the absolute path of the template, ``template_fullpath`` is the absolute path of the template, and ``template_run_date`` is the date that the template was rendered. Note that including a string that uses a date in the template will result in the template being marked 'changed' each time.

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
    <td>backup</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Create a backup file including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Location to render the template to on the remote machine.</td>
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
        <td>Path of a Jinja2 formatted template on the local server. This can be a relative or absolute path.</td>
    </tr>
            <tr>
    <td>validate</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The validation command to run before copying into place.The path to the file to validate is passed in via '%s' which must be present as in the visudo example below.validation to run before copying into place. The command is passed securely so shell features like expansion and pipes won't work. (added in Ansible 1.2)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example from Ansible Playbooks
    - template: src=/mytemplates/foo.j2 dest=/etc/file.conf owner=bin group=wheel mode=0644
    
    # The same example, but using symbolic modes equivalent to 0644
    - template: src=/mytemplates/foo.j2 dest=/etc/file.conf owner=bin group=wheel mode="u=rw,g=r,o=r"
    
    # Copy a new "sudoers" file into place, after passing validation with visudo
    - template: src=/mine/sudoers dest=/etc/sudoers validate='visudo -cf %s'

.. note:: Since Ansible version 0.9, templates are loaded with ``trim_blocks=True``.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

