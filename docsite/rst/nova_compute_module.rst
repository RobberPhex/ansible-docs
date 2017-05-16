.. _nova_compute:


nova_compute - Create/Delete VMs from OpenStack
+++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1

DEPRECATED
----------

Deprecated in 2.0. Use os_server instead

Synopsis
--------

Create or Remove virtual machines from Openstack.


Requirements
------------

  * python >= 2.6
  * python-novaclient


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
    <td>auth_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td><ul></ul></td>
        <td><div>The keystone url for authentication</div></td></tr>
            <tr>
    <td>auto_floating_ip<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td><div>Should a floating ip be auto created and assigned</div></td></tr>
            <tr>
    <td>availability_zone<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the availability zone</div></td></tr>
            <tr>
    <td>config_drive<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td><div>Whether to boot the server with config drive enabled</div></td></tr>
            <tr>
    <td>flavor_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The id of the flavor in which the new VM has to be created. Mutually exclusive with flavor_ram</div></td></tr>
            <tr>
    <td>flavor_include<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Text to use to filter flavor names, for the case, such as Rackspace, where there are multiple flavors that have the same ram count. flavor_include is a positive match filter - it must exist in the flavor name.</div></td></tr>
            <tr>
    <td>flavor_ram<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The minimum amount of ram in MB that the flavor in which the new VM has to be created must have. Mutually exclusive with flavor_id</div></td></tr>
            <tr>
    <td>floating_ip_pools<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>list of floating IP pools from which to choose a floating IP</div></td></tr>
            <tr>
    <td>floating_ips<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>list of valid floating IPs that pre-exist to assign to this node</div></td></tr>
            <tr>
    <td>image_exclude<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Text to use to filter image names, for the case, such as HP, where there are multiple image names matching the common identifying portions. image_exclude is a negative match filter - it is text that may not exist in the image name. Defaults to "(deprecated)"</div></td></tr>
            <tr>
    <td>image_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The id of the base image to boot. Mutually exclusive with image_name</div></td></tr>
            <tr>
    <td>image_name<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the base image to boot. Mutually exclusive with image_id</div></td></tr>
            <tr>
    <td>key_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The key pair name to be used when creating a VM</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>Password of login user</div></td></tr>
            <tr>
    <td>login_tenant_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>The tenant name of the login user</div></td></tr>
            <tr>
    <td>login_username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>admin</td>
        <td><ul></ul></td>
        <td><div>login username to authenticate to keystone</div></td></tr>
            <tr>
    <td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of key value pairs that should be provided as a metadata to the new VM</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name that has to be given to the instance</div></td></tr>
            <tr>
    <td>nics<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of network id's to which the VM's interface should be attached</div></td></tr>
            <tr>
    <td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the region</div></td></tr>
            <tr>
    <td>scheduler_hints<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Arbitrary key/value pairs to the scheduler for custom use</div></td></tr>
            <tr>
    <td>security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the security group to which the VM should be added</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>user_data<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Opaque blob of data which is made available to the instance</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>If the module should wait for the VM to be created.</div></td></tr>
            <tr>
    <td>wait_for<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td><ul></ul></td>
        <td><div>The amount of time the module should wait for the VM to get into active state</div></td></tr>
        </table>
    </br>



Examples
--------

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





For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

