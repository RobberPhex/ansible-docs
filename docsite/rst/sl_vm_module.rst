.. _sl_vm:


sl_vm - create or cancel a virtual instance in SoftLayer
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates or cancels SoftLayer instances. When created, optionally waits for it to be 'running'.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * softlayer >= 4.1.1


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
    <td>cpus<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Count of cpus to be assigned to new virtual instance</div></td></tr>
            <tr>
    <td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Datacenter for the virtual instance to be deployed</div></td></tr>
            <tr>
    <td>dedicated<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Falg to determine if the instance should be deployed in dedicated space</div></td></tr>
            <tr>
    <td>disks<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>[25]</td>
        <td><ul></ul></td>
        <td><div>List of disk sizes to be assigned to new virtual instance</div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain name to be provided to a virtual instance</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Hostname to be provided to a virtual instance</div></td></tr>
            <tr>
    <td>hourly<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Flag to determine if the instance should be hourly billed</div></td></tr>
            <tr>
    <td>image_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Image Template to be used for new virtual instance</div></td></tr>
            <tr>
    <td>instance_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Instance Id of the virtual instance to perform action option</div></td></tr>
            <tr>
    <td>local_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Flag to determine if local disk should be used for the new instance</div></td></tr>
            <tr>
    <td>memory<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Amount of memory to be assigned to new virtual instance</div></td></tr>
            <tr>
    <td>nic_speed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>NIC Speed to be assigned to new virtual instance</div></td></tr>
            <tr>
    <td>os_code<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>OS Code to be used for new virtual instance</div></td></tr>
            <tr>
    <td>post_uri<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL of a post provisioning script ot be loaded and exectued on virtual instance</div></td></tr>
            <tr>
    <td>private<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Flag to determine if the instance should be private only</div></td></tr>
            <tr>
    <td>private_vlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>VLAN by its Id to be assigned to the private NIC</div></td></tr>
            <tr>
    <td>public_vlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>VLAN by its Id to be assigned to the public NIC</div></td></tr>
            <tr>
    <td>ssh_keys<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of ssh keys by their Id to be assigned to a virtual instance</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul></ul></td>
        <td><div>Create, or cancel a virtual instance. Specify "present" for create, "absent" to cancel.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Tag or list of tags to be provided to a virtual instance</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Flag used to wait for active status before returning</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>time in seconds before wait returns</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Build instance
      hosts: localhost
      gather_facts: False
      tasks:
      - name: Build instance request
        local_action:
          module: sl_vm
          hostname: instance-1
          domain: anydomain.com
          datacenter: dal09
          tags: ansible-module-test
          hourly: True
          private: False
          dedicated: False
          local_disk: True
          cpus: 1
          memory: 1024
          disks: [25]
          os_code: UBUNTU_LATEST
          wait: False
    
    - name: Build additional instances
      hosts: localhost
      gather_facts: False
      tasks:
      - name: Build instances request
        local_action:
          module: sl_vm
          hostname: "{{ item.hostname }}"
          domain: "{{ item.domain }}"
          datacenter: "{{ item.datacenter }}"
          tags: "{{ item.tags }}"
          hourly: "{{ item.hourly }}"
          private: "{{ item.private }}"
          dedicated: "{{ item.dedicated }}"
          local_disk: "{{ item.local_disk }}"
          cpus: "{{ item.cpus }}"
          memory: "{{ item.memory }}"
          disks: "{{ item.disks }}"
          os_code: "{{ item.os_code }}"
          ssh_keys: "{{ item.ssh_keys }}"
          wait: "{{ item.wait }}"
        with_items:
          - { hostname: 'instance-2', domain: 'anydomain.com', datacenter: 'dal09', tags: ['ansible-module-test', 'ansible-module-test-slaves'], hourly: True, private: False, dedicated: False, local_disk: True, cpus: 1, memory: 1024, disks: [25,100], os_code: 'UBUNTU_LATEST', ssh_keys: [], wait: True }
          - { hostname: 'instance-3', domain: 'anydomain.com', datacenter: 'dal09', tags: ['ansible-module-test', 'ansible-module-test-slaves'], hourly: True, private: False, dedicated: False, local_disk: True, cpus: 1, memory: 1024, disks: [25,100], os_code: 'UBUNTU_LATEST', ssh_keys: [], wait: True }
    
    
    - name: Cancel instances
      hosts: localhost
      gather_facts: False
      tasks:
      - name: Cancel by tag
        local_action:
          module: sl_vm
          state: absent
          tags: ansible-module-test




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

