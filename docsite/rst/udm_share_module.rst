.. _udm_share:


udm_share - Manage samba shares on a univention corporate server
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows to manage samba shares on a univention corporate server (UCS). It uses the python API of the UCS to create a new object or edit it.


Requirements (on host that executes module)
-------------------------------------------

  * Python >= 2.6


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
    <td>directorymode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>00755</td>
        <td><ul></ul></td>
        <td><div>Permissions for the share's root directory.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul></ul></td>
        <td><div>Directory owner group of the share's root directory.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Host FQDN (server which provides the share), e.g. <code>{{ ansible_fqdn }}</code>. Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name</div></td></tr>
            <tr>
    <td>nfs_custom_settings<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Option name in exports file.</div></br>
        <div style="font-size: small;">aliases: nfsCustomSettings<div></td></tr>
            <tr>
    <td>nfs_hosts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Only allow access for this host, IP address or network.</div></td></tr>
            <tr>
    <td>ou<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Organisational unit, inside the LDAP Base DN.</div></td></tr>
            <tr>
    <td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Directory owner of the share's root directory.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Directory on the providing server, e.g. <code>/home</code>. Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>root_squash<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Modify user ID for root user (root squashing).</div></td></tr>
            <tr>
    <td>samba_block_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Blocking size.</div></br>
        <div style="font-size: small;">aliases: sambaBlockSize<div></td></tr>
            <tr>
    <td>samba_blocking_locks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Blocking locks.</div></br>
        <div style="font-size: small;">aliases: sambaBlockingLocks<div></td></tr>
            <tr>
    <td>samba_browseable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Show in Windows network environment.</div></br>
        <div style="font-size: small;">aliases: sambaBrowseable<div></td></tr>
            <tr>
    <td>samba_create_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0744</td>
        <td><ul></ul></td>
        <td><div>File mode.</div></br>
        <div style="font-size: small;">aliases: sambaCreateMode<div></td></tr>
            <tr>
    <td>samba_csc_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>manual</td>
        <td><ul></ul></td>
        <td><div>Client-side caching policy.</div></br>
        <div style="font-size: small;">aliases: sambaCscPolicy<div></td></tr>
            <tr>
    <td>samba_custom_settings<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Option name in smb.conf and its value.</div></br>
        <div style="font-size: small;">aliases: sambaCustomSettings<div></td></tr>
            <tr>
    <td>samba_directory_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0755</td>
        <td><ul></ul></td>
        <td><div>Directory mode.</div></br>
        <div style="font-size: small;">aliases: sambaDirectoryMode<div></td></tr>
            <tr>
    <td>samba_directory_security_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0777</td>
        <td><ul></ul></td>
        <td><div>Directory security mode.</div></br>
        <div style="font-size: small;">aliases: sambaDirectorySecurityMode<div></td></tr>
            <tr>
    <td>samba_dos_filemode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Users with write access may modify permissions.</div></br>
        <div style="font-size: small;">aliases: sambaDosFilemode<div></td></tr>
            <tr>
    <td>samba_fake_oplocks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Fake oplocks.</div></br>
        <div style="font-size: small;">aliases: sambaFakeOplocks<div></td></tr>
            <tr>
    <td>samba_force_create_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Force file mode.</div></br>
        <div style="font-size: small;">aliases: sambaForceCreateMode<div></td></tr>
            <tr>
    <td>samba_force_directory_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Force directory mode.</div></br>
        <div style="font-size: small;">aliases: sambaForceDirectoryMode<div></td></tr>
            <tr>
    <td>samba_force_directory_security_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Force directory security mode.</div></br>
        <div style="font-size: small;">aliases: sambaForceDirectorySecurityMode<div></td></tr>
            <tr>
    <td>samba_force_group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Force group.</div></br>
        <div style="font-size: small;">aliases: sambaForceGroup<div></td></tr>
            <tr>
    <td>samba_force_security_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Force security mode.</div></br>
        <div style="font-size: small;">aliases: sambaForceSecurityMode<div></td></tr>
            <tr>
    <td>samba_force_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Force user.</div></br>
        <div style="font-size: small;">aliases: sambaForceUser<div></td></tr>
            <tr>
    <td>samba_hide_files<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Hide files.</div></br>
        <div style="font-size: small;">aliases: sambaHideFiles<div></td></tr>
            <tr>
    <td>samba_hide_unreadable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Hide unreadable files/directories.</div></br>
        <div style="font-size: small;">aliases: sambaHideUnreadable<div></td></tr>
            <tr>
    <td>samba_hosts_allow<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Allowed host/network.</div></br>
        <div style="font-size: small;">aliases: sambaHostsAllow<div></td></tr>
            <tr>
    <td>samba_hosts_deny<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Denied host/network.</div></br>
        <div style="font-size: small;">aliases: sambaHostsDeny<div></td></tr>
            <tr>
    <td>samba_inherit_acls<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Inherit ACLs.</div></br>
        <div style="font-size: small;">aliases: sambaInheritAcls<div></td></tr>
            <tr>
    <td>samba_inherit_owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Create files/directories with the owner of the parent directory.</div></br>
        <div style="font-size: small;">aliases: sambaInheritOwner<div></td></tr>
            <tr>
    <td>samba_inherit_permissions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Create files/directories with permissions of the parent directory.</div></br>
        <div style="font-size: small;">aliases: sambaInheritPermissions<div></td></tr>
            <tr>
    <td>samba_invalid_users<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Invalid users or groups.</div></br>
        <div style="font-size: small;">aliases: sambaInvalidUsers<div></td></tr>
            <tr>
    <td>samba_level_2_oplocks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Level 2 oplocks.</div></br>
        <div style="font-size: small;">aliases: sambaLevel2Oplocks<div></td></tr>
            <tr>
    <td>samba_locking<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Locking.</div></br>
        <div style="font-size: small;">aliases: sambaLocking<div></td></tr>
            <tr>
    <td>samba_msdfs_root<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>MSDFS root.</div></br>
        <div style="font-size: small;">aliases: sambaMSDFSRoot<div></td></tr>
            <tr>
    <td>samba_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Windows name. Required if <code>state=present</code>.</div></br>
        <div style="font-size: small;">aliases: sambaName<div></td></tr>
            <tr>
    <td>samba_nt_acl_support<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>NT ACL support.</div></br>
        <div style="font-size: small;">aliases: sambaNtAclSupport<div></td></tr>
            <tr>
    <td>samba_oplocks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Oplocks.</div></br>
        <div style="font-size: small;">aliases: sambaOplocks<div></td></tr>
            <tr>
    <td>samba_postexec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Postexec script.</div></br>
        <div style="font-size: small;">aliases: sambaPostexec<div></td></tr>
            <tr>
    <td>samba_preexec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Preexec script.</div></br>
        <div style="font-size: small;">aliases: sambaPreexec<div></td></tr>
            <tr>
    <td>samba_public<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Allow anonymous read-only access with a guest user.</div></br>
        <div style="font-size: small;">aliases: sambaPublic<div></td></tr>
            <tr>
    <td>samba_security_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0777</td>
        <td><ul></ul></td>
        <td><div>Security mode.</div></br>
        <div style="font-size: small;">aliases: sambaSecurityMode<div></td></tr>
            <tr>
    <td>samba_strict_locking<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Auto</td>
        <td><ul></ul></td>
        <td><div>Strict locking.</div></br>
        <div style="font-size: small;">aliases: sambaStrictLocking<div></td></tr>
            <tr>
    <td>samba_valid_users<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Valid users or groups.</div></br>
        <div style="font-size: small;">aliases: sambaValidUsers<div></td></tr>
            <tr>
    <td>samba_vfs_objects<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>VFS objects.</div></br>
        <div style="font-size: small;">aliases: sambaVFSObjects<div></td></tr>
            <tr>
    <td>samba_write_list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Restrict write access to these users/groups.</div></br>
        <div style="font-size: small;">aliases: sambaWriteList<div></td></tr>
            <tr>
    <td>samba_writeable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Samba write access.</div></br>
        <div style="font-size: small;">aliases: sambaWriteable<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the share is present or not.</div></td></tr>
            <tr>
    <td>subtree_checking<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Subtree checking.</div></td></tr>
            <tr>
    <td>sync<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>sync</td>
        <td><ul></ul></td>
        <td><div>NFS synchronisation.</div></td></tr>
            <tr>
    <td>writeable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>NFS write access.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a share named home on the server ucs.example.com with the path /home.
    - udm_share: name=home
                 path=/home
                 host=ucs.example.com
                 sambaName=Home




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

