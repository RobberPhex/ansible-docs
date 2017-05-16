.. _lvol:


lvol - Configure LVM logical volumes
++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module creates, removes or resizes logical volumes.




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
    <td>force<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Shrink or remove operations of volumes requires this switch. Ensures that that filesystems get never corrupted/destroyed by mistake.</div></td></tr>
            <tr>
    <td>lv<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the logical volume.</div></td></tr>
            <tr>
    <td>opts<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Free-form options to be passed to the lvcreate command</div></td></tr>
            <tr>
    <td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The size of the logical volume, according to lvcreate(8) --size, by default in megabytes or optionally with one of [bBsSkKmMgGtTpPeE] units; or according to lvcreate(8) --extents as a percentage of [VG|PVS|FREE]; Float values must begin with a digit. Resizing using percentage values was not supported prior to 2.1.</div></td></tr>
            <tr>
    <td>snapshot<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the snapshot volume</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Control if the logical volume exists. If <code>present</code> the <code>size</code> option is required.</div></td></tr>
            <tr>
    <td>vg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The volume group this logical volume is part of.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a logical volume of 512m.
    - lvol: vg=firefly lv=test size=512
    
    # Create a logical volume of 512g.
    - lvol: vg=firefly lv=test size=512g
    
    # Create a logical volume the size of all remaining space in the volume group
    - lvol: vg=firefly lv=test size=100%FREE
    
    # Create a logical volume with special options
    - lvol: vg=firefly lv=test size=512g opts="-r 16"
    
    # Extend the logical volume to 1024m.
    - lvol: vg=firefly lv=test size=1024
    
    # Extend the logical volume to consume all remaining space in the volume group
    - lvol: vg=firefly lv=test size=+100%FREE
    
    # Extend the logical volume to take all remaining space of the PVs
    - lvol: vg=firefly lv=test size=100%PVS
    
    # Resize the logical volume to % of VG
    - lvol: vg-firefly lv=test size=80%VG force=yes
    
    # Reduce the logical volume to 512m
    - lvol: vg=firefly lv=test size=512 force=yes
    
    # Remove the logical volume.
    - lvol: vg=firefly lv=test state=absent force=yes
    
    # Create a snapshot volume of the test logical volume.
    - lvol: vg=firefly lv=test snapshot=snap1 size=100m


Notes
-----

.. note:: Filesystems on top of the volume are not resized.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

