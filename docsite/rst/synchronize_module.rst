.. _synchronize:


synchronize - Uses rsync to make synchronizing file paths in your playbooks quick and easy.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

This is a wrapper around rsync. Of course you could just use the command action to call rsync yourself, but you also have to add a fair number of boilerplate options and host facts. You still may need to call rsync directly via ``command`` or ``shell`` depending on your use case. The synchronize action is meant to do common things with ``rsync`` easily. It does not provide access to the full power of rsync, but does make most invocations easier to follow.

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
    <td>archive</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Mirrors the rsync archive flag, enables recursive, links, perms, times, owner, group flags and -D.</td>
    </tr>
            <tr>
    <td>checksum</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Skip based on checksum, rather than mod-time &amp; size; Note that that "archive" option is still enabled by default - the "checksum" option will not disable it. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>compress</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Compress file data during the transfer. In most cases, leave this enabled unless it causes problems. (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>copy_links</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Copy symlinks as the item that they point to (the referent) is copied, rather than the symlink.</td>
    </tr>
            <tr>
    <td>delete</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Delete files that don't exist (after transfer, not before) in the <code>src</code> path. This option requires <code>recursive=yes</code>.</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path on the destination machine that will be synchronized from the source; The path can be absolute or relative.</td>
    </tr>
            <tr>
    <td>dest_port</td>
    <td>no</td>
    <td>22</td>
        <td><ul></ul></td>
        <td>Port number for ssh on the destination host. The ansible_ssh_port inventory var takes precedence over this value. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>dirs</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Transfer directories without recursing</td>
    </tr>
            <tr>
    <td>existing_only</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Skip creating new files on receiver. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>group</td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Preserve group</td>
    </tr>
            <tr>
    <td>links</td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Copy symlinks as symlinks.</td>
    </tr>
            <tr>
    <td>mode</td>
    <td>no</td>
    <td>push</td>
        <td><ul><li>push</li><li>pull</li></ul></td>
        <td>Specify the direction of the synchronization. In push mode the localhost or delegate is the source; In pull mode the remote host in context is the source.</td>
    </tr>
            <tr>
    <td>owner</td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Preserve owner (super user only)</td>
    </tr>
            <tr>
    <td>perms</td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Preserve permissions.</td>
    </tr>
            <tr>
    <td>recursive</td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Recurse into directories.</td>
    </tr>
            <tr>
    <td>rsync_opts</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specify additional rsync options by passing in an array. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>rsync_path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specify the rsync command to run on the remote machine. See <code>--rsync-path</code> on the rsync man page.</td>
    </tr>
            <tr>
    <td>rsync_timeout</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specify a --timeout for the rsync command in seconds.</td>
    </tr>
            <tr>
    <td>set_remote_user</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>put user@ for the remote paths. If you have a custom ssh config to define the remote user for a host that does not match the inventory user, you should set this parameter to "no".</td>
    </tr>
            <tr>
    <td>src</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path on the source machine that will be synchronized to the destination; The path can be absolute or relative.</td>
    </tr>
            <tr>
    <td>times</td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Preserve modification times</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Synchronization of src on the control machine to dest on the remote hosts
    synchronize: src=some/relative/path dest=/some/absolute/path
    
    # Synchronization without any --archive options enabled
    synchronize: src=some/relative/path dest=/some/absolute/path archive=no
    
    # Synchronization with --archive options enabled except for --recursive
    synchronize: src=some/relative/path dest=/some/absolute/path recursive=no
    
    # Synchronization with --archive options enabled except for --times, with --checksum option enabled
    synchronize: src=some/relative/path dest=/some/absolute/path checksum=yes times=no
    
    # Synchronization without --archive options enabled except use --links
    synchronize: src=some/relative/path dest=/some/absolute/path archive=no links=yes
    
    # Synchronization of two paths both on the control machine
    local_action: synchronize src=some/relative/path dest=/some/absolute/path
    
    # Synchronization of src on the inventory host to the dest on the localhost in
    pull mode
    synchronize: mode=pull src=some/relative/path dest=/some/absolute/path
    
    # Synchronization of src on delegate host to dest on the current inventory host.
    # If delegate_to is set to the current inventory host, this can be used to syncronize
    # two directories on that host. 
    synchronize: >
        src=some/relative/path dest=/some/absolute/path
        delegate_to: delegate.host
    
    # Synchronize and delete files in dest on the remote host that are not found in src of localhost.
    synchronize: src=some/relative/path dest=/some/absolute/path delete=yes
    
    # Synchronize using an alternate rsync command
    synchronize: src=some/relative/path dest=/some/absolute/path rsync_path="sudo rsync"
    
    # Example .rsync-filter file in the source directory
    - var       # exclude any path whose last part is 'var'
    - /var      # exclude any path starting with 'var' starting at the source directory
    + /var/conf # include /var/conf even though it was previously excluded
    
    # Synchronize passing in extra rsync options
    synchronize: src=/tmp/helloworld dest=/var/www/helloword rsync_opts=--no-motd,--exclude=.git 

.. note:: Inspect the verbose output to validate the destination user/host/path are what was expected.
.. note:: The remote user for the dest path will always be the remote_user, not the sudo_user.
.. note:: Expect that dest=~/x will be ~<remote_user>/x even if using sudo.
.. note:: To exclude files and directories from being synchronized, you may add ``.rsync-filter`` files to the source directory.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

