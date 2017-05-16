.. _zfs:


zfs - Manage zfs
++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages ZFS file systems on Solaris and FreeBSD. Can manage file systems, volumes and snapshots. See zfs(1M) for more information about the properties.




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
    <td>aclinherit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>discard</li><li>noallow</li><li>restricted</li><li>passthrough</li><li>passthrough-x</li></ul></td>
        <td><div>The aclinherit property.</div></td></tr>
            <tr>
    <td>aclmode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>discard</li><li>groupmask</li><li>passthrough</li></ul></td>
        <td><div>The aclmode property.</div></td></tr>
            <tr>
    <td>atime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The atime property.</div></td></tr>
            <tr>
    <td>canmount<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li><li>noauto</li></ul></td>
        <td><div>The canmount property.</div></td></tr>
            <tr>
    <td>casesensitivity<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>sensitive</li><li>insensitive</li><li>mixed</li></ul></td>
        <td><div>The casesensitivity property.</div></td></tr>
            <tr>
    <td>checksum<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li><li>fletcher2</li><li>fletcher4</li><li>sha256</li></ul></td>
        <td><div>The checksum property.</div></td></tr>
            <tr>
    <td>compression<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li><li>lzjb</li><li>gzip</li><li>gzip-1</li><li>gzip-2</li><li>gzip-3</li><li>gzip-4</li><li>gzip-5</li><li>gzip-6</li><li>gzip-7</li><li>gzip-8</li><li>gzip-9</li><li>lz4</li><li>zle</li></ul></td>
        <td><div>The compression property.</div></td></tr>
            <tr>
    <td>copies<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>1</li><li>2</li><li>3</li></ul></td>
        <td><div>The copies property.</div></td></tr>
            <tr>
    <td>dedup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The dedup property.</div></td></tr>
            <tr>
    <td>devices<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The devices property.</div></td></tr>
            <tr>
    <td>exec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The exec property.</div></td></tr>
            <tr>
    <td>jailed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The jailed property.</div></td></tr>
            <tr>
    <td>logbias<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>latency</li><li>throughput</li></ul></td>
        <td><div>The logbias property.</div></td></tr>
            <tr>
    <td>mountpoint<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The mountpoint property.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File system, snapshot or volume name e.g. <code>rpool/myfs</code></div></td></tr>
            <tr>
    <td>nbmand<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The nbmand property.</div></td></tr>
            <tr>
    <td>normalization<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>none</li><li>formC</li><li>formD</li><li>formKC</li><li>formKD</li></ul></td>
        <td><div>The normalization property.</div></td></tr>
            <tr>
    <td>origin<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the snapshot to clone</div></td></tr>
            <tr>
    <td>primarycache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li><li>none</li><li>metadata</li></ul></td>
        <td><div>The primarycache property.</div></td></tr>
            <tr>
    <td>quota<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The quota property.</div></td></tr>
            <tr>
    <td>readonly<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The readonly property.</div></td></tr>
            <tr>
    <td>recordsize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The recordsize property.</div></td></tr>
            <tr>
    <td>refquota<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The refquota property.</div></td></tr>
            <tr>
    <td>refreservation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The refreservation property.</div></td></tr>
            <tr>
    <td>reservation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The reservation property.</div></td></tr>
            <tr>
    <td>secondarycache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li><li>none</li><li>metadata</li></ul></td>
        <td><div>The secondarycache property.</div></td></tr>
            <tr>
    <td>setuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The setuid property.</div></td></tr>
            <tr>
    <td>shareiscsi<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The shareiscsi property.</div></td></tr>
            <tr>
    <td>sharenfs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The sharenfs property.</div></td></tr>
            <tr>
    <td>sharesmb<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The sharesmb property.</div></td></tr>
            <tr>
    <td>snapdir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>hidden</li><li>visible</li></ul></td>
        <td><div>The snapdir property.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to create (<code>present</code>), or remove (<code>absent</code>) a file system, snapshot or volume.</div></td></tr>
            <tr>
    <td>sync<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>standard</li><li>always</li><li>disabled</li></ul></td>
        <td><div>The sync property.</div></td></tr>
            <tr>
    <td>utf8only<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The utf8only property.</div></td></tr>
            <tr>
    <td>volblocksize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The volblocksize property.</div></td></tr>
            <tr>
    <td>volsize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The volsize property.</div></td></tr>
            <tr>
    <td>vscan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The vscan property.</div></td></tr>
            <tr>
    <td>xattr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The xattr property.</div></td></tr>
            <tr>
    <td>zoned<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td><div>The zoned property.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new file system called myfs in pool rpool
    - zfs: name=rpool/myfs state=present
    
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

