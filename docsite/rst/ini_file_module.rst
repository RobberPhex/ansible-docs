.. _ini_file:


ini_file - Tweak settings in INI files
++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Manage (add, remove, change) individual settings in an INI-style file without having to manage the file as a whole with, say, ``template`` or ``assemble``. Adds missing sections if they don't exist.
Comments are discarded when the source file is read, and therefore will not show up in the destination file.

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
        <td>Path to the INI-style file; this file is created if required</td>
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
    <td>option</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>if set (required for changing a <em>value</em>), this is the name of the option.May be omitted if adding/removing a whole <em>section</em>.</td>
    </tr>
            <tr>
    <td>others</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>all arguments accepted by the <span class='module'>file</span> module also work here</td>
    </tr>
            <tr>
    <td>owner</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the user that should own the file/directory, as would be fed to <em>chown</em></td>
    </tr>
            <tr>
    <td>section</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Section name in INI file. This is added if <code>state=present</code> automatically when a single value is being set.</td>
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
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>If set to <code>absent</code> the option or section will be removed if present instead of created.</td>
    </tr>
            <tr>
    <td>value</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the string value to be associated with an <em>option</em>. May be omitted when removing an <em>option</em>.</td>
    </tr>
        </table>


.. note:: Requires ConfigParser


Examples
--------

.. raw:: html

    <br/>


::

    # Ensure "fav=lemonade is in section "[drinks]" in specified file
    - ini_file: dest=/etc/conf section=drinks option=fav value=lemonade mode=0600 backup=yes
    
    - ini_file: dest=/etc/anotherconf
                section=drinks
                option=temperature
                value=cold
                backup=yes

.. note:: While it is possible to add an *option* without specifying a *value*, this makes no sense.
.. note:: A section named ``default`` cannot be added by the module, but if it exists, individual options within the section can be updated. (This is a limitation of Python's *ConfigParser*.) Either use ``template`` to create a base INI file with a ``[default]`` section, or use ``lineinfile`` to add the missing line.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

