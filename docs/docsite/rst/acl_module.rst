.. _acl:


acl - Sets and retrieves file ACL information.
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Sets and retrieves file ACL information.




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
                <tr><td>default<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if the target is a directory, setting this to yes will make it the default acl for entities created inside the directory. It causes an error if path is a file.</div>        </td></tr>
                <tr><td>entity<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>actual user or group that the ACL applies to when matching entity types user or group are selected.</div>        </td></tr>
                <tr><td>entry<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>DEPRECATED. The acl to set or remove.  This must always be quoted in the form of '&lt;etype&gt;:&lt;qualifier&gt;:&lt;perms&gt;'.  The qualifier may be empty for some types, but the type and perms are always required. '-' can be used as placeholder when you do not care about permissions. This is now superseded by entity, type and permissions fields.</div>        </td></tr>
                <tr><td>etype<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>user</li><li>group</li><li>mask</li><li>other</li></ul></td>
        <td><div>the entity type of the ACL to apply, see setfacl documentation for more info.</div>        </td></tr>
                <tr><td>follow<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>whether to follow symlinks on the path if a symlink is encountered.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The full path of the file or object.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>permissions<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Permissions to apply/remove can be any combination of r, w and  x (read, write and execute respectively)</div>        </td></tr>
                <tr><td>recursive<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Recursively sets the specified ACL (added in Ansible 2.0). Incompatible with <code>state=query</code>.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>query</td>
        <td><ul><li>query</li><li>present</li><li>absent</li></ul></td>
        <td><div>defines whether the ACL should be present or not.  The <code>query</code> state gets the current acl without changing it, for use in 'register' operations.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Grant user Joe read access to a file
    - acl:
        path: /etc/foo.conf
        entity: joe
        etype: user
        permissions: r
        state: present
    
    # Removes the acl for Joe on a specific file
    - acl:
        path: /etc/foo.conf
        entity: joe
        etype: user
        state: absent
    
    # Sets default acl for joe on foo.d
    - acl:
        path: /etc/foo.d
        entity: joe
        etype: user
        permissions: rw
        default: yes
        state: present
    
    # Same as previous but using entry shorthand
    - acl:
        path: /etc/foo.d
        entry: "default:user:joe:rw-"
        state: present
    
    # Obtain the acl for a specific file
    - acl:
        path: /etc/foo.conf
      register: acl_info

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
        <td> acl </td>
        <td> Current acl on provided path (after changes, if any) </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ['user::rwx', 'group::rwx', 'other::rwx'] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - The "acl" module requires that acls are enabled on the target filesystem and that the setfacl and getfacl binaries are installed.
    - As of Ansible 2.0, this module only supports Linux distributions.
    - As of Ansible 2.3, the *name* option has been changed to *path* as default, but *name* still works as well.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
