.. _patch:


patch - Apply patch files using the GNU patch tool.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Apply patch files using the GNU patch tool.




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
    <td>backup<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>passes --backup --version-control=numbered to patch, producing numbered backup copies</div></td></tr>
            <tr>
    <td>basedir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path of a base directory in which the patch file will be applied. May be ommitted when <code>dest</code> option is specified, otherwise required.</div></td></tr>
            <tr>
    <td>binary<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Setting to <code>yes</code> will disable patch's heuristic for transforming CRLF line endings into LF. Line endings of src and dest must match. If set to <code>no</code>, patch will replace CRLF in src files on POSIX.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path of the file on the remote machine to be patched.</div><div>The names of the files to be patched are usually taken from the patch file, but if there's just one file to be patched it can specified with this option.</div></br>
        <div style="font-size: small;">aliases: originalfile<div></td></tr>
            <tr>
    <td>remote_src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, it will search for src at originating/master machine, if <code>yes</code> it will go to the remote/target machine for the src. Default is <code>no</code>.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path of the patch file as accepted by the GNU patch tool. If <code>remote_src</code> is 'no', the patch source file is looked up from the module's "files" directory.</div></br>
        <div style="font-size: small;">aliases: patchfile<div></td></tr>
            <tr>
    <td>strip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul></ul></td>
        <td><div>Number that indicates the smallest prefix containing leading slashes that will be stripped from each file name found in the patch file. For more information see the strip parameter of the GNU patch tool.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: apply patch to one file
      patch: >
        src=/tmp/index.html.patch
        dest=/var/www/index.html
    
    - name: apply patch to multiple files under basedir
      patch: >
        src=/tmp/customize.patch
        basedir=/var/www
        strip=1




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

