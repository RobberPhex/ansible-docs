.. _vmware_guest:


vmware_guest - Manages virtual machines in vcenter
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create new virtual machines (from templates or not)
* Power on/power off/restart a virtual machine
* Modify, rename or remove a virtual machine


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * PyVmomi


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
                <tr><td>annotation<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A note or annotation to include in the VM</div>        </td></tr>
                <tr><td>cluster<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The cluster name where the VM will run.</div>        </td></tr>
                <tr><td>customization<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Parameters to customize template</div><div>Common parameters (Linux/Windows):</div><div>  dns_servers (list): List of DNS servers to configure</div><div>  dns_suffix (list): List of domain suffixes, aka DNS search path (default: <code>domain</code> parameter)</div><div>  domain (string): DNS domain name to use</div><div>  hostname (string): Computer hostname (default: <code>name</code> parameter)</div><div>Parameters related to windows customization:</div><div>  autologon (bool): Auto logon after VM customization (default: False)</div><div>  autologoncount (int): Number of autologon after reboot (default: 1)</div><div>  domainadmin (string): User used to join in AD domain (mandatory with joindomain)</div><div>  domainadminpassword (string): Password used to join in AD domain (mandatory with joindomain)</div><div>  fullname (string): Server owner name (default: Administrator)</div><div>  joindomain (string): AD domain to join (Not compatible with <code>joinworkgroup</code>)</div><div>  joinworkgroup (string): Workgroup to join (Not compatible with <code>joindomain</code>, default: WORKGROUP)</div><div>  orgname (string): Organisation name (default: ACME)</div><div>  password (string): Local administrator password (mandatory)</div><div>  productid (string): Product ID</div><div>  runonce (list): List of commands to run at first user logon</div><div>  timezone (int): Timezone (default: 85) See https://msdn.microsoft.com/en-us/library/ms912391(v=winembedded.11).aspx</div>        </td></tr>
                <tr><td>customvalues<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Define a list of customvalues to set on VM.</div><div>A customvalue object takes 2 fields 'key' and 'value'.</div>        </td></tr>
                <tr><td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ha-datacenter</td>
        <td></td>
        <td><div>Destination datacenter for the deploy operation</div>        </td></tr>
                <tr><td>disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of disks to add</div><div>Valid attributes are: size_[tb,gb,mb,kb], type, datastore and autoselect_datastore</div><div>type: Valid value is thin (default: None)</div><div>datastore: Datastore to use for the disk. If autoselect_datastore is True, filter datastore selection.</div><div>autoselect_datastore (bool): select the less used datastore.</div>        </td></tr>
                <tr><td>esxi_hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The esxi hostname where the VM will run.</div>        </td></tr>
                <tr><td>folder<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Destination folder, absolute path to find an existing guest or create the new guest</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ignore warnings and complete the actions</div>        </td></tr>
                <tr><td>guest_id<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set the guest ID (Debian, RHEL, Windows...)</div><div>This field is required when creating a VM</div><div>Valid values are referenced here: https://www.vmware.com/support/developer/converter-sdk/conv55_apireference/vim.vm.GuestOsDescriptor.GuestOsIdentifier.html</div>        </td></tr>
                <tr><td>hardware<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Manage some VM hardware attributes.</div><div>Valid attributes are: memory_mb, num_cpus and scsi</div><div>scsi: Valid values are buslogic, lsilogic, lsilogicsas and paravirtual (default)</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the vSphere vCenter.</div>        </td></tr>
                <tr><td>is_template<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Flag the instance as a template</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the VM to work with</div>        </td></tr>
                <tr><td>name_match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>first</td>
        <td><ul><li>first</li><li>last</li></ul></td>
        <td><div>If multiple VMs matching the name, use the first or last found</div>        </td></tr>
                <tr><td>networks<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Network to use should include <code>name</code> or <code>vlan</code> entry</div><div>Add an optional <code>ip</code> and <code>netmask</code> for network configuration</div><div>Add an optional <code>gateway</code> entry to configure a gateway</div><div>Add an optional <code>mac</code> entry to customize mac address</div><div>Add an optional <code>dns_servers</code> or <code>domain</code> entry per interface (Windows)</div><div>Add an optional <code>device_type</code> to configure the virtual NIC (pcnet32, vmxnet2, vmxnet3, e1000, e1000e)</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: pass, pwd<div>        </td></tr>
                <tr><td>resource_pool<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Affect machine to the given resource pool</div><div>Resource pool should be child of the selected host parent</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>poweredon</li><li>poweredoff</li><li>restarted</li><li>suspended</li><li>shutdownguest</li><li>rebootguest</li></ul></td>
        <td><div>What state should the virtual machine be in?</div><div>If <code>state</code> is set to <code>present</code> and VM exists, ensure the VM configuration conforms to task arguments</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Template used to create VM.</div><div>If this value is not set, VM is created without using a template.</div><div>If the VM exists already this setting will be ignored.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: user, admin<div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of the instance to manage if known, this is VMware's unique identifier.</div><div>This is required if name is not supplied.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted.</div>        </td></tr>
                <tr><td>wait_for_ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Wait until vCenter detects an IP address for the VM</div><div>This requires vmware-tools (vmtoolsd) to properly work after creation</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a VM from a template
      - name: create the VM
        vmware_guest:
          hostname: 192.0.2.44
          username: administrator@vsphere.local
          password: vmware
          validate_certs: no
          esxi_hostname: 192.0.2.117
          datacenter: datacenter1
          folder: testvms
          name: testvm_2
          state: poweredon
          guest_id: centos64guest
          disk:
          - size_gb: 10
            type: thin
            datastore: g73_datastore
          hardware:
            memory_mb: 512
            num_cpus: 1
            scsi: paravirtual
          networks:
          - name: VM Network
            ip: 192.168.1.100
            netmask: 255.255.255.0
            mac: 'aa:bb:dd:aa:00:14'
          template: template_el7
          wait_for_ip_address: yes
        register: deploy
    
    # Clone a VM from Template and customize
      - name: Clone template and customize
        vmware_guest:
          hostname: 192.168.1.209
          username: administrator@vsphere.local
          password: vmware
          validate_certs: no
          datacenter: datacenter1
          cluster: cluster
          name: testvm-2
          template: template_windows
          networks:
          - name: VM Network
            ip: 192.168.1.100
            netmask: 255.255.255.0
            gateway: 192.168.1.1
            mac: 'aa:bb:dd:aa:00:14'
            domain: my_domain
            dns_servers:
            - 192.168.1.1
            - 192.168.1.2
          customization:
            autologon: True
            dns_servers:
            - 192.168.1.1
            - 192.168.1.2
            domain: my_domain
            password: new_vm_password
            runonce:
            - powershell.exe -ExecutionPolicy Unrestricted -File C:\Windows\Temp\Enable-WinRM.ps1 -ForceNewSSLCert
    
    # Create a VM template
      - name: create a VM template
        vmware_guest:
          hostname: 192.0.2.88
          username: administrator@vsphere.local
          password: vmware
          validate_certs: no
          datacenter: datacenter1
          cluster: vmware_cluster_esx
          resource_pool: highperformance_pool
          folder: testvms
          name: testvm_6
          is_template: yes
          guest_id: debian6_64Guest
          disk:
          - size_gb: 10
            type: thin
            datastore: g73_datastore
          hardware:
            memory_mb: 512
            num_cpus: 1
            scsi: lsilogic
          wait_for_ip_address: yes
        register: deploy
    
    # Rename a VM (requires the VM's uuid)
      - vmware_guest:
          hostname: 192.168.1.209
          username: administrator@vsphere.local
          password: vmware
          uuid: 421e4592-c069-924d-ce20-7e7533fab926
          name: new_name
          state: present
    
    # Remove a VM by uuid
      - vmware_guest:
          hostname: 192.168.1.209
          username: administrator@vsphere.local
          password: vmware
          uuid: 421e4592-c069-924d-ce20-7e7533fab926
          state: absent

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
        <td> instance </td>
        <td>  </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> None </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Tested on vSphere 5.5 and 6.0



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
