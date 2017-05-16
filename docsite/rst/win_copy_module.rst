.. _win_copy:


win_copy - Copies files to remote locations on windows hosts.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9.2

The ``win_copy`` module copies a file on the local box to remote windows locations.

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
        <td>Remote absolute path where the file should be copied to. If src is a directory, this must be a directory too. Use \ for path separators.</td>
    </tr>
            <tr>
    <td>src</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Local path to a file to copy to the remote server; can be absolute or relative. If path is a directory, it is copied recursively. In this case, if path ends with "/", only inside contents of that directory are copied to destination. Otherwise, if it does not end with "/", the directory itself with all contents is copied. This behavior is similar to Rsync.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Copy a single file
    - win_copy: src=/srv/myfiles/foo.conf dest=c:\TEMP\foo.conf
    
    # Copy the contents of files/temp_files dir into c:	emp\.  Includes any sub dirs under files/temp_files
    # Note the use of unix style path in the dest.  
    # This is necessary because \ is yaml escape sequence
    - win_copy: src=files/temp_files/ dest=c:/temp/
    
    # Copy the files/temp_files dir and any files or sub dirs into c:	emp
    # Copies the folder because there is no trailing / on 'files/temp_files'
    - win_copy: src=files/temp_files dest=c:/temp/
    

.. note:: The "win_copy" module is best used for small files only. This module should **not** be used for files bigger than 3Mb as this will result in a 500 response from the winrm host and it will not be possible to connect via winrm again until the windows remote management service has been restarted on the windows host. Files larger than 1Mb will take minutes to transfer. The recommended way to transfer large files is using win_get_url or collecting from a windows file share folder.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

