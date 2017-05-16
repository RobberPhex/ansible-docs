.. _fetch:


fetch - Fetches a file from remote nodes
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


This module works like ``copy``, but in reverse. It is used for fetching files from remote machines and storing them locally in a file tree, organized by hostname. Note that this module is written to transfer log files that might not be present, so a missing remote file won't be an error unless fail_on_missing is set to 'yes'.

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
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>A directory to save the file into. For example, if the <em>dest</em> directory is <code>/backup</code> a <em>src</em> file named <code>/etc/profile</code> on host <code>host.example.com</code>, would be saved into <code>/backup/host.example.com/etc/profile</code></td>
    </tr>
            <tr>
    <td>fail_on_missing</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Makes it fails when the source file is missing. (added in Ansible 1.1)</td>
    </tr>
            <tr>
    <td>flat</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Allows you to override the default behavior of prepending hostname/path/to/file to the destination.  If dest ends with '/', it will use the basename of the source file, similar to the copy module. Obviously this is only handy if the filenames are unique. (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>src</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The file on the remote system to fetch. This <em>must</em> be a file, not a directory. Recursive fetching may be supported in a later release.</td>
    </tr>
            <tr>
    <td>validate_checksum</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Verify that the source and destination checksums match after the files are fetched. (added in Ansible 1.4)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Store file into /tmp/fetched/host.example.com/tmp/somefile
    - fetch: src=/tmp/somefile dest=/tmp/fetched
    
    # Specifying a path directly
    - fetch: src=/tmp/somefile dest=/tmp/prefix-{{ ansible_hostname }} flat=yes
    
    # Specifying a destination path
    - fetch: src=/tmp/uniquefile dest=/tmp/special/ flat=yes
    
    # Storing in a path relative to the playbook
    - fetch: src=/tmp/uniquefile dest=special/prefix-{{ ansible_hostname }} flat=yes



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

