.. _win_path:


win_path - Manage Windows path environment variables
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Allows element-based ordering, addition, and removal of Windows path environment variables.




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
                <tr><td>elements<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A single path element, or a list of path elements (ie, directories) to add or remove.</div><div>When multiple elements are included in the list (and <code>state</code> is <code>present</code>), the elements are guaranteed to appear in the same relative order in the resultant path value.</div><div>Variable expansions (eg, <code>%VARNAME%</code>) are allowed, and are stored unexpanded in the target path element.</div><div>Any existing path elements not mentioned in <code>elements</code> are always preserved in their current order.</div><div>New path elements are appended to the path, and existing path elements may be moved closer to the end to satisfy the requested ordering.</div><div>Paths are compared in a case-insensitive fashion, and trailing backslashes are ignored for comparison purposes. However, note that trailing backslashes in YAML require quotes.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>PATH</td>
        <td></td>
        <td><div>Target path environment variable name</div>        </td></tr>
                <tr><td>scope<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>machine</td>
        <td><ul><li>machine</li><li>user</li></ul></td>
        <td><div>The level at which the environment variable specified by <code>name</code> should be managed (either for the current user or global machine scope).</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the path elements specified in <code>elements</code> should be present or absent.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Ensure that system32 and Powershell are present on the global system path, and in the specified order
      win_path:
        elements:
        - '%SystemRoot%\system32'
        - '%SystemRoot%\system32\WindowsPowerShell\v1.0'
    
    - name: Ensure that C:\Program Files\MyJavaThing is not on the current user's CLASSPATH
      win_path:
        name: CLASSPATH
        elements: C:\Program Files\MyJavaThing
        scope: user
        state: absent


Notes
-----

.. note::
    - This module is for modifying indidvidual elements of path-like environment variables. For general-purpose management of other environment vars, use the :ref:`win_environment <win_environment>` module.
    - This module does not broadcast change events. This means that the minority of windows applications which can have their environment changed without restarting will not be notified and therefore will need restarting to pick up new environment settings. User level environment variables will require an interactive user to log out and in again before they become available.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
