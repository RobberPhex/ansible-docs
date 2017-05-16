.. _mount:


mount - Control active and configured mount points
++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module controls active and configured mount points in ``/etc/fstab``.




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
    <td>boot<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Determines if the filesystem should be mounted on boot.</div><div>Only applies to Solaris systems.</div></td></tr>
            <tr>
    <td>dump<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dump (see fstab(5)). Note that if set to <code>null</code> and <em>state</em> set to <code>present</code>, it will cease to work and duplicate entries will be made with subsequent runs.</div><div>Has no effect on Solaris systems.</div></td></tr>
            <tr>
    <td>fstab<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/fstab (/etc/vfstab on Solaris)</td>
        <td><ul></ul></td>
        <td><div>File to use instead of <code>/etc/fstab</code>. You shouldn't use this option unless you really know what you are doing. This might be useful if you need to configure mountpoints in a chroot environment.  OpenBSD does not allow specifying alternate fstab files with mount so do not use this on OpenBSD with any state that operates on the live filesystem.</div></td></tr>
            <tr>
    <td>fstype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Filesystem type. Required when <em>state</em> is <code>present</code> or <code>mounted</code>.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the mount point (e.g. <code>/mnt/files</code>)</div></td></tr>
            <tr>
    <td>opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Mount options (see fstab(5), or vfstab(4) on Solaris).</div></td></tr>
            <tr>
    <td>passno<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Passno (see fstab(5)). Note that if set to <code>null</code> and <em>state</em> set to <code>present</code>, it will cease to work and duplicate entries will be made with subsequent runs.</div><div>Deprecated on Solaris systems.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Device to be mounted on <em>name</em>. Required when <em>state</em> set to <code>present</code> or <code>mounted</code>.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>mounted</li><li>unmounted</li></ul></td>
        <td><div>If <code>mounted</code> or <code>unmounted</code>, the device will be actively mounted or unmounted as needed and appropriately configured in <em>fstab</em>.</div><div><code>absent</code> and <code>present</code> only deal with <em>fstab</em> but will not affect current mounting.</div><div>If specifying <code>mounted</code> and the mount point is not present, the mount point will be created.</div><div>Similarly, specifying <code>absent</code> will remove the mount point directory.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Mount DVD read-only
      mount:
        name: /mnt/dvd
        src: /dev/sr0
        fstype: iso9660
        opts: ro
        state: present
    
    - name: Mount up device by label
      mount:
        name: /srv/disk
        src: LABEL=SOME_LABEL
        fstype: ext4
        state: present
    
    - name: Mount up device by UUID
      mount:
        name: /home
        src: UUID=b3e48f45-f933-4c8e-a700-22a159ec9077
        fstype: xfs
        opts: noatime
        state: present




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

