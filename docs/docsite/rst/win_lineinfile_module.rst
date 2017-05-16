.. _win_lineinfile:


win_lineinfile - Ensure a particular line is in a file, or replace an existing line using a back-referenced regular expression.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module will search a file for a line, and ensure that it is present or absent.
* This is primarily useful when you want to change a single line in a file only.




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
                <tr><td>backrefs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Used with <code>state=present</code>. If set, line can contain backreferences (both positional and named) that will get populated if the <code>regexp</code> matches. This flag changes the operation of the module slightly; <code>insertbefore</code> and <code>insertafter</code> will be ignored, and if the <code>regexp</code> doesn't match anywhere in the file, the file will be left unchanged.</div><div>If the <code>regexp</code> does match, the last matching line will be replaced by the expanded line parameter.</div>        </td></tr>
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Create a backup file including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.</div>        </td></tr>
                <tr><td>create<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the file will be created if it does not already exist. By default it will fail if the file is missing.</div>        </td></tr>
                <tr><td>encoding<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>auto</td>
        <td></td>
        <td><div>Specifies the encoding of the source text file to operate on (and thus what the output encoding will be). The default of <code>auto</code> will cause the module to auto-detect the encoding of the source file and ensure that the modified file is written with the same encoding.</div><div>An explicit encoding can be passed as a string that is a valid value to pass to the .NET framework System.Text.Encoding.GetEncoding() method - see <a href='https://msdn.microsoft.com/en-us/library/system.text.encoding%28v=vs.110%29.aspx'>https://msdn.microsoft.com/en-us/library/system.text.encoding%28v=vs.110%29.aspx</a>.</div><div>This is mostly useful with <code>create=yes</code> if you want to create a new file with a specific encoding. If <code>create=yes</code> is specified without a specific encoding, the default encoding (UTF-8, no BOM) will be used.</div>        </td></tr>
                <tr><td>insertafter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>EOF</td>
        <td><ul><li>EOF</li><li>*regex*</li></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the line will be inserted after the last match of specified regular expression. A special value is available; <code>EOF</code> for inserting the line at the end of the file.</div><div>If specified regular expression has no matches, EOF will be used instead. May not be used with <code>backrefs</code>.</div>        </td></tr>
                <tr><td>insertbefore<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>BOF</li><li>*regex*</li></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the line will be inserted before the last match of specified regular expression. A value is available; <code>BOF</code> for inserting the line at the beginning of the file.</div><div>If specified regular expression has no matches, the line will be inserted at the end of the file. May not be used with <code>backrefs</code>.</div>        </td></tr>
                <tr><td>line<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Required for <code>state=present</code>. The line to insert/replace into the file. If <code>backrefs</code> is set, may contain backreferences that will get expanded with the <code>regexp</code> capture groups if the regexp matches.</div>        </td></tr>
                <tr><td>newline<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>windows</td>
        <td><ul><li>windows</li><li>unix</li></ul></td>
        <td><div>Specifies the line separator style to use for the modified file. This defaults to the windows line separator (<code>
    </code>). Note that the indicated line separator will be used for file output regardless of the original line separator that appears in the input file.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The path of the file to modify.</div><div>Note that the Windows path delimiter <code>\</code> must be escaped as <code>\\</code> when the line is double quoted.</div><div>Before 2.3 this option was only usable as <em>dest</em>, <em>destfile</em> and <em>name</em>.</div></br>
    <div style="font-size: small;">aliases: dest, destfile, name<div>        </td></tr>
                <tr><td>regexp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The regular expression to look for in every line of the file. For <code>state=present</code>, the pattern to replace if found; only the last line found will be replaced. For <code>state=absent</code>, the pattern of the line to remove. Uses .NET compatible regular expressions; see <a href='https://msdn.microsoft.com/en-us/library/hs600312%28v=vs.110%29.aspx'>https://msdn.microsoft.com/en-us/library/hs600312%28v=vs.110%29.aspx</a>.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the line should be there or not.</div>        </td></tr>
                <tr><td>validate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Validation to run before copying into place. Use %s in the command to indicate the current file to validate.</div><div>The command is passed securely so shell features like expansion and pipes won't work.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Before 2.3, option 'dest', 'destfile' or 'name' was used instead of 'path'
    - win_lineinfile:
        path: C:\temp\example.conf
        regexp: '^name='
        line: 'name=JohnDoe'
    
    - win_lineinfile:
        path: C:\temp\example.conf
        regexp: '^name='
        state: absent
    
    - win_lineinfile:
        path: C:\temp\example.conf
        regexp: '^127\.0\.0\.1'
        line: '127.0.0.1 localhost'
    
    - win_lineinfile:
        path: C:\temp\httpd.conf
        regexp: '^Listen '
        insertafter: '^#Listen '
        line: Listen 8080
    
    - win_lineinfile:
        path: C:\temp\services
        regexp: '^# port for http'
        insertbefore: '^www.*80/tcp'
        line: '# port for http by default'
    
    # Create file if it doesn't exist with a specific encoding
    - win_lineinfile:
        path: C:\temp\utf16.txt
        create: yes
        encoding: utf-16
        line: This is a utf-16 encoded file
    
    # Add a line to a file and ensure the resulting file uses unix line separators
    - win_lineinfile:
        path: C:\temp\testfile.txt
        line: Line added to file
        newline: unix
    
    # Update a line using backrefs
    - win_lineinfile:
        path: C:\temp\example.conf
        backrefs: yes
        regexp: '(^name=)'
        line: '$1JohnDoe'


Notes
-----

.. note::
    - As of Ansible 2.3, the *dest* option has been changed to *path* as default, but *dest* still works as well.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
