.. _win_file:


win_file - Creates, touches or removes files or directories.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates (empty) files, updates file modification stamps of existing files, and can create or remove directories.
* Unlike :ref:`file <file>`, does not modify ownership, permissions or manipulate links.




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
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>path to the file being managed.  Aliases: <em>dest</em>, <em>name</em></div></br>
    <div style="font-size: small;">aliases: dest, name<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>file</li><li>directory</li><li>touch</li><li>absent</li></ul></td>
        <td><div>If <code>directory</code>, all immediate subdirectories will be created if they do not exist. If <code>file</code>, the file will NOT be created if it does not exist, see the <span class='module'>copy</span> or <span class='module'>template</span> module if you want that behavior.  If <code>absent</code>, directories will be recursively deleted, and files will be removed. If <code>touch</code>, an empty file will be created if the <code>path</code> does not exist, while an existing file or directory will receive updated file access and modification times (similar to the way <code>touch</code> works from the command line).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a file
      win_file:
        path: C:\Temp\foo.conf
        state: file
    
    - name: Touch a file (creates if not present, updates modification time if present)
      win_file:
        path: C:\Temp\foo.conf
        state: touch
    
    - name: Remove a file, if present
      win_file:
        path: C:\Temp\foo.conf
        state: absent
    
    - name: Create directory structure
      win_file:
        path: C:\Temp\folder\subfolder
        state: directory
    
    - name: Remove directory structure
      win_file:
        path: C:\Temp
        state: absent


Notes
-----

.. note::
    - See also :ref:`win_copy <win_copy>`, :ref:`win_template <win_template>`, :ref:`copy <copy>`, :ref:`template <template>`, :ref:`assemble <assemble>`



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
