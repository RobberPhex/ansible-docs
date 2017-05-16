.. _xattr:


xattr - set/retrieve extended attributes
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Manages filesystem user defined extended attributes, requires that they are enabled on the target filesystem and that the setfattr/getfattr utilities are present.

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
    <td>follow</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if yes, dereferences symlinks and sets/gets attributes on symlink target, otherwise acts on symlink itself.</td>
    </tr>
            <tr>
    <td>key</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of a specific Extended attribute key to set/retrieve</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The full path of the file/object to get the facts of</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>read</li><li>present</li><li>all</li><li>keys</li><li>absent</li></ul></td>
        <td>defines which state you want to do. <code>read</code> retrieves the current value for a <code>key</code> (default) <code>present</code> sets <code>name</code> to <code>value</code>, default if value is set <code>all</code> dumps all data <code>keys</code> retrieves all keys <code>absent</code> deletes the key</td>
    </tr>
            <tr>
    <td>value</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The value to set the named name/key to, it automatically sets the <code>state</code> to 'set'</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Obtain the extended attributes  of /etc/foo.conf
    - xattr: name=/etc/foo.conf
    
    # Sets the key 'foo' to value 'bar'
    - xattr: path=/etc/foo.conf key=user.foo value=bar
    
    # Removes the key 'foo'
    - xattr: name=/etc/foo.conf key=user.foo state=absent



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

