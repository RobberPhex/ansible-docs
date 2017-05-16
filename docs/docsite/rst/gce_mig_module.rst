.. _gce_mig:


gce_mig - Create, Update or Destroy a Managed Instance Group (MIG).
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, Update or Destroy a Managed Instance Group (MIG).  See https://cloud.google.com/compute/docs/instance-groups for an overview. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 1.2.0


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
                <tr><td>autoscaling<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A dictionary of configuration for the autoscaler. 'enabled (bool)', 'name (str)' and policy.max_instances (int) are required fields if autoscaling is used. See <a href='https://cloud.google.com/compute/docs/reference/beta/autoscalers'>https://cloud.google.com/compute/docs/reference/beta/autoscalers</a> for more information on Autoscaling.</div>        </td></tr>
                <tr><td>credentials_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to the JSON file associated with the service account email</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the Managed Instance Group.</div>        </td></tr>
                <tr><td>named_ports<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Define named ports that backend services can forward data to.  Format is a a list of name:port dictionaries.</div>        </td></tr>
                <tr><td>project_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>GCE project ID</div>        </td></tr>
                <tr><td>service_account_email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>service account email</div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Size of Managed Instance Group.  If MIG already exists, it will be resized to the number provided here.  Required for creating MIGs.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>desired state of the resource</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Instance Template to be used in creating the VMs.  See <a href='https://cloud.google.com/compute/docs/instance-templates'>https://cloud.google.com/compute/docs/instance-templates</a> to learn more about Instance Templates.  Required for creating MIGs.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The GCE zone to use for this Managed Instance Group.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Following playbook creates, rebuilds instances, resizes and then deletes a MIG.
    # Notes:
    # - Two valid Instance Templates must exist in your GCE project in order to run
    #   this playbook.  Change the fields to match the templates used in your
    #   project.
    # - The use of the 'pause' module is not required, it is just for convenience.
    - name: Managed Instance Group Example
      hosts: localhost
      gather_facts: False
      tasks:
        - name: Create MIG
          gce_mig:
            name: ansible-mig-example
            zone: us-central1-c
            state: present
            size: 1
            template: my-instance-template-1
            named_ports:
            - name: http
              port: 80
            - name: foobar
              port: 82
    
        - name: Pause for 30 seconds
          pause:
            seconds: 30
    
        - name: Recreate MIG Instances with Instance Template change.
          gce_mig:
            name: ansible-mig-example
            zone: us-central1-c
            state: present
            template: my-instance-template-2-small
            recreate_instances: yes
    
        - name: Pause for 30 seconds
          pause:
            seconds: 30
    
        - name: Resize MIG
          gce_mig:
            name: ansible-mig-example
            zone: us-central1-c
            state: present
            size: 3
    
        - name: Update MIG with Autoscaler
          gce_mig:
            name: ansible-mig-example
            zone: us-central1-c
            state: present
            size: 3
            template: my-instance-template-2-small
            recreate_instances: yes
            autoscaling:
              enabled: yes
              name: my-autoscaler
              policy:
                min_instances: 2
                max_instances: 5
                cool_down_period: 37
                cpu_utilization:
                  target: .39
                load_balancing_utilization:
                  target: 0.4
    
        - name: Pause for 30 seconds
          pause:
            seconds: 30
    
        - name: Delete MIG
          gce_mig:
            name: ansible-mig-example
            zone: us-central1-c
            state: absent
            autoscaling:
              enabled: no
              name: my-autoscaler

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
        <td> set_named_ports </td>
        <td> True if the named_ports have been set </td>
        <td align=center> named_ports have been set </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> deleted_instances </td>
        <td> Names of instances deleted. </td>
        <td align=center> When instances are deleted. </td>
        <td align=center> list </td>
        <td align=center> ['ansible-mig-new-0k4y', 'ansible-mig-new-0zk5', 'ansible-mig-new-kp68'] </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the Managed Instance Group. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> my-managed-instance-group </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Zone in which to launch MIG. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> us-central1-b </td>
    </tr>
            <tr>
        <td> created_instances </td>
        <td> Names of instances created. </td>
        <td align=center> When instances are created. </td>
        <td align=center> list </td>
        <td align=center> ['ansible-mig-new-0k4y', 'ansible-mig-new-0zk5', 'ansible-mig-new-kp68'] </td>
    </tr>
            <tr>
        <td> resize_deleted_instances </td>
        <td> Names of instances deleted during resizing. </td>
        <td align=center> When a resize results in the deletion of instances. </td>
        <td align=center> list </td>
        <td align=center> ['ansible-mig-new-0k4y', 'ansible-mig-new-0zk5', 'ansible-mig-new-kp68'] </td>
    </tr>
            <tr>
        <td> created_autoscaler </td>
        <td> True if Autoscaler was attempted and created.  False otherwise. </td>
        <td align=center> When the creation of an Autoscaler was attempted. </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> named_ports </td>
        <td> list of named ports acted upon </td>
        <td align=center> when named_ports are initially set or updated </td>
        <td align=center> list </td>
        <td align=center> [{'name': 'http', 'port': 80}, {'name': 'foo', 'port': 82}] </td>
    </tr>
            <tr>
        <td> recreated_instances </td>
        <td> Names of instances recreated. </td>
        <td align=center> When instances are recreated. </td>
        <td align=center> list </td>
        <td align=center> ['ansible-mig-new-0k4y', 'ansible-mig-new-0zk5', 'ansible-mig-new-kp68'] </td>
    </tr>
            <tr>
        <td> template </td>
        <td> Instance Template to use for VMs.  Must exist prior to using with MIG. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> my-instance-template </td>
    </tr>
            <tr>
        <td> updated_autoscaler </td>
        <td> True if an Autoscaler update was attempted and succeeded. False returned if update failed. </td>
        <td align=center> When the update of an Autoscaler was attempted. </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> updated_named_ports </td>
        <td> True if the named_ports have been updated </td>
        <td align=center> named_ports have been updated </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> resize_created_instances </td>
        <td> Names of instances created during resizing. </td>
        <td align=center> When a resize results in the creation of instances. </td>
        <td align=center> list </td>
        <td align=center> ['ansible-mig-new-0k4y', 'ansible-mig-new-0zk5', 'ansible-mig-new-kp68'] </td>
    </tr>
            <tr>
        <td> deleted_autoscaler </td>
        <td> True if an Autoscaler delete attempted and succeeded. False returned if delete failed. </td>
        <td align=center> When the delete of an Autoscaler was attempted. </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> size </td>
        <td> Number of VMs in Managed Instance Group. </td>
        <td align=center> changed </td>
        <td align=center> integer </td>
        <td align=center> 4 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Resizing and Recreating VM are also supported.
    - An existing instance template is required in order to create a Managed Instance Group.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
