.. _win_file:


win_file - Creates, touches or removes files or directories.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates (empty) files, updates file modification stamps of existing files, and can create or remove directories. Unlike :ref:`file <file>`, does not modify ownership, permissions or manipulate links.




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
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the file being managed.  Aliases: <em>dest</em>, <em>name</em></div></br>
        <div style="font-size: small;">aliases: dest, name<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>directory</li><li>touch</li><li>absent</li></ul></td>
        <td><div>If <code>directory</code>, all immediate subdirectories will be created if they do not exist. If <code>file</code>, the file will NOT be created if it does not exist, see the <span class='module'>copy</span> or <span class='module'>template</span> module if you want that behavior.  If <code>absent</code>, directories will be recursively deleted, and files will be removed. If <code>touch</code>, an empty file will be created if the c(path) does not exist, while an existing file or directory will receive updated file access and modification times (similar to the way `touch` works from the command line).</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # create a file
    - win_file: path=C:\temp\foo.conf 
    
    # touch a file (creates if not present, updates modification time if present)
    - win_file: path=C:\temp\foo.conf state=touch 
    
    # remove a file, if present
    - win_file: path=C:\temp\foo.conf state=absent
    
    # create directory structure
    - win_file: path=C:\temp\folder\subfolder state=directory
    
    # remove directory structure
    - win_file: path=C:\temp state=absent


Notes
-----

.. note:: See also :ref:`win_copy <win_copy>`, :ref:`win_template <win_template>`, :ref:`copy <copy>`, :ref:`template <template>`, :ref:`assemble <assemble>`


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

