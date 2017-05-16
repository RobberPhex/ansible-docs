.. _fetch:


fetch - Fetches a file from remote nodes
++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module works like :ref:`copy <copy>`, but in reverse. It is used for fetching files from remote machines and storing them locally in a file tree, organized by hostname. Note that this module is written to transfer log files that might not be present, so a missing remote file won't be an error unless fail_on_missing is set to 'yes'.




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
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A directory to save the file into. For example, if the <em>dest</em> directory is <code>/backup</code> a <em>src</em> file named <code>/etc/profile</code> on host <code>host.example.com</code>, would be saved into <code>/backup/host.example.com/etc/profile</code></div></td></tr>
            <tr>
    <td>fail_on_missing<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to 'yes', the task will fail if the source file is missing.</div></td></tr>
            <tr>
    <td>flat<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Allows you to override the default behavior of appending hostname/path/to/file to the destination.  If dest ends with '/', it will use the basename of the source file, similar to the copy module. Obviously this is only handy if the filenames are unique.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The file on the remote system to fetch. This <em>must</em> be a file, not a directory. Recursive fetching may be supported in a later release.</div></td></tr>
            <tr>
    <td>validate_checksum<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Verify that the source and destination checksums match after the files are fetched.</div></br>
        <div style="font-size: small;">aliases: validate_md5<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Store file into /tmp/fetched/host.example.com/tmp/somefile
    - fetch: src=/tmp/somefile dest=/tmp/fetched
    
    # Specifying a path directly
    - fetch: src=/tmp/somefile dest=/tmp/prefix-{{ inventory_hostname }} flat=yes
    
    # Specifying a destination path
    - fetch: src=/tmp/uniquefile dest=/tmp/special/ flat=yes
    
    # Storing in a path relative to the playbook
    - fetch: src=/tmp/uniquefile dest=special/prefix-{{ inventory_hostname }} flat=yes


Notes
-----

.. note:: When running fetch with ``become``, the :ref:`slurp <slurp>` module will also be used to fetch the contents of the file for determining the remote checksum. This effectively doubles the transfer size, and depending on the file size can consume all available memory on the remote or local hosts causing a ``MemoryError``. Due to this it is advisable to run this module without ``become`` whenever possible.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

