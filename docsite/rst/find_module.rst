.. _find:


find - return a list of files based on specific criteria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Return a list files based on specific criteria. Multiple criteria are AND'd together.




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
    <td>age<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Select files whose age is equal to or greater than the specified time. Use a negative age to find files equal to or less than the specified time. You can choose seconds, minutes, hours, days, or weeks by specifying the first letter of any of those words (e.g., "1w").</div></td></tr>
            <tr>
    <td>age_stamp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>mtime</td>
        <td><ul><li>atime</li><li>mtime</li><li>ctime</li></ul></td>
        <td><div>Choose the file property against which we compare age. Default is mtime.</div></td></tr>
            <tr>
    <td>contains<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>One or more regex patterns which should be matched against the file content</div></td></tr>
            <tr>
    <td>file_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>directory</li></ul></td>
        <td><div>Type of file to select</div></td></tr>
            <tr>
    <td>follow<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>False</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set this to true to follow symlinks in path for systems with python 2.6+</div></td></tr>
            <tr>
    <td>get_checksum<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>False</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set this to true to retrieve a file's sha1 checksum</div></td></tr>
            <tr>
    <td>hidden<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>False</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set this to true to include hidden files, otherwise they'll be ignored.</div></td></tr>
            <tr>
    <td>paths<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of paths to the file or directory to search. All paths must be fully qualified.</div></br>
        <div style="font-size: small;">aliases: name, path<div></td></tr>
            <tr>
    <td>patterns<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td><div>One or more (shell or regex) patterns, which type is controlled by <code>use_regex</code> option.</div><div>The patterns restrict the list of files to be returned to those whose basenames match at least one of the patterns specified. Multiple patterns can be specified using a list.</div></br>
        <div style="font-size: small;">aliases: pattern<div></td></tr>
            <tr>
    <td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If target is a directory, recursively descend into the directory looking for files.</div></td></tr>
            <tr>
    <td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Select files whose size is equal to or greater than the specified size. Use a negative size to find files equal to or less than the specified size. Unqualified values are in bytes, but b, k, m, g, and t can be appended to specify bytes, kilobytes, megabytes, gigabytes, and terabytes, respectively. Size is not evaluated for directories.</div></td></tr>
            <tr>
    <td>use_regex<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>False</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If false the patterns are file globs (shell) if true they are python regexes</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Recursively find /tmp files older than 2 days
    - find: paths="/tmp" age="2d" recurse=yes
    
    # Recursively find /tmp files older than 4 weeks and equal or greater than 1 megabyte
    - find: paths="/tmp" age="4w" size="1m" recurse=yes
    
    # Recursively find /var/tmp files with last access time greater than 3600 seconds
    - find: paths="/var/tmp" age="3600" age_stamp=atime recurse=yes
    
    # find /var/log files equal or greater than 10 megabytes ending with .old or .log.gz
    - find: paths="/var/tmp" patterns="*.old,*.log.gz" size="10m"
    
    # find /var/log files equal or greater than 10 megabytes ending with .old or .log.gz via regex
    - find: paths="/var/tmp" patterns="^.*?\.(?:old|log\.gz)$" size="10m" use_regex=True

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> files </td>
        <td> all matches found with the specified criteria (see stat module for full output of each dictionary) </td>
        <td align=center> success </td>
        <td align=center> list of dictionaries </td>
        <td align=center> [{'mode=0644': None, 'path="/var/tmp/test1"': None, '...': None, 'checksum=16fac7be61a6e4591a33ef4b729c5c3302307523': None}, {'...': None, 'path="/var/tmp/test2"': None}] </td>
    </tr>
            <tr>
        <td> examined </td>
        <td> number of filesystem objects looked at </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 34 </td>
    </tr>
            <tr>
        <td> matched </td>
        <td> number of matches </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 14 </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

