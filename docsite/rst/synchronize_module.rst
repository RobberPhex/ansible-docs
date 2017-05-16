.. _synchronize:


synchronize - Uses rsync to make synchronizing file paths in your playbooks quick and easy.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

``synchronize`` is a wrapper around the rsync command, meant to make common tasks with rsync easier. It is run and originates on the local host where Ansible is being run. Of course, you could just use the command action to call rsync yourself, but you also have to add a fair number of boilerplate options and host facts. You `still` may need to call rsync directly via ``command`` or ``shell`` depending on your use case. ``synchronize`` does not provide access to the full power of rsync, but does make most invocations easier to follow.




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
    <td>archive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Mirrors the rsync archive flag, enables recursive, links, perms, times, owner, group flags and -D.</div></td></tr>
            <tr>
    <td>checksum<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Skip based on checksum, rather than mod-time &amp; size; Note that that "archive" option is still enabled by default - the "checksum" option will not disable it.</div></td></tr>
            <tr>
    <td>compress<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Compress file data during the transfer. In most cases, leave this enabled unless it causes problems.</div></td></tr>
            <tr>
    <td>copy_links<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Copy symlinks as the item that they point to (the referent) is copied, rather than the symlink.</div></td></tr>
            <tr>
    <td>delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Delete files in <code>dest</code> that don't exist (after transfer, not before) in the <code>src</code> path. This option requires <code>recursive=yes</code>.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path on the destination host that will be synchronized from the source; The path can be absolute or relative.</div></td></tr>
            <tr>
    <td>dest_port<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>Value of ansible_ssh_port for this host, remote_port config setting, or the value from ssh client configuration if none of those are set</td>
        <td><ul></ul></td>
        <td><div>Port number for ssh on the destination host. Prior to ansible 2.0, the ansible_ssh_port inventory var took precedence over this value.</div></td></tr>
            <tr>
    <td>dirs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Transfer directories without recursing</div></td></tr>
            <tr>
    <td>existing_only<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Skip creating new files on receiver.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Preserve group</div></td></tr>
            <tr>
    <td>links<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Copy symlinks as symlinks.</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>push</td>
        <td><ul><li>push</li><li>pull</li></ul></td>
        <td><div>Specify the direction of the synchronization. In push mode the localhost or delegate is the source; In pull mode the remote host in context is the source.</div></td></tr>
            <tr>
    <td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Preserve owner (super user only)</div></td></tr>
            <tr>
    <td>partial<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Tells rsync to keep the partial file which should make a subsequent transfer of the rest of the file much faster.</div></td></tr>
            <tr>
    <td>perms<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Preserve permissions.</div></td></tr>
            <tr>
    <td>recursive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Recurse into directories.</div></td></tr>
            <tr>
    <td>rsync_opts<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify additional rsync options by passing in an array.</div></td></tr>
            <tr>
    <td>rsync_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the rsync command to run on the remote host. See <code>--rsync-path</code> on the rsync man page.</div></td></tr>
            <tr>
    <td>rsync_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify a --timeout for the rsync command in seconds.</div></td></tr>
            <tr>
    <td>set_remote_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>put user@ for the remote paths. If you have a custom ssh config to define the remote user for a host that does not match the inventory user, you should set this parameter to "no".</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path on the source host that will be synchronized to the destination; The path can be absolute or relative.</div></td></tr>
            <tr>
    <td>times<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>the value of the archive option</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Preserve modification times</div></td></tr>
            <tr>
    <td>use_ssh_args<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Use the ssh_args specified in ansible.cfg</div></td></tr>
            <tr>
    <td>verify_host<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Verify destination host key.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Synchronization of src on the control machine to dest on the remote hosts
    synchronize: src=some/relative/path dest=/some/absolute/path
    
    # Synchronization using rsync protocol (push)
    synchronize: src=some/relative/path/ dest=rsync://somehost.com/path/
    
    # Synchronization using rsync protocol (pull)
    synchronize: mode=pull src=rsync://somehost.com/path/ dest=/some/absolute/path/
    
    # Synchronization using rsync protocol on delegate host (push)
    synchronize: >
        src=/some/absolute/path/ dest=rsync://somehost.com/path/
        delegate_to: delegate.host
    
    # Synchronization using rsync protocol on delegate host (pull)
    synchronize: >
        mode=pull src=rsync://somehost.com/path/ dest=/some/absolute/path/
        delegate_to: delegate.host
    
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
    
    # Synchronization of src on the inventory host to the dest on the localhost in pull mode
    synchronize: mode=pull src=some/relative/path dest=/some/absolute/path
    
    # Synchronization of src on delegate host to dest on the current inventory host.
    synchronize:
        src: /first/absolute/path
        dest: /second/absolute/path
    delegate_to: delegate.host
    
    # Synchronize two directories on one remote host.
    synchronize:
        src: /first/absolute/path
        dest: /second/absolute/path
    delegate_to: "{{ inventory_hostname }}"
    
    # Synchronize and delete files in dest on the remote host that are not found in src of localhost.
    synchronize: src=some/relative/path dest=/some/absolute/path delete=yes recursive=yes
    
    # Synchronize using an alternate rsync command
    # This specific command is granted su privileges on the destination
    synchronize: src=some/relative/path dest=/some/absolute/path rsync_path="su -c rsync"
    
    # Example .rsync-filter file in the source directory
    - var       # exclude any path whose last part is 'var'
    - /var      # exclude any path starting with 'var' starting at the source directory
    + /var/conf # include /var/conf even though it was previously excluded
    
    # Synchronize passing in extra rsync options
    synchronize:
        src: /tmp/helloworld
        dest: /var/www/helloworld
        rsync_opts:
          - "--no-motd"
          - "--exclude=.git"


Notes
-----

.. note:: rsync must be installed on both the local and remote host.
.. note:: For the ``synchronize`` module, the "local host" is the host `the synchronize task originates on`, and the "destination host" is the host `synchronize is connecting to`.
.. note:: The "local host" can be changed to a different host by using `delegate_to`.  This enables copying between two remote hosts or entirely on one remote machine.
.. note:: The user and permissions for the synchronize `src` are those of the user running the Ansible task on the local host (or the remote_user for a delegate_to host when delegate_to is used).
.. note:: The user and permissions for the synchronize `dest` are those of the `remote_user` on the destination host or the `become_user` if `become=yes` is active.
.. note:: In 2.0.0.0 a bug in the synchronize module made become occur on the "local host".  This was fixed in 2.0.1.
.. note:: Expect that dest=~/x will be ~<remote_user>/x even if using sudo.
.. note:: Inspect the verbose output to validate the destination user/host/path are what was expected.
.. note:: To exclude files and directories from being synchronized, you may add ``.rsync-filter`` files to the source directory.
.. note:: rsync daemon must be up and running with correct permission when using rsync protocol in source or destination path.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

