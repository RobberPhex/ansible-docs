.. _zfs:


zfs - Manage zfs
++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

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
    <td>aclinherit</td>
    <td>no</td>
    <td></td>
        <td><ul><li>discard</li><li>noallow</li><li>restricted</li><li>passthrough</li><li>passthrough-x</li></ul></td>
        <td>The aclinherit property.</td>
    </tr>
            <tr>
    <td>aclmode</td>
    <td>no</td>
    <td></td>
        <td><ul><li>discard</li><li>groupmask</li><li>passthrough</li></ul></td>
        <td>The aclmode property.</td>
    </tr>
            <tr>
    <td>atime</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The atime property.</td>
    </tr>
            <tr>
    <td>canmount</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li><li>noauto</li></ul></td>
        <td>The canmount property.</td>
    </tr>
            <tr>
    <td>casesensitivity</td>
    <td>no</td>
    <td></td>
        <td><ul><li>sensitive</li><li>insensitive</li><li>mixed</li></ul></td>
        <td>The casesensitivity property.</td>
    </tr>
            <tr>
    <td>checksum</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li><li>fletcher2</li><li>fletcher4</li><li>sha256</li></ul></td>
        <td>The checksum property.</td>
    </tr>
            <tr>
    <td>compression</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li><li>lzjb</li><li>gzip</li><li>gzip-1</li><li>gzip-2</li><li>gzip-3</li><li>gzip-4</li><li>gzip-5</li><li>gzip-6</li><li>gzip-7</li><li>gzip-8</li><li>gzip-9</li><li>lz4</li><li>zle</li></ul></td>
        <td>The compression property.</td>
    </tr>
            <tr>
    <td>copies</td>
    <td>no</td>
    <td></td>
        <td><ul><li>1</li><li>2</li><li>3</li></ul></td>
        <td>The copies property.</td>
    </tr>
            <tr>
    <td>dedup</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The dedup property.</td>
    </tr>
            <tr>
    <td>devices</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The devices property.</td>
    </tr>
            <tr>
    <td>exec</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The exec property.</td>
    </tr>
            <tr>
    <td>jailed</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The jailed property.</td>
    </tr>
            <tr>
    <td>logbias</td>
    <td>no</td>
    <td></td>
        <td><ul><li>latency</li><li>throughput</li></ul></td>
        <td>The logbias property.</td>
    </tr>
            <tr>
    <td>mountpoint</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The mountpoint property.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>File system, snapshot or volume name e.g. <code>rpool/myfs</code></td>
    </tr>
            <tr>
    <td>nbmand</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The nbmand property.</td>
    </tr>
            <tr>
    <td>normalization</td>
    <td>no</td>
    <td></td>
        <td><ul><li>none</li><li>formC</li><li>formD</li><li>formKC</li><li>formKD</li></ul></td>
        <td>The normalization property.</td>
    </tr>
            <tr>
    <td>primarycache</td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li><li>none</li><li>metadata</li></ul></td>
        <td>The primarycache property.</td>
    </tr>
            <tr>
    <td>quota</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The quota property.</td>
    </tr>
            <tr>
    <td>readonly</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The readonly property.</td>
    </tr>
            <tr>
    <td>recordsize</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The recordsize property.</td>
    </tr>
            <tr>
    <td>refquota</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The refquota property.</td>
    </tr>
            <tr>
    <td>refreservation</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The refreservation property.</td>
    </tr>
            <tr>
    <td>reservation</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The reservation property.</td>
    </tr>
            <tr>
    <td>secondarycache</td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li><li>none</li><li>metadata</li></ul></td>
        <td>The secondarycache property.</td>
    </tr>
            <tr>
    <td>setuid</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The setuid property.</td>
    </tr>
            <tr>
    <td>shareiscsi</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The shareiscsi property.</td>
    </tr>
            <tr>
    <td>sharenfs</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The sharenfs property.</td>
    </tr>
            <tr>
    <td>sharesmb</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The sharesmb property.</td>
    </tr>
            <tr>
    <td>snapdir</td>
    <td>no</td>
    <td></td>
        <td><ul><li>hidden</li><li>visible</li></ul></td>
        <td>The snapdir property.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether to create (<code>present</code>), or remove (<code>absent</code>) a file system, snapshot or volume.</td>
    </tr>
            <tr>
    <td>sync</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The sync property.</td>
    </tr>
            <tr>
    <td>utf8only</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The utf8only property.</td>
    </tr>
            <tr>
    <td>volblocksize</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The volblocksize property.</td>
    </tr>
            <tr>
    <td>volsize</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The volsize property.</td>
    </tr>
            <tr>
    <td>vscan</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The vscan property.</td>
    </tr>
            <tr>
    <td>xattr</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The xattr property.</td>
    </tr>
            <tr>
    <td>zoned</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li></ul></td>
        <td>The zoned property.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Create a new file system called myfs in pool rpool
    - zfs: name=rpool/myfs state=present
    
    # Create a new volume called myvol in pool rpool. 
    - zfs: name=rpool/myvol state=present volsize=10M
    
    # Create a snapshot of rpool/myfs file system.
    - zfs: name=rpool/myfs@mysnapshot state=present
    
    # Create a new file system called myfs2 with snapdir enabled
    - zfs: name=rpool/myfs2 state=present snapdir=enabled



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

