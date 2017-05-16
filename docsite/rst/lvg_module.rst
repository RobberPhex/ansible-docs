.. _lvg:


lvg - Configure LVM volume groups
+++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module creates, removes or resizes volume groups.




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
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If yes, allows to remove volume group with logical volumes.</div></td></tr>
            <tr>
    <td>pesize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>4</td>
        <td><ul></ul></td>
        <td><div>The size of the physical extent in megabytes. Must be a power of 2.</div></td></tr>
            <tr>
    <td>pvs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of comma-separated devices to use as physical devices in this volume group. Required when creating or resizing volume group.</div><div>The module will take care of running pvcreate if needed.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Control if the volume group exists.</div></td></tr>
            <tr>
    <td>vg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the volume group.</div></td></tr>
            <tr>
    <td>vg_options<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Additional options to pass to <code>vgcreate</code> when creating the volume group.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a volume group on top of /dev/sda1 with physical extent size = 32MB.
    - lvg:  vg=vg.services pvs=/dev/sda1 pesize=32
    
    # Create or resize a volume group on top of /dev/sdb1 and /dev/sdc5.
    # If, for example, we already have VG vg.services on top of /dev/sdb1,
    # this VG will be extended by /dev/sdc5.  Or if vg.services was created on
    # top of /dev/sda5, we first extend it with /dev/sdb1 and /dev/sdc5,
    # and then reduce by /dev/sda5.
    - lvg: vg=vg.services pvs=/dev/sdb1,/dev/sdc5
    
    # Remove a volume group with name vg.services.
    - lvg: vg=vg.services state=absent


Notes
-----

.. note:: module does not modify PE size for already present volume group


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

