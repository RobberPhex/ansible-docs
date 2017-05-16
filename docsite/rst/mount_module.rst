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
    <td>dump<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>dump (see fstab(8)), Note that if nulled, <code>state=present</code> will cease to work and duplicate entries will be made with subsequent runs.</div></td></tr>
            <tr>
    <td>fstab<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/fstab</td>
        <td><ul></ul></td>
        <td><div>file to use instead of <code>/etc/fstab</code>. You shouldn't use that option unless you really know what you are doing. This might be useful if you need to configure mountpoints in a chroot environment.</div></td></tr>
            <tr>
    <td>fstype<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>file-system type</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the mount point, eg: <code>/mnt/files</code></div></td></tr>
            <tr>
    <td>opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>mount options (see fstab(8))</div></td></tr>
            <tr>
    <td>passno<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>passno (see fstab(8)), Note that if nulled, <code>state=present</code> will cease to work and duplicate entries will be made with subsequent runs.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>device to be mounted on <em>name</em>.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>mounted</li><li>unmounted</li></ul></td>
        <td><div>If <code>mounted</code> or <code>unmounted</code>, the device will be actively mounted or unmounted as needed and appropriately configured in <em>fstab</em>. <code>absent</code> and <code>present</code> only deal with <em>fstab</em> but will not affect current mounting. If specifying <code>mounted</code> and the mount point is not present, the mount point will be created. Similarly, specifying <code>absent</code>        will remove the mount point directory.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Mount DVD read-only
    - mount: name=/mnt/dvd src=/dev/sr0 fstype=iso9660 opts=ro state=present
    
    # Mount up device by label
    - mount: name=/srv/disk src='LABEL=SOME_LABEL' fstype=ext4 state=present
    
    # Mount up device by UUID
    - mount: name=/home src='UUID=b3e48f45-f933-4c8e-a700-22a159ec9077' fstype=xfs opts=noatime state=present




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

