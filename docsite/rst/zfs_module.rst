.. _zfs:


zfs - Manage zfs
++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages ZFS file systems, volumes, clones and snapshots.




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
    <td>key_value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>zfs</code> module takes key=value pairs for zfs properties to be set. See the zfs(8) man page for more information.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File system, snapshot or volume name e.g. <code>rpool/myfs</code></div></td></tr>
            <tr>
    <td>origin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Snapshot from which to create a clone</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to create (<code>present</code>), or remove (<code>absent</code>) a file system, snapshot or volume. All parents/children will be created/destroyed as needed to reach the desired state.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new file system called myfs in pool rpool with the setuid property turned off
    - zfs: name=rpool/myfs state=present setuid=off
    
    # Create a new volume called myvol in pool rpool.
    - zfs: name=rpool/myvol state=present volsize=10M
    
    # Create a snapshot of rpool/myfs file system.
    - zfs: name=rpool/myfs@mysnapshot state=present
    
    # Create a new file system called myfs2 with snapdir enabled
    - zfs: name=rpool/myfs2 state=present snapdir=enabled
    
    # Create a new file system by cloning a snapshot
    - zfs: name=rpool/cloned_fs state=present origin=rpool/myfs@mysnapshot
    
    # Destroy a filesystem
    - zfs: name=rpool/myfs state=absent




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

