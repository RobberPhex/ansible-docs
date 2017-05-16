.. _zpool_facts:


zpool_facts - Gather facts about ZFS pools.
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Gather facts from ZFS pool properties.




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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>ZFS pool name.</div></br>
    <div style="font-size: small;">aliases: pool, zpool<div>        </td></tr>
                <tr><td>parsable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies if property values should be displayed in machine friendly format.</div>        </td></tr>
                <tr><td>properties<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td></td>
        <td><div>Specifies which dataset properties should be queried in comma-separated format. For more information about dataset properties, check zpool(1M) man page.</div></br>
    <div style="font-size: small;">aliases: props<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Gather facts about ZFS pool rpool
    zpool_facts: pool=rpool
    
    # Gather space usage about all imported ZFS pools
    zpool_facts: properties='free,size'
    debug: msg='ZFS pool {{ item.name }} has {{ item.free }} free space out of {{ item.size }}.'
    with_items: '{{ ansible_zfs_pools }}'

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
        <td> zfs_pools </td>
        <td> ZFS pool facts </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> {'comment': '-', 'freeing': '0', 'listsnapshots': 'off', 'leaked': '0', 'feature@sha512': 'enabled', 'delegation': 'on', 'dedupditto': '0', 'dedupratio': '1.00x', 'autoexpand': 'off', 'feature@bookmarks': 'enabled', 'allocated': '3.46G', 'guid': '15729052870819522408', 'feature@large_blocks': 'enabled', 'feature@lz4_compress': 'active', 'feature@enabled_txg': 'active', 'autoreplace': 'off', 'capacity': '6%', 'feature@multi_vdev_crash_dump': 'enabled', 'feature@extensible_dataset': 'enabled', 'cachefile': '-', 'bootfs': 'rpool/ROOT/openindiana', 'feature@hole_birth': 'active', 'readonly': 'off', 'version': '-', 'health': 'ONLINE', 'expandsize': '-', 'feature@embedded_data': 'active', 'size': '49.8G', 'feature@async_destroy': 'enabled', 'feature@skein': 'enabled', 'feature@empty_bpobj': 'active', 'feature@spacemap_histogram': 'active', 'free': '46.3G', 'failmode': 'wait', 'feature@filesystem_limits': 'enabled', 'feature@edonr': 'enabled', 'altroot': '-', 'fragmentation': '3%', 'name': 'rpool'} </td>
    </tr>
            <tr>
        <td> name </td>
        <td> ZFS pool name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> rpool </td>
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
