.. _gce_pd:


gce_pd - utilize GCE persistent disk resources
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module can create and destroy unformatted GCE persistent disks https://developers.google.com/compute/docs/disks#persistentdisks. It also supports attaching and detaching disks from running instances. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 0.13.3, >= 0.17.0 if using JSON credentials


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
    <td>credentials_file<br/><div style="font-size: small;"> (added in 2.1.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the JSON file associated with the service account email</div></td></tr>
            <tr>
    <td>detach_only<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>do not destroy the disk, merely detach it from an instance</div></td></tr>
            <tr>
    <td>disk_type<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>pd-standard</td>
        <td><ul><li>pd-standard</li><li>pd-ssd</li></ul></td>
        <td><div>type of disk provisioned</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the source image to use for the disk</div></td></tr>
            <tr>
    <td>instance_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>instance name if you wish to attach or detach the disk</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>READ_ONLY</td>
        <td><ul><li>READ_WRITE</li><li>READ_ONLY</li></ul></td>
        <td><div>GCE mount mode of disk, READ_ONLY (default) or READ_WRITE</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the disk</div></td></tr>
            <tr>
    <td>pem_file<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the pem file associated with the service account email This option is deprecated. Use 'credentials_file'.</div></td></tr>
            <tr>
    <td>project_id<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>your GCE project ID</div></td></tr>
            <tr>
    <td>service_account_email<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>service account email</div></td></tr>
            <tr>
    <td>size_gb<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>whole integer size of disk (in GB) to create, default is 10 GB</div></td></tr>
            <tr>
    <td>snapshot<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the source snapshot to use for the disk</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li></ul></td>
        <td><div>desired state of the persistent disk</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us-central1-b</td>
        <td><ul></ul></td>
        <td><div>zone in which to create the disk</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Simple attachment action to an existing instance
    - local_action:
        module: gce_pd
        instance_name: notlocalhost
        size_gb: 5
        name: pd




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

