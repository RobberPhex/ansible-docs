.. _vsphere_guest:


vsphere_guest - Create/delete/manage a guest VM through VMware vSphere.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create/delete/reconfigure a guest VM through VMware vSphere. This module has a dependency on pysphere >= 1.7


Requirements
------------

  * python >= 2.6
  * pysphere


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
    <td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the cluster to create the VM in. By default this is derived from the host you tell the module to build the guest on.</div></td></tr>
            <tr>
    <td>esxi<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary which includes datacenter and hostname on which the VM should be created. For standalone ESXi hosts, ha-datacenter should be used as the datacenter name</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Boolean. Allows you to run commands which may alter the running state of a guest. Also used to reconfigure and destroy.</div></td></tr>
            <tr>
    <td>from_template<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies if the VM should be deployed from a template (mutually exclusive with 'state' parameter). No guest customization changes to hardware such as CPU, RAM, NICs or Disks can be applied when launching from template.</div></td></tr>
            <tr>
    <td>guest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The virtual server name you wish to manage.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password of the user to connect to vcenter as.</div></td></tr>
            <tr>
    <td>power_on_after_clone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies if the VM should be powered on after the clone.</div></td></tr>
            <tr>
    <td>resource_pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the resource_pool to create the VM in.</div></td></tr>
            <tr>
    <td>snapshot_to_clone<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>A string that when specified, will create a linked clone copy of the VM. Snapshot must already be taken in vCenter.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>powered_off</li><li>absent</li><li>powered_on</li><li>restarted</li><li>reconfigured</li></ul></td>
        <td><div>Indicate desired state of the vm. 'reconfigured' only applies changes to 'memory_mb' and 'num_cpus' in vm_hardware parameter, and only when hot-plugging is enabled for the guest.</div></td></tr>
            <tr>
    <td>template_src<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the source template to deploy from</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username to connect to vcenter as.</div></td></tr>
            <tr>
    <td>vcenter_hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname of the vcenter server the module will connect to, to create the guest.</div></td></tr>
            <tr>
    <td>vm_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A key, value list of disks and their sizes and which datastore to keep it in.</div></td></tr>
            <tr>
    <td>vm_extra_config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A key, value pair of any extra values you want set or changed in the vmx file of the VM. Useful to set advanced options on the VM.</div></td></tr>
            <tr>
    <td>vm_hardware<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A key, value list of VM config settings. Must include ['memory_mb', 'num_cpus', 'osid', 'scsi'].</div></td></tr>
            <tr>
    <td>vm_hw_version<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Desired hardware version identifier (for example, "vmx-08" for vms that needs to be managed with vSphere Client). Note that changing hardware version of existing vm is not supported.</div></td></tr>
            <tr>
    <td>vm_nic<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A key, value list of nics, their types and what network to put them on.</div></td></tr>
            <tr>
    <td>vmware_guest_facts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Gather facts from vCenter on a particular VM</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new VM on an ESX server
    # Returns changed = False when the VM already exists
    # Returns changed = True and a adds ansible_facts from the new VM
    # State will set the power status of a guest upon creation. Use powered_on to create and boot.
    # Options ['state', 'vm_extra_config', 'vm_disk', 'vm_nic', 'vm_hardware', 'esxi'] are required together
    # Note: vm_floppy support added in 2.0
    
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
          nic2:
            type: vmxnet3
            network: dvSwitch Network
            network_type: dvs
        vm_hardware:
          memory_mb: 2048
          num_cpus: 2
          osid: centos64Guest
          scsi: paravirtual
          vm_cdrom:
            type: "iso"
            iso_path: "DatastoreName/cd-image.iso"
          vm_floppy:
            type: "image"
            image_path: "DatastoreName/floppy-image.flp"
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
    
    # Deploy a guest from a template
    - vsphere_guest:
        vcenter_hostname: vcenter.mydomain.local
        username: myuser
        password: mypass
        guest: newvm001
        from_template: yes
        template_src: centosTemplate
        cluster: MainCluster
        resource_pool: "/Resources"
    
    # Task to gather facts from a vSphere cluster only if the system is a VMWare guest
    
    - vsphere_guest:
        vcenter_hostname: vcenter.mydomain.local
        username: myuser
        password: mypass
        guest: newvm001
        vmware_guest_facts: yes
    
    
    # Typical output of a vsphere_facts run on a guest
    # If vmware tools is not installed, ipadresses with return None
    
    - hw_eth0:
      - addresstype: "assigned"
        label: "Network adapter 1"
        macaddress: "00:22:33:33:44:55"
        macaddress_dash: "00-22-33-33-44-55"
        ipaddresses: ['192.0.2.100', '2001:DB8:56ff:feac:4d8a']
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


Notes
-----

.. note:: This module should run from a system that can access vSphere directly. Either by using local_action, or using delegate_to.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

