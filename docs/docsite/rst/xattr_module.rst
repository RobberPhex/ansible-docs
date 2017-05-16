.. _xattr:


xattr - set/retrieve extended attributes
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages filesystem user defined extended attributes, requires that they are enabled on the target filesystem and that the setfattr/getfattr utilities are present.




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
                <tr><td>follow<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if yes, dereferences symlinks and sets/gets attributes on symlink target, otherwise acts on symlink itself.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The name of a specific Extended attribute key to set/retrieve</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>The full path of the file/object to get the facts of.</div><div>Before 2.3 this option was only usable as <em>name</em>.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>read</li><li>present</li><li>all</li><li>keys</li><li>absent</li></ul></td>
        <td><div>defines which state you want to do. <code>read</code> retrieves the current value for a <code>key</code> (default) <code>present</code> sets <code>name</code> to <code>value</code>, default if value is set <code>all</code> dumps all data <code>keys</code> retrieves all keys <code>absent</code> deletes the key</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The value to set the named name/key to, it automatically sets the <code>state</code> to 'set'</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Obtain the extended attributes  of /etc/foo.conf
    - xattr:
        path: /etc/foo.conf
    
    # Sets the key 'foo' to value 'bar'
    - xattr:
        path: /etc/foo.conf
        key: user.foo
        value: bar
    
    # Removes the key 'foo'
    - xattr:
        path: /etc/foo.conf
        key: user.foo
        state: absent


Notes
-----

.. note::
    - As of Ansible 2.3, the *name* option has been changed to *path* as default, but *name* still works as well.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
