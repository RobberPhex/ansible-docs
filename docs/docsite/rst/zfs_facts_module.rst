.. _zfs_facts:


zfs_facts - Gather facts about ZFS datasets.
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Gather facts from ZFS dataset properties.




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
                <tr><td>depth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Specifiies recurion depth.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ZFS dataset name.</div></br>
    <div style="font-size: small;">aliases: ds, dataset<div>        </td></tr>
                <tr><td>parsable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies if property values should be displayed in machine friendly format.</div>        </td></tr>
                <tr><td>properties<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td></td>
        <td><div>Specifies which dataset properties should be queried in comma-separated format. For more information about dataset properties, check zfs(1M) man page.</div></br>
    <div style="font-size: small;">aliases: props<div>        </td></tr>
                <tr><td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies if properties for any children should be recursively displayed.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>all</li><li>filesystem</li><li>volume</li><li>snapshot</li><li>bookmark</li></ul></td>
        <td><div>Specifies which datasets types to display. Multiple values have to be provided in comma-separated form.</div></br>
    <div style="font-size: small;">aliases: props<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Gather facts about ZFS dataset rpool/export/home
      zfs_facts:
        dataset: rpool/export/home
    
    - name: Report space usage on ZFS filesystems under data/home
      zfs_facts:
        name: data/home
        recurse: yes
        type: filesystem
    
    - debug:
        msg: 'ZFS dataset {{ item.name }} consumes {{ item.used }} of disk space.'
      with_items: '{{ ansible_zfs_datasets }}'

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
        <td> parsable </td>
        <td> if parsable output should be provided in machine friendly format. </td>
        <td align=center> if 'parsable' is set to True </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> recurse </td>
        <td> if we should recurse over ZFS dataset </td>
        <td align=center> if 'recurse' is set to True </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> name </td>
        <td> ZFS dataset name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> rpool/var/spool </td>
    </tr>
            <tr>
        <td> zfs_datasets </td>
        <td> ZFS dataset facts </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> {'setuid': 'on', 'referenced': '29.5K', 'logicalused': '3.45G', 'zoned': 'off', 'primarycache': 'all', 'logbias': 'latency', 'creation': 'Thu Jun 16 11:37 2016', 'sync': 'standard', 'copies': '1', 'sharenfs': 'off', 'usedbyrefreservation': '0', 'sharesmb': 'off', 'canmount': 'on', 'mountpoint': '/rpool', 'casesensitivity': 'sensitive', 'utf8only': 'off', 'usedbysnapshots': '0', 'readonly': 'off', 'mounted': 'yes', 'compression': 'off', 'xattr': 'on', 'aclmode': 'discard', 'dedup': 'off', 'snapshot_limit': 'none', 'aclinherit': 'restricted', 'compressratio': '1.00x', 'written': '29.5K', 'version': '5', 'normalization': 'none', 'filesystem_limit': 'none', 'type': 'filesystem', 'secondarycache': 'all', 'logicalreferenced': '18.5K', 'available': '43.8G', 'used': '4.41G', 'exec': 'on', 'refquota': 'none', 'refcompressratio': '1.00x', 'quota': 'none', 'snapshot_count': 'none', 'vscan': 'off', 'reservation': 'none', 'atime': 'on', 'recordsize': '128K', 'usedbychildren': '4.41G', 'usedbydataset': '29.5K', 'org.openindiana.caiman:install': 'ready', 'name': 'rpool', 'mlslabel': 'none', 'redundant_metadata': 'all', 'filesystem_count': 'none', 'devices': 'on', 'nbmand': 'off', 'refreservation': 'none', 'checksum': 'on', 'snapdir': 'hidden'} </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
