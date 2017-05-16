.. _nova_compute:


nova_compute - Create/Delete VMs from OpenStack
+++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Create or Remove virtual machines from Openstack.

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
    <td>auth_url</td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td><ul></ul></td>
        <td>The keystone url for authentication</td>
    </tr>
            <tr>
    <td>auto_floating_ip</td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td>Should a floating ip be auto created and assigned (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>availability_zone</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Name of the availability zone (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>config_drive</td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td>Whether to boot the server with config drive enabled (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>flavor_id</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>The id of the flavor in which the new VM has to be created. Mutually exclusive with flavor_ram</td>
    </tr>
            <tr>
    <td>flavor_include</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Text to use to filter flavor names, for the case, such as Rackspace, where there are multiple flavors that have the same ram count. flavor_include is a positive match filter - it must exist in the flavor name. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>flavor_ram</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>The minimum amount of ram in MB that the flavor in which the new VM has to be created must have. Mutually exclusive with flavor_id (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>floating_ip_pools</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>list of floating IP pools from which to choose a floating IP (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>floating_ips</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>list of valid floating IPs that pre-exist to assign to this node (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>image_exclude</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Text to use to filter image names, for the case, such as HP, where there are multiple image names matching the common identifying portions. image_exclude is a negative match filter - it is text that may not exist in the image name. Defaults to "(deprecated)" (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>image_id</td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The id of the base image to boot. Mutually exclusive with image_name</td>
    </tr>
            <tr>
    <td>image_name</td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of the base image to boot. Mutually exclusive with image_id (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>key_name</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The key pair name to be used when creating a VM</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td>Password of login user</td>
    </tr>
            <tr>
    <td>login_tenant_name</td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td>The tenant name of the login user</td>
    </tr>
            <tr>
    <td>login_username</td>
    <td>yes</td>
    <td>admin</td>
        <td><ul></ul></td>
        <td>login username to authenticate to keystone</td>
    </tr>
            <tr>
    <td>meta</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>A list of key value pairs that should be provided as a metadata to the new VM</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Name that has to be given to the instance</td>
    </tr>
            <tr>
    <td>nics</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>A list of network id's to which the VM's interface should be attached</td>
    </tr>
            <tr>
    <td>region_name</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Name of the region</td>
    </tr>
            <tr>
    <td>scheduler_hints</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Arbitrary key/value pairs to the scheduler for custom use (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>security_groups</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of the security group to which the VM should be added</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>user_data</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Opaque blob of data which is made available to the instance (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td>If the module should wait for the VM to be created.</td>
    </tr>
            <tr>
    <td>wait_for</td>
    <td>no</td>
    <td>180</td>
        <td><ul></ul></td>
        <td>The amount of time the module should wait for the VM to get into active state</td>
    </tr>
        </table>


.. note:: Requires novaclient


Examples
--------

.. raw:: html

    <br/>


::

    # Creates a new VM and attaches to a network and passes metadata to the instance
    - nova_compute:
           state: present
           login_username: admin
           login_password: admin
           login_tenant_name: admin
           name: vm1
           image_id: 4f905f38-e52a-43d2-b6ec-754a13ffb529
           key_name: ansible_key
           wait_for: 200
           flavor_id: 4
           nics:
             - net-id: 34605f38-e52a-25d2-b6ec-754a13ffb723
           meta:
             hostname: test1
             group: uge_master
    
    # Creates a new VM in HP Cloud AE1 region availability zone az2 and automatically assigns a floating IP
    - name: launch a nova instance
      hosts: localhost
      tasks:
      - name: launch an instance
        nova_compute:
          state: present
          login_username: username
          login_password: Equality7-2521
          login_tenant_name: username-project1
          name: vm1
          auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
          region_name: region-b.geo-1
          availability_zone: az2
          image_id: 9302692b-b787-4b52-a3a6-daebb79cb498
          key_name: test
          wait_for: 200
          flavor_id: 101
          security_groups: default
          auto_floating_ip: yes
    
    # Creates a new VM in HP Cloud AE1 region availability zone az2 and assigns a pre-known floating IP
    - name: launch a nova instance
      hosts: localhost
      tasks:
      - name: launch an instance
        nova_compute:
          state: present
          login_username: username
          login_password: Equality7-2521
          login_tenant_name: username-project1
          name: vm1
          auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
          region_name: region-b.geo-1
          availability_zone: az2
          image_id: 9302692b-b787-4b52-a3a6-daebb79cb498
          key_name: test
          wait_for: 200
          flavor_id: 101
          floating-ips:
            - 12.34.56.79
    
    # Creates a new VM with 4G of RAM on Ubuntu Trusty, ignoring deprecated images
    - name: launch a nova instance
      hosts: localhost
      tasks:
      - name: launch an instance
        nova_compute:
          name: vm1
          state: present
          login_username: username
          login_password: Equality7-2521
          login_tenant_name: username-project1
          auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
          region_name: region-b.geo-1
          image_name: Ubuntu Server 14.04
          image_exclude: deprecated
          flavor_ram: 4096
    
    # Creates a new VM with 4G of RAM on Ubuntu Trusty on a Rackspace Performance node in DFW
    - name: launch a nova instance
      hosts: localhost
      tasks:
      - name: launch an instance
        nova_compute:
          name: vm1
          state: present
          login_username: username
          login_password: Equality7-2521
          login_tenant_name: username-project1
          auth_url: https://identity.api.rackspacecloud.com/v2.0/
          region_name: DFW
          image_name: Ubuntu 14.04 LTS (Trusty Tahr) (PVHVM)
          flavor_ram: 4096
          flavor_include: Performance



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

