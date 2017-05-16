.. _acl:


acl - Sets and retrieves file ACL information.
++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Sets and retrieves file ACL information.

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
    <td>default</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if the target is a directory, setting this to yes will make it the default acl for entities created inside the directory. It causes an error if name is a file. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>entity</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>actual user or group that the ACL applies to when matching entity types user or group are selected. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>entry</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>DEPRECATED. The acl to set or remove.  This must always be quoted in the form of '&lt;etype&gt;:&lt;qualifier&gt;:&lt;perms&gt;'.  The qualifier may be empty for some types, but the type and perms are always requried. '-' can be used as placeholder when you do not care about permissions. This is now superseded by entity, type and permissions fields.</td>
    </tr>
            <tr>
    <td>etype</td>
    <td>no</td>
    <td></td>
        <td><ul><li>user</li><li>group</li><li>mask</li><li>other</li></ul></td>
        <td>the entity type of the ACL to apply, see setfacl documentation for more info. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>follow</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>whether to follow symlinks on the path if a symlink is encountered.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The full path of the file or object.</td>
    </tr>
            <tr>
    <td>permissions</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Permissions to apply/remove can be any combination of r, w and  x (read, write and execute respectively) (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>query</td>
        <td><ul><li>query</li><li>present</li><li>absent</li></ul></td>
        <td>defines whether the ACL should be present or not.  The <code>query</code> state gets the current acl without changing it, for use in 'register' operations.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Grant user Joe read access to a file
    - acl: name=/etc/foo.conf entity=joe etype=user permissions="r" state=present
    
    # Removes the acl for Joe on a specific file
    - acl: name=/etc/foo.conf entity=joe etype=user state=absent
    
    # Sets default acl for joe on foo.d
    - acl: name=/etc/foo.d entity=joe etype=user permissions=rw default=yes state=present
    
    # Same as previous but using entry shorthand
    - acl: name=/etc/foo.d entry="default:user:joe:rw-" state=present
    
    # Obtain the acl for a specific file
    - acl: name=/etc/foo.conf
      register: acl_info

.. note:: The "acl" module requires that acls are enabled on the target filesystem and that the setfacl and getfacl binaries are installed.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

