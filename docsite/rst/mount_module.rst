.. _mount:


mount - Control active and configured mount points
++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


This module controls active and configured mount points in ``/etc/fstab``.

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
    <td>dump</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>dump (see fstab(8))</td>
    </tr>
            <tr>
    <td>fstab</td>
    <td>no</td>
    <td>/etc/fstab</td>
        <td><ul></ul></td>
        <td>file to use instead of <code>/etc/fstab</code>. You shouldn't use that option unless you really know what you are doing. This might be useful if you need to configure mountpoints in a chroot environment.</td>
    </tr>
            <tr>
    <td>fstype</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>file-system type</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to the mount point, eg: <code>/mnt/files</code></td>
    </tr>
            <tr>
    <td>opts</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>mount options (see fstab(8))</td>
    </tr>
            <tr>
    <td>passno</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>passno (see fstab(8))</td>
    </tr>
            <tr>
    <td>src</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>device to be mounted on <em>name</em>.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>mounted</li><li>unmounted</li></ul></td>
        <td>If <code>mounted</code> or <code>unmounted</code>, the device will be actively mounted or unmounted as needed and appropriately configured in <em>fstab</em>. <code>absent</code> and <code>present</code> only deal with <em>fstab</em> but will not affect current mounting. If specifying <code>mounted</code> and the mount point is not present, the mount point will be created. Similarly, specifying <code>absent</code>        will remove the mount point directory.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Mount DVD read-only
    - mount: name=/mnt/dvd src=/dev/sr0 fstype=iso9660 opts=ro state=present
    
    # Mount up device by label
    - mount: name=/srv/disk src='LABEL=SOME_LABEL' fstype=ext4 state=present
    
    # Mount up device by UUID
    - mount: name=/home src='UUID=b3e48f45-f933-4c8e-a700-22a159ec9077' fstype=xfs opts=noatime state=present



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

