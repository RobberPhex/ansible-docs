.. _gce:


gce - create or terminate GCE instances
+++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Creates or terminates Google Compute Engine (GCE) instances.  See https://cloud.google.com/products/compute-engine for an overview. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.

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
    <td>disk_auto_delete</td>
    <td>no</td>
    <td>true</td>
        <td><ul></ul></td>
        <td>if set boot disk will be removed after instance destruction (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>disks</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a list of persistent disks to attach to the instance; a string value gives the name of the disk; alternatively, a dictionary value can define 'name' and 'mode' ('READ_ONLY' or 'READ_WRITE'). The first entry will be the boot disk (which must be READ_WRITE). (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>external_ip</td>
    <td>no</td>
    <td>ephemeral</td>
        <td><ul></ul></td>
        <td>type of external ip, ephemeral by default (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>image</td>
    <td>no</td>
    <td>debian-7</td>
        <td><ul></ul></td>
        <td>image string to use for the instance</td>
    </tr>
            <tr>
    <td>instance_names</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a comma-separated list of instance names to create or destroy</td>
    </tr>
            <tr>
    <td>ip_forward</td>
    <td>no</td>
    <td>false</td>
        <td><ul></ul></td>
        <td>set to true if the instance can forward ip packets (useful for gateways) (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>machine_type</td>
    <td>no</td>
    <td>n1-standard-1</td>
        <td><ul></ul></td>
        <td>machine type to use for the instance, use 'n1-standard-1' by default</td>
    </tr>
            <tr>
    <td>metadata</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a hash/dictionary of custom data for the instance; '{"key":"value",...}'</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>identifier when working with a single instance</td>
    </tr>
            <tr>
    <td>network</td>
    <td>no</td>
    <td>default</td>
        <td><ul></ul></td>
        <td>name of the network, 'default' will be used if not specified</td>
    </tr>
            <tr>
    <td>pem_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to the pem file associated with the service account email (added in Ansible 1.5.1)</td>
    </tr>
            <tr>
    <td>persistent_boot_disk</td>
    <td>no</td>
    <td>false</td>
        <td><ul></ul></td>
        <td>if set, create the instance with a persistent boot disk</td>
    </tr>
            <tr>
    <td>project_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>your GCE project ID (added in Ansible 1.5.1)</td>
    </tr>
            <tr>
    <td>service_account_email</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>service account email (added in Ansible 1.5.1)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li></ul></td>
        <td>desired state of the resource</td>
    </tr>
            <tr>
    <td>tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a comma-separated list of tags to associate with the instance</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>yes</td>
    <td>us-central1-a</td>
        <td><ul></ul></td>
        <td>the GCE zone to use</td>
    </tr>
        </table>


.. note:: Requires libcloud


Examples
--------

.. raw:: html

    <br/>


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
    

.. note:: Either *name* or *instance_names* is required.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

