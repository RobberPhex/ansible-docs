.. _gce_snapshot:


gce_snapshot - Create or destroy snapshots for GCE storage volumes
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages snapshots for GCE instances. This module manages snapshots for the storage volumes of a GCE compute instance. If there are multiple volumes, each snapshot will be prepended with the disk name


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 0.19.0


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
                <tr><td>credentials_file<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The path to the credentials file associated with the service account</div>        </td></tr>
                <tr><td>disks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td></td>
        <td><div>A list of disks to create snapshots for. If none is provided, all of the volumes will be snapshotted</div>        </td></tr>
                <tr><td>instance_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The GCE instance to snapshot</div>        </td></tr>
                <tr><td>project_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The GCP project ID to use</div>        </td></tr>
                <tr><td>service_account_email<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>GCP service account email for the project where the instance resides</div>        </td></tr>
                <tr><td>snapshot_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the snapshot to manage</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether a snapshot should be <code>present</code> or <code>absent</code></div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create gce snapshot
      gce_snapshot:
        instance_name: example-instance
        snapshot_name: example-snapshot
        state: present
        service_account_email: project_name@appspot.gserviceaccount.com
        credentials_file: /path/to/credentials
        project_id: project_name
      delegate_to: localhost
    
    - name: Delete gce snapshot
      gce_snapshot:
        instance_name: example-instance
        snapshot_name: example-snapshot
        state: absent
        service_account_email: project_name@appspot.gserviceaccount.com
        credentials_file: /path/to/credentials
        project_id: project_name
      delegate_to: localhost
    
    # This example creates snapshots for only two of the available disks as
    # disk0-example-snapshot and disk1-example-snapshot
    - name: Create snapshots of specific disks
      gce_snapshot:
        instance_name: example-instance
        snapshot_name: example-snapshot
        state: present
        disks:
          - disk0
          - disk1
        service_account_email: project_name@appspot.gserviceaccount.com
        credentials_file: /path/to/credentials
        project_id: project_name
      delegate_to: localhost

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
        <td> snapshots_created </td>
        <td> List of newly created snapshots </td>
        <td align=center> When snapshots are created </td>
        <td align=center> list </td>
        <td align=center> [disk0-example-snapshot, disk1-example-snapshot] </td>
    </tr>
            <tr>
        <td> snapshots_deleted </td>
        <td> List of destroyed snapshots </td>
        <td align=center> When snapshots are deleted </td>
        <td align=center> list </td>
        <td align=center> [disk0-example-snapshot, disk1-example-snapshot] </td>
    </tr>
            <tr>
        <td> snapshots_absent </td>
        <td> List of snapshots that were already absent (no-op) </td>
        <td align=center> When snapshots were already absent </td>
        <td align=center> list </td>
        <td align=center> [disk0-example-snapshot, disk1-example-snapshot] </td>
    </tr>
            <tr>
        <td> snapshots_existing </td>
        <td> List of snapshots that already existed (no-op) </td>
        <td align=center> When snapshots were already present </td>
        <td align=center> list </td>
        <td align=center> [disk0-example-snapshot, disk1-example-snapshot] </td>
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
