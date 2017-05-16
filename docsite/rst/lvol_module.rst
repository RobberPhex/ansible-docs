.. _lvol:


lvol - Configure LVM logical volumes
++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

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
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Shrink or remove operations of volumes requires this switch. Ensures that that filesystems get never corrupted/destroyed by mistake. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>lv</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the logical volume.</td>
    </tr>
            <tr>
    <td>size</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The size of the logical volume, according to lvcreate(8) --size, by default in megabytes or optionally with one of [bBsSkKmMgGtTpPeE] units; or according to lvcreate(8) --extents as a percentage of [VG|PVS|FREE]; resizing is not supported with percentages.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Control if the logical volume exists.</td>
    </tr>
            <tr>
    <td>vg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The volume group this logical volume is part of.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Create a logical volume of 512m.
    - lvol: vg=firefly lv=test size=512
    
    # Create a logical volume of 512g.
    - lvol: vg=firefly lv=test size=512g
    
    # Create a logical volume the size of all remaining space in the volume group
    - lvol: vg=firefly lv=test size=100%FREE
    
    # Extend the logical volume to 1024m.
    - lvol: vg=firefly lv=test size=1024
    
    # Reduce the logical volume to 512m
    - lvol: vg=firefly lv=test size=512 force=yes
    
    # Remove the logical volume.
    - lvol: vg=firefly lv=test state=absent force=yes

.. note:: Filesystems on top of the volume are not resized.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

