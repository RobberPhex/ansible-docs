.. _filesystem:


filesystem - Makes file system on block device
++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module creates file system.




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
    <td>dev<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Target block device.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If yes, allows to create new filesystem on devices that already has filesystem.</div></td></tr>
            <tr>
    <td>fstype<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File System type to be created.</div></td></tr>
            <tr>
    <td>opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of options to be passed to mkfs command.</div></td></tr>
            <tr>
    <td>resizefs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If yes, if the block device and filessytem size differ, grow the filesystem into the space. Note, XFS Will only grow if mounted.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a ext2 filesystem on /dev/sdb1.
    - filesystem: fstype=ext2 dev=/dev/sdb1
    
    # Create a ext4 filesystem on /dev/sdb1 and check disk blocks.
    - filesystem: fstype=ext4 dev=/dev/sdb1 opts="-cc"


Notes
-----

.. note:: uses mkfs command


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

