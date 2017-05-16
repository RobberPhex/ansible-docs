.. _gce_instance_template:


gce_instance_template - create or destroy intance templates of Compute Engine of GCP.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates or destroy Google instance templates of Compute Engine of Google Cloud Platform.


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
                <tr><td>automatic_restart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Defines whether the instance should be automatically restarted when it is terminated by Compute Engine.</div>        </td></tr>
                <tr><td>can_ip_forward<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set to True to allow instance to send/receive non-matching src/dst packets.</div>        </td></tr>
                <tr><td>credentials_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to the JSON file associated with the service account email</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>description of instance template</div>        </td></tr>
                <tr><td>disk_auto_delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Indicate that the boot disk should be deleted when the Node is deleted.</div>        </td></tr>
                <tr><td>disk_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>pd-standard</td>
        <td></td>
        <td><div>Specify a <code>pd-standard</code> disk or <code>pd-ssd</code> for an SSD disk.</div>        </td></tr>
                <tr><td>disks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a list of persistent disks to attach to the instance; a string value gives the name of the disk; alternatively, a dictionary value can define 'name' and 'mode' ('READ_ONLY' or 'READ_WRITE'). The first entry will be the boot disk (which must be READ_WRITE).</div>        </td></tr>
                <tr><td>external_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ephemeral</td>
        <td></td>
        <td><div>The external IP address to use. If <code>ephemeral</code>, a new non-static address will be used.  If <code>None</code>, then no external address will be used.  To use an existing static IP address specify adress name.</div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The image to use to create the instance. Cannot specify both both <em>image</em> and <em>source</em>.</div>        </td></tr>
                <tr><td>image_family<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The image family to use to create the instance. If <em>image</em> has been used <em>image_family</em> is ignored. Cannot specify both <em>image</em> and <em>source</em>.</div>        </td></tr>
                <tr><td>metadata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a hash/dictionary of custom data for the instance; '{"key":"value", ...}'</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the GCE instance template.</div>        </td></tr>
                <tr><td>network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default</td>
        <td></td>
        <td><div>The network to associate with the instance.</div>        </td></tr>
                <tr><td>nic_gce_struct<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Support passing in the GCE-specific formatted networkInterfaces[] structure.</div>        </td></tr>
                <tr><td>pem_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to the pem file associated with the service account email This option is deprecated. Use 'credentials_file'.</div>        </td></tr>
                <tr><td>preemptible<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Defines whether the instance is preemptible.</div>        </td></tr>
                <tr><td>project_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>your GCE project ID</div>        </td></tr>
                <tr><td>service_account_email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>service account email</div>        </td></tr>
                <tr><td>service_account_permissions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>bigquery</li><li>cloud-platform</li><li>compute-ro</li><li>compute-rw</li><li>useraccounts-ro</li><li>useraccounts-rw</li><li>datastore</li><li>logging-write</li><li>monitoring</li><li>sql-admin</li><li>storage-full</li><li>storage-ro</li><li>storage-rw</li><li>taskqueue</li><li>userinfo-email</li></ul></td>
        <td><div>service account permissions (see <a href='https://cloud.google.com/sdk/gcloud/reference/compute/instances/create'>https://cloud.google.com/sdk/gcloud/reference/compute/instances/create</a>, --scopes section for detailed information)</div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>f1-micro</td>
        <td></td>
        <td><div>The desired machine type for the instance template.</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A source disk to attach to the instance. Cannot specify both <em>image</em> and <em>source</em>.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The desired state for the instance template.</div>        </td></tr>
                <tr><td>subnetwork<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Subnetwork resource name for this instance.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a comma-separated list of tags to associate with the instance</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Usage
    - name: create instance template named foo
      gce_instance_template:
        name: foo
        size: n1-standard-1
        image_family: ubuntu-1604-lts
        state: present
        project_id: "your-project-name"
        credentials_file: "/path/to/your-key.json"
        service_account_email: "your-sa@your-project-name.iam.gserviceaccount.com"
    
    # Example Playbook
    - name: Compute Engine Instance Template Examples
      hosts: localhost
      vars:
        service_account_email: "your-sa@your-project-name.iam.gserviceaccount.com"
        credentials_file: "/path/to/your-key.json"
        project_id: "your-project-name"
      tasks:
        - name: create instance template
          gce_instance_template:
            name: my-test-instance-template
            size: n1-standard-1
            image_family: ubuntu-1604-lts
            state: present
            project_id: "{{ project_id }}"
            credentials_file: "{{ credentials_file }}"
            service_account_email: "{{ service_account_email }}"
        - name: delete instance template
          gce_instance_template:
            name: my-test-instance-template
            size: n1-standard-1
            image_family: ubuntu-1604-lts
            state: absent
            project_id: "{{ project_id }}"
            credentials_file: "{{ credentials_file }}"
            service_account_email: "{{ service_account_email }}"


Notes
-----

.. note::
    - JSON credentials strongly preferred.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
