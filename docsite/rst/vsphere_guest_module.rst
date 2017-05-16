.. _vsphere_guest:


vsphere_guest - Create/delete/manage a guest VM through VMware vSphere.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Create/delete/reconfigure a guest VM through VMware vSphere. This module has a dependency on pysphere >= 1.7

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
    <td>cluster</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of the cluster to create the VM in. By default this is derived from the host you tell the module to build the guest on.</td>
    </tr>
            <tr>
    <td>esxi</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Dictionary which includes datacenter and hostname on which the VM should be created. For standalone ESXi hosts, ha-datacenter should be used as the datacenter name</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Boolean. Allows you to run commands which may alter the running state of a guest. Also used to reconfigure and destroy.</td>
    </tr>
            <tr>
    <td>guest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The virtual server name you wish to manage.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Password of the user to connect to vcenter as.</td>
    </tr>
            <tr>
    <td>resource_pool</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of the resource_pool to create the VM in.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>powered_on</li><li>absent</li><li>powered_off</li><li>restarted</li><li>reconfigured</li></ul></td>
        <td>Indicate desired state of the vm.</td>
    </tr>
            <tr>
    <td>username</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Username to connect to vcenter as.</td>
    </tr>
            <tr>
    <td>vcenter_hostname</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The hostname of the vcenter server the module will connect to, to create the guest.</td>
    </tr>
            <tr>
    <td>vm_disk</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A key, value list of disks and their sizes and which datastore to keep it in.</td>
    </tr>
            <tr>
    <td>vm_extra_config</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A key, value pair of any extra values you want set or changed in the vmx file of the VM. Useful to set advanced options on the VM.</td>
    </tr>
            <tr>
    <td>vm_hardware</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A key, value list of VM config settings. Must include ['memory_mb', 'num_cpus', 'osid', 'scsi'].</td>
    </tr>
            <tr>
    <td>vm_hw_version</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Desired hardware version identifier (for example, "vmx-08" for vms that needs to be managed with vSphere Client). Note that changing hardware version of existing vm is not supported. (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>vm_nic</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A key, value list of nics, their types and what network to put them on.</td>
    </tr>
            <tr>
    <td>vmware_guest_facts</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Gather facts from vCenter on a particular VM</td>
    </tr>
        </table>


.. note:: Requires pysphere


Examples
--------

.. raw:: html

    <br/>


::

    # Create a new VM on an ESX server
    # Returns changed = False when the VM already exists
    # Returns changed = True and a adds ansible_facts from the new VM
    # State will set the power status of a guest upon creation. Use powered_on to create and boot.
    # Options ['state', 'vm_extra_config', 'vm_disk', 'vm_nic', 'vm_hardware', 'esxi'] are required together
    
    - vsphere_guest:
        vcenter_hostname: vcenter.mydomain.local
        username: myuser
        password: mypass
        guest: newvm001
        state: powered_on
        vm_extra_config:
          vcpu.hotadd: yes
          mem.hotadd:  yes
          notes: This is a test VM
        vm_disk:
          disk1:
            size_gb: 10
            type: thin
            datastore: storage001
        vm_nic:
          nic1:
            type: vmxnet3
            network: VM Network
            network_type: standard
        vm_hardware:
          memory_mb: 2048
          num_cpus: 2
          osid: centos64Guest
          scsi: paravirtual
        esxi:
          datacenter: MyDatacenter
          hostname: esx001.mydomain.local
    
    # Reconfigure the CPU and Memory on the newly created VM
    # Will return the changes made
    
    - vsphere_guest:
        vcenter_hostname: vcenter.mydomain.local
        username: myuser
        password: mypass
        guest: newvm001
        state: reconfigured
        vm_extra_config:
          vcpu.hotadd: yes
          mem.hotadd:  yes
          notes: This is a test VM
        vm_disk:
          disk1:
            size_gb: 10
            type: thin
            datastore: storage001
        vm_nic:
          nic1:
            type: vmxnet3
            network: VM Network
            network_type: standard
        vm_hardware:
          memory_mb: 4096
          num_cpus: 4
          osid: centos64Guest
          scsi: paravirtual
        esxi:
          datacenter: MyDatacenter
          hostname: esx001.mydomain.local
    
    # Task to gather facts from a vSphere cluster only if the system is a VMWare guest
    
    - vsphere_guest:
        vcenter_hostname: vcenter.mydomain.local
        username: myuser
        password: mypass
        guest: newvm001
        vmware_guest_facts: yes
    
    
    # Typical output of a vsphere_facts run on a guest
    
    - hw_eth0:
      - addresstype: "assigned"
        label: "Network adapter 1"
        macaddress: "00:22:33:33:44:55"
        macaddress_dash: "00-22-33-33-44-55"
        summary: "VM Network"
      hw_guest_full_name: "newvm001"
      hw_guest_id: "rhel6_64Guest"
      hw_memtotal_mb: 2048
      hw_name: "centos64Guest"
      hw_processor_count: 2
      hw_product_uuid: "ef50bac8-2845-40ff-81d9-675315501dac"
    
    # Remove a vm from vSphere
    # The VM must be powered_off or you need to use force to force a shutdown
    
    - vsphere_guest:
        vcenter_hostname: vcenter.mydomain.local
        username: myuser
        password: mypass
        guest: newvm001
        state: absent
        force: yes

.. note:: This module should run from a system that can access vSphere directly. Either by using local_action, or using delegate_to.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

