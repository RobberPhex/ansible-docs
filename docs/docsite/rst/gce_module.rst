.. _gce:


gce - create or terminate GCE instances
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates or terminates Google Compute Engine (GCE) instances.  See https://cloud.google.com/compute for an overview. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 0.13.3, >= 0.17.0 if using JSON credentials, >= 0.20.0 if using preemptible option


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
                <tr><td>credentials_file<br/><div style="font-size: small;"> (added in 2.1.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to the JSON file associated with the service account email</div>        </td></tr>
                <tr><td>disk_auto_delete<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>true</td>
        <td></td>
        <td><div>if set boot disk will be removed after instance destruction</div>        </td></tr>
                <tr><td>disk_size<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>The size of the boot disk created for this instance (in GB)</div>        </td></tr>
                <tr><td>disks<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a list of persistent disks to attach to the instance; a string value gives the name of the disk; alternatively, a dictionary value can define 'name' and 'mode' ('READ_ONLY' or 'READ_WRITE'). The first entry will be the boot disk (which must be READ_WRITE).</div>        </td></tr>
                <tr><td>external_ip<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>ephemeral</td>
        <td></td>
        <td><div>type of external ip, ephemeral by default; alternatively, a fixed gce ip or ip name can be given. Specify 'none' if no external ip is desired.</div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>debian-8</td>
        <td></td>
        <td><div>image string to use for the instance (default will follow latest stable debian image)</div>        </td></tr>
                <tr><td>instance_names<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a comma-separated list of instance names to create or destroy</div>        </td></tr>
                <tr><td>ip_forward<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>false</td>
        <td></td>
        <td><div>set to true if the instance can forward ip packets (useful for gateways)</div>        </td></tr>
                <tr><td>machine_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>n1-standard-1</td>
        <td></td>
        <td><div>machine type to use for the instance, use 'n1-standard-1' by default</div>        </td></tr>
                <tr><td>metadata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a hash/dictionary of custom data for the instance; '{"key":"value", ...}'</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>either a name of a single instance or when used with 'num_instances', the base name of a cluster of nodes</div></br>
    <div style="font-size: small;">aliases: base_name<div>        </td></tr>
                <tr><td>network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default</td>
        <td></td>
        <td><div>name of the network, 'default' will be used if not specified</div>        </td></tr>
                <tr><td>num_instances<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>can be used with 'name', specifies the number of nodes to provision using 'name' as a base name</div>        </td></tr>
                <tr><td>pem_file<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to the pem file associated with the service account email This option is deprecated. Use 'credentials_file'.</div>        </td></tr>
                <tr><td>persistent_boot_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>false</td>
        <td></td>
        <td><div>if set, create the instance with a persistent boot disk</div>        </td></tr>
                <tr><td>preemptible<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>false</td>
        <td></td>
        <td><div>if set to true, instances will be preemptible and time-limited. (requires libcloud &gt;= 0.20.0)</div>        </td></tr>
                <tr><td>project_id<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>your GCE project ID</div>        </td></tr>
                <tr><td>service_account_email<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>service account email</div>        </td></tr>
                <tr><td>service_account_permissions<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>bigquery</li><li>cloud-platform</li><li>compute-ro</li><li>compute-rw</li><li>useraccounts-ro</li><li>useraccounts-rw</li><li>datastore</li><li>logging-write</li><li>monitoring</li><li>sql-admin</li><li>storage-full</li><li>storage-ro</li><li>storage-rw</li><li>taskqueue</li><li>userinfo-email</li></ul></td>
        <td><div>service account permissions (see <a href='https://cloud.google.com/sdk/gcloud/reference/compute/instances/create'>https://cloud.google.com/sdk/gcloud/reference/compute/instances/create</a>, --scopes section for detailed information)</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li><li>started</li><li>stopped</li><li>terminated</li></ul></td>
        <td><div>desired state of the resource</div>        </td></tr>
                <tr><td>subnetwork<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>name of the subnetwork in which the instance should be created</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a comma-separated list of tags to associate with the instance</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>us-central1-a</td>
        <td></td>
        <td><div>the GCE zone to use</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic provisioning example.  Create a single Debian 8 instance in the
    # us-central1-a Zone of the n1-standard-1 machine type.
    # Create multiple instances by specifying multiple names, seperated by
    # commas in the instance_names field
    # (e.g. my-test-instance1,my-test-instance2)
        gce:
          instance_names: my-test-instance1
          zone: us-central1-a
          machine_type: n1-standard-1
          image: debian-8
          state: present
          service_account_email: "your-sa@your-project-name.iam.gserviceaccount.com"
          credentials_file: "/path/to/your-key.json"
          project_id: "your-project-name"
          disk_size: 32
    
    # Create a single Debian 8 instance in the us-central1-a Zone
    # Use existing disks, custom network/subnetwork, set service account permissions
    # add tags and metadata.
        gce:
          instance_names: my-test-instance
          zone: us-central1-a
          machine_type: n1-standard-1
          state: present
          metadata: '{"db":"postgres", "group":"qa", "id":500}'
          tags:
            - http-server
            - my-other-tag
          disks:
            - name: disk-2
              mode: READ_WRITE
            - name: disk-3
              mode: READ_ONLY
          disk_auto_delete: false
          network: foobar-network
          subnetwork: foobar-subnetwork-1
          preemptible: true
          ip_forward: true
          service_account_permissions:
            - storage-full
            - taskqueue
            - bigquery
          service_account_email: "your-sa@your-project-name.iam.gserviceaccount.com"
          credentials_file: "/path/to/your-key.json"
          project_id: "your-project-name"
    
    ---
    # Example Playbook
    - name: Compute Engine Instance Examples
      hosts: localhost
      vars:
        service_account_email: "your-sa@your-project-name.iam.gserviceaccount.com"
        credentials_file: "/path/to/your-key.json"
        project_id: "your-project-name"
      tasks:
        - name: create multiple instances
          # Basic provisioning example.  Create multiple Debian 8 instances in the
          # us-central1-a Zone of n1-standard-1 machine type.
          gce:
            instance_names: test1,test2,test3
            zone: us-central1-a
            machine_type: n1-standard-1
            image: debian-8
            state: present
            service_account_email: "{{ service_account_email }}"
            credentials_file: "{{ credentials_file }}"
            project_id: "{{ project_id }}"
            metadata : '{ "startup-script" : "apt-get update" }'
          register: gce
    
        - name: Save host data
          add_host:
            hostname: "{{ item.public_ip }}"
            groupname: gce_instances_ips
          with_items: "{{ gce.instance_data }}"
    
        - name: Wait for SSH for instances
          wait_for:
            delay: 1
            host: "{{ item.public_ip }}"
            port: 22
            state: started
            timeout: 30
          with_items: "{{ gce.instance_data }}"
    
        - name: Configure Hosts
          hosts: gce_instances_ips
          become: yes
          become_method: sudo
          roles:
            - my-role-one
            - my-role-two
          tags:
            - config
    
        - name: delete test-instances
          # Basic termination of instance.
          gce:
            service_account_email: "{{ service_account_email }}"
            credentials_file: "{{ credentials_file }}"
            project_id: "{{ project_id }}"
            instance_names: "{{ gce.instance_names }}"
            zone: us-central1-a
            state: absent
          tags:
            - delete


Notes
-----

.. note::
    - Either *instance_names* or *name* is required.
    - JSON credentials strongly preferred.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
