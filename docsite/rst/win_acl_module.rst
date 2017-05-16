.. _win_acl:


win_acl - Set file/directory permissions for a system user or group.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove rights/permissions for a given user or group for the specified src file or folder.




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
    <td>inherit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>For Leaf File, None; For Directory, ContainerInherit, ObjectInherit;</td>
        <td><ul><li>ContainerInherit</li><li>ObjectInherit</li><li>None</li></ul></td>
        <td><div>Inherit flags on the ACL rules.  Can be specified as a comma separated list (Ex. "ContainerInherit, ObjectInherit").  For more information on the choices see MSDN InheritanceFlags Enumeration.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File or Directory</div></td></tr>
            <tr>
    <td>propagation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>None</li><li>NoPropagateInherit</li><li>InheritOnly</li></ul></td>
        <td><div>Propagation flag on the ACL rules.  For more information on the choices see MSDN PropagationFlags Enumeration.</div></td></tr>
            <tr>
    <td>rights<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>none</td>
        <td><ul><li>AppendData</li><li>ChangePermissions</li><li>Delete</li><li>DeleteSubdirectoriesAndFiles</li><li>ExecuteFile</li><li>FullControl</li><li>ListDirectory</li><li>Modify</li><li>Read</li><li>ReadAndExecute</li><li>ReadAttributes</li><li>ReadData</li><li>ReadExtendedAttributes</li><li>ReadPermissions</li><li>Synchronize</li><li>TakeOwnership</li><li>Traverse</li><li>Write</li><li>WriteAttributes</li><li>WriteData</li><li>WriteExtendedAttributes</li></ul></td>
        <td><div>The rights/permissions that are to be allowed/denyed for the specified user or group for the given src file or directory.  Can be entered as a comma separated list (Ex. "Modify, Delete, ExecuteFile").  For more information on the choices see MSDN FileSystemRights Enumeration.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specify whether to add (present) or remove (absent) the specified access rule</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>none</td>
        <td><ul><li>allow</li><li>deny</li></ul></td>
        <td><div>Specify whether to allow or deny the rights specified</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>User or Group to add specified rights to act on src file/folder</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Restrict write,execute access to User Fed-Phil
    $ ansible -i hosts -m win_acl -a "user=Fed-Phil path=C:\Important\Executable.exe type=deny rights='ExecuteFile,Write'" all
    
    # Playbook example
    # Add access rule to allow IIS_IUSRS FullControl to MySite
    ---
    - name: Add IIS_IUSRS allow rights
      win_acl:
        path: 'C:\inetpub\wwwroot\MySite'
        user: 'IIS_IUSRS'
        rights: 'FullControl'
        type: 'allow'
        state: 'present'
        inherit: 'ContainerInherit, ObjectInherit'
        propagation: 'None'
    
    # Remove previously added rule for IIS_IUSRS
    - name: Remove FullControl AccessRule for IIS_IUSRS
        path: 'C:\inetpub\wwwroot\MySite'
        user: 'IIS_IUSRS'
        rights: 'FullControl'
        type: 'allow'
        state: 'absent'
        inherit: 'ContainerInherit, ObjectInherit'
        propagation: 'None'
    
    # Deny Intern
    - name: Deny Deny
        path: 'C:\Administrator\Documents'
        user: 'Intern'
        rights: 'Read,Write,Modify,FullControl,Delete'
        type: 'deny'
        state: 'present'




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

