.. _lvg:


lvg - Configure LVM volume groups
+++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

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
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If yes, allows to remove volume group with logical volumes.</td>
    </tr>
            <tr>
    <td>pesize</td>
    <td>no</td>
    <td>4</td>
        <td><ul></ul></td>
        <td>The size of the physical extent in megabytes. Must be a power of 2.</td>
    </tr>
            <tr>
    <td>pvs</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of comma-separated devices to use as physical devices in this volume group. Required when creating or resizing volume group.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Control if the volume group exists.</td>
    </tr>
            <tr>
    <td>vg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the volume group.</td>
    </tr>
            <tr>
    <td>vg_options</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Additional options to pass to <code>vgcreate</code> when creating the volume group. (added in Ansible 1.6)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


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

.. note:: module does not modify PE size for already present volume group


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

