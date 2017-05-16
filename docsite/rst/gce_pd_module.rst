.. _gce_pd:


gce_pd - utilize GCE persistent disk resources
++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

This module can create and destroy unformatted GCE persistent disks https://developers.google.com/compute/docs/disks#persistentdisks. It also supports attaching and detaching disks from running instances. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.

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
    <td>detach_only</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>do not destroy the disk, merely detach it from an instance</td>
    </tr>
            <tr>
    <td>disk_type</td>
    <td>no</td>
    <td>pd-standard</td>
        <td><ul><li>pd-standard</li><li>pd-ssd</li></ul></td>
        <td>type of disk provisioned (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>image</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the source image to use for the disk (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>instance_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>instance name if you wish to attach or detach the disk</td>
    </tr>
            <tr>
    <td>mode</td>
    <td>no</td>
    <td>READ_ONLY</td>
        <td><ul><li>READ_WRITE</li><li>READ_ONLY</li></ul></td>
        <td>GCE mount mode of disk, READ_ONLY (default) or READ_WRITE</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the disk</td>
    </tr>
            <tr>
    <td>pem_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to the pem file associated with the service account email (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>project_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>your GCE project ID (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>service_account_email</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>service account email (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>size_gb</td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td>whole integer size of disk (in GB) to create, default is 10 GB</td>
    </tr>
            <tr>
    <td>snapshot</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the source snapshot to use for the disk (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li></ul></td>
        <td>desired state of the persistent disk</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td>us-central1-b</td>
        <td><ul></ul></td>
        <td>zone in which to create the disk</td>
    </tr>
        </table>


.. note:: Requires libcloud


Examples
--------

.. raw:: html

    <br/>


::

    # Simple attachment action to an existing instance
    - local_action:
        module: gce_pd
        instance_name: notlocalhost
        size_gb: 5
        name: pd



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

