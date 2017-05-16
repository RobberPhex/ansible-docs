.. _gce:


gce - create or terminate GCE instances
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates or terminates Google Compute Engine (GCE) instances.  See https://cloud.google.com/products/compute-engine for an overview. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.


Requirements
------------

  * python >= 2.6
  * apache-libcloud >= 0.13.3


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
    <td>disk_auto_delete<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>true</td>
        <td><ul></ul></td>
        <td><div>if set boot disk will be removed after instance destruction</div></td></tr>
            <tr>
    <td>disks<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a list of persistent disks to attach to the instance; a string value gives the name of the disk; alternatively, a dictionary value can define 'name' and 'mode' ('READ_ONLY' or 'READ_WRITE'). The first entry will be the boot disk (which must be READ_WRITE).</div></td></tr>
            <tr>
    <td>external_ip<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>ephemeral</td>
        <td><ul></ul></td>
        <td><div>type of external ip, ephemeral by default</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>debian-7</td>
        <td><ul></ul></td>
        <td><div>image string to use for the instance</div></td></tr>
            <tr>
    <td>instance_names<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a comma-separated list of instance names to create or destroy</div></td></tr>
            <tr>
    <td>ip_forward<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>false</td>
        <td><ul></ul></td>
        <td><div>set to true if the instance can forward ip packets (useful for gateways)</div></td></tr>
            <tr>
    <td>machine_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>n1-standard-1</td>
        <td><ul></ul></td>
        <td><div>machine type to use for the instance, use 'n1-standard-1' by default</div></td></tr>
            <tr>
    <td>metadata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a hash/dictionary of custom data for the instance; '{"key":"value",...}'</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>identifier when working with a single instance</div></td></tr>
            <tr>
    <td>network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default</td>
        <td><ul></ul></td>
        <td><div>name of the network, 'default' will be used if not specified</div></td></tr>
            <tr>
    <td>pem_file<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the pem file associated with the service account email</div></td></tr>
            <tr>
    <td>persistent_boot_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>false</td>
        <td><ul></ul></td>
        <td><div>if set, create the instance with a persistent boot disk</div></td></tr>
            <tr>
    <td>project_id<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>your GCE project ID</div></td></tr>
            <tr>
    <td>service_account_email<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>service account email</div></td></tr>
            <tr>
    <td>service_account_permissions<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>bigquery</li><li>cloud-platform</li><li>compute-ro</li><li>compute-rw</li><li>computeaccounts-ro</li><li>computeaccounts-rw</li><li>datastore</li><li>logging-write</li><li>monitoring</li><li>sql</li><li>sql-admin</li><li>storage-full</li><li>storage-ro</li><li>storage-rw</li><li>taskqueue</li><li>userinfo-email</li></ul></td>
        <td><div>service account permissions (see <a href='https://cloud.google.com/sdk/gcloud/reference/compute/instances/create'>https://cloud.google.com/sdk/gcloud/reference/compute/instances/create</a>, --scopes section for detailed information)</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li></ul></td>
        <td><div>desired state of the resource</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a comma-separated list of tags to associate with the instance</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>us-central1-a</td>
        <td><ul></ul></td>
        <td><div>the GCE zone to use</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic provisioning example.  Create a single Debian 7 instance in the
    # us-central1-a Zone of n1-standard-1 machine type.
    - local_action:
        module: gce
        name: test-instance
        zone: us-central1-a
        machine_type: n1-standard-1
        image: debian-7
    
    # Example using defaults and with metadata to create a single 'foo' instance
    - local_action:
        module: gce
        name: foo
        metadata: '{"db":"postgres", "group":"qa", "id":500}'
    
    
    # Launch instances from a control node, runs some tasks on the new instances,
    # and then terminate them
    - name: Create a sandbox instance
      hosts: localhost
      vars:
        names: foo,bar
        machine_type: n1-standard-1
        image: debian-6
        zone: us-central1-a
        service_account_email: unique-email@developer.gserviceaccount.com
        pem_file: /path/to/pem_file
        project_id: project-id
      tasks:
        - name: Launch instances
          local_action: gce instance_names={{names}} machine_type={{machine_type}}
                        image={{image}} zone={{zone}} service_account_email={{ service_account_email }}
                        pem_file={{ pem_file }} project_id={{ project_id }}
          register: gce
        - name: Wait for SSH to come up
          local_action: wait_for host={{item.public_ip}} port=22 delay=10
                        timeout=60 state=started
          with_items: {{gce.instance_data}}
    
    - name: Configure instance(s)
      hosts: launched
      sudo: True
      roles:
        - my_awesome_role
        - my_awesome_tasks
    
    - name: Terminate instances
      hosts: localhost
      connection: local
      tasks:
        - name: Terminate instances that were previously launched
          local_action:
            module: gce
            state: 'absent'
            instance_names: {{gce.instance_names}}
    


Notes
-----

.. note:: Either *name* or *instance_names* is required.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

