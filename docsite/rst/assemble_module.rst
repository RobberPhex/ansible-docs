.. _assemble:


assemble - Assembles a configuration file from fragments
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Assembles a configuration file from fragments. Often a particular program will take a single configuration file and does not support a ``conf.d`` style structure where it is easy to build up the configuration from multiple sources. ``assemble`` will take a directory of files that can be local or have already been transferred to the system, and concatenate them together to produce a destination file. Files are assembled in string sorting order. Puppet calls this idea *fragments*.

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
        <td>Create a backup file (if <code>yes</code>), including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.</td>
    </tr>
            <tr>
    <td>delimiter</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A delimiter to separate the file contents. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>A file to create using the concatenation of all of the source files.</td>
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
    <td>regexp</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Assemble files only if <code>regex</code> matches the filename. If not set, all files are assembled. All "\" (backslash) must be escaped as "\\" to comply yaml syntax. Uses Python regular expressions; see <a href='http://docs.python.org/2/library/re.html'>http://docs.python.org/2/library/re.html</a>.</td>
    </tr>
            <tr>
    <td>remote_src</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>If False, it will search for src at originating/master machine, if True it will go to the remote/target machine for the src. Default is True. (added in Ansible 1.4)</td>
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
        <td>An already existing directory full of source files.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example from Ansible Playbooks
    - assemble: src=/etc/someapp/fragments dest=/etc/someapp/someapp.conf
    
    # When a delimiter is specified, it will be inserted in between each fragment
    - assemble: src=/etc/someapp/fragments dest=/etc/someapp/someapp.conf delimiter='### START FRAGMENT ###'



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

