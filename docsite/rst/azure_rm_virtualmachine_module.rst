.. _azure_rm_virtualmachine:


azure_rm_virtualmachine - Manage Azure virtual machines.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update, stop and start a virtual machine. Provide an existing storage account and network interface or allow the module to create these for you. If you choose not to provide a network interface, the resource group must contain a virtual network with at least one subnet.
Currently requires an image found in the Azure Marketplace. Use azure_rm_virtualmachineimage_facts module to discover the publisher, offer, sku and version of a particular image.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * azure == 2.0.0rc5


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
    <td>ad_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Active Directory username. Use when authenticating with an Active Directory user rather than service principal.</div></td></tr>
            <tr>
    <td>admin_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password for the admin username. Not required if the os_type is Linux and SSH password authentication is disabled by setting ssh_password_enabled to false.</div></td></tr>
            <tr>
    <td>admin_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Admin username used to access the host after it is created. Required when creating a VM.</div></td></tr>
            <tr>
    <td>allocated<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Toggle that controls if the machine is allocated/deallocated, only useful with state='present'.</div></td></tr>
            <tr>
    <td>append_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Use to control if tags field is canonical or just appends to existing tags. When canonical, any tags not found in the tags parameter will be removed from the object's metadata.</div></td></tr>
            <tr>
    <td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary describing the Marketplace image used to build the VM. Will contain keys: publisher, offer, sku and version. NOTE: set image.version to 'latest' to get the most recent version of a given image.</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Valid Azure location. Defaults to location of the resource group.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the virtual machine.</div></td></tr>
            <tr>
    <td>network_interface_names<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of existing network interface names to add to the VM. If a network interface name is not provided when the VM is created, a default network interface will be created. In order for the module to create a network interface, at least one Virtual Network with one Subnet must exist.</div></td></tr>
            <tr>
    <td>open_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If a network interface is created when creating the VM, a security group will be created as well. For Linux hosts a rule will be added to the security group allowing inbound TCP connections to the default SSH port 22, and for Windows hosts ports 3389 and 5986 will be opened. Override the default open ports by providing a list of ports.</div></td></tr>
            <tr>
    <td>os_disk_caching<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ReadOnly</td>
        <td><ul><li>ReadOnly</li><li>ReadWrite</li></ul></td>
        <td><div>Type of OS disk caching.</div></br>
        <div style="font-size: small;">aliases: disk_caching<div></td></tr>
            <tr>
    <td>os_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'Linux']</td>
        <td><ul><li>Windows</li><li>Linux</li></ul></td>
        <td><div>Base type of operating system.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Active Directory user password. Use when authenticating with an Active Directory user rather than service principal.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Security profile found in ~/.azure/credentials file.</div></td></tr>
            <tr>
    <td>public_ip_allocation_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'Static']</td>
        <td><ul><li>Dynamic</li><li>Static</li></ul></td>
        <td><div>If a public IP address is created when creating the VM (because a Network Interface was not provided), determines if the public IP address remains permanently associated with the Network Interface. If set to 'Dynamic' the public IP address may change any time the VM is rebooted or power cycled.</div></br>
        <div style="font-size: small;">aliases: public_ip_allocation<div></td></tr>
            <tr>
    <td>remove_on_absent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'all']</td>
        <td><ul></ul></td>
        <td><div>When removing a VM using state 'absent', also remove associated resources</div><div>It can be 'all' or a list with any of the following: ['network_interfaces', 'virtual_storage', 'public_ips']</div><div>Any other input will be ignored</div></td></tr>
            <tr>
    <td>resource_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the resource group containing the virtual machine.</div></td></tr>
            <tr>
    <td>restarted<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with state 'present' to restart a running VM.</div></td></tr>
            <tr>
    <td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>short_hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name assigned internally to the host. On a linux VM this is the name returned by the `hostname` command. When creating a virtual machine, short_hostname defaults to name.</div></td></tr>
            <tr>
    <td>ssh_password_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>When the os_type is Linux, setting ssh_password_enabled to false will disable SSH password authentication and require use of SSH keys.</div></td></tr>
            <tr>
    <td>ssh_public_keys<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>For os_type Linux provide a list of SSH keys. Each item in the list should be a dictionary where the dictionary contains two keys: path and key_data. Set the path to the default location of the authorized_keys files. On an Enterprise Linux host, for example, the path will be /home/&lt;admin username&gt;/.ssh/authorized_keys. Set key_data to the actual value of the public key.</div></td></tr>
            <tr>
    <td>started<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Use with state 'present' to start the machine. Set to false to have the machine be 'stopped'.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Assert the state of the virtual machine.</div><div>State 'present' will check that the machine exists with the requested configuration. If the configuration of the existing machine does not match, the machine will be updated. Use options started, allocated and restarted to change the machine's power state.</div><div>State 'absent' will remove the virtual machine.</div></td></tr>
            <tr>
    <td>storage_account_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of an existing storage account that supports creation of VHD blobs. If not specified for a new VM, a new storage account named &lt;vm name&gt;01 will be created using storage type 'Standard_LRS'.</div></td></tr>
            <tr>
    <td>storage_blob_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name fo the storage blob used to hold the VM's OS disk image. If no name is provided, defaults to the VM name + '.vhd'. If you provide a name, it must end with '.vhd'</div></br>
        <div style="font-size: small;">aliases: storage_blob<div></td></tr>
            <tr>
    <td>storage_container_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>vhds</td>
        <td><ul></ul></td>
        <td><div>Name of the container to use within the storage account to store VHD blobs. If no name is specified a default container will created.</div></td></tr>
            <tr>
    <td>subnet_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When creating a virtual machine, if a network interface name is not provided, one will be created. The new network interface will be assigned to the first subnet found in the virtual network. Use this parameter to provide a specific subnet instead.</div></br>
        <div style="font-size: small;">aliases: virtual_network<div></td></tr>
            <tr>
    <td>subscription_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your Azure subscription Id.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary of string:string pairs to assign as metadata to the object. Metadata tags on the object will be updated with any provided values. To remove tags set append_tags option to false.</div></td></tr>
            <tr>
    <td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure tenant ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>virtual_network_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When creating a virtual machine, if a network interface name is not provided, one will be created. The new network interface will be assigned to the first virtual network found in the resource group. Use this parameter to provide a specific virtual network instead.</div></br>
        <div style="font-size: small;">aliases: virtual_network<div></td></tr>
            <tr>
    <td>vm_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Standard_D1</td>
        <td><ul></ul></td>
        <td><div>A valid Azure VM size value. For example, 'Standard_D4'. The list of choices varies depending on the subscription and location. Check your subscription for available choices.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: Create VM with defaults
      azure_rm_virtualmachine:
        resource_group: Testing
        name: testvm10
        admin_username: chouseknecht
        admin_password: <your password here>
        image:
          offer: CentOS
          publisher: OpenLogic
          sku: '7.1'
          version: latest
    
    - name: Create a VM with exiting storage account and NIC
      azure_rm_virtualmachine:
        resource_group: Testing
        name: testvm002
        vm_size: Standard_D4
        storage_account: testaccount001
        admin_username: adminUser
        ssh_public_keys:
          - path: /home/adminUser/.ssh/authorized_keys
            key_data: < insert yor ssh public key here... >
        network_interfaces: testvm001
        image:
          offer: CentOS
          publisher: OpenLogic
          sku: '7.1'
          version: latest
    
    - name: Power Off
      azure_rm_virtualmachine:
        resource_group: Testing
        name: testvm002
        started: no
    
    - name: Deallocate
      azure_rm_virtualmachine:
        resource_group: Testing
        name: testvm002
        allocated: no
    
    - name: Power On
      azure_rm_virtualmachine:
        resource_group:
        name: testvm002
    
    - name: Restart
      azure_rm_virtualmachine:
        resource_group:
        name: testvm002
        restarted: yes
    
    - name: remove vm and all resources except public ips
      azure_rm_virtualmachine:
        resource_group: Testing
        name: testvm002
        state: absent
        remove_on_absent:
            - network_interfaces
            - virtual_storage

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
        <td> deleted_public_ips </td>
        <td> List of deleted public IP address names. </td>
        <td align=center> on delete </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> deleted_vhd_uris </td>
        <td> List of deleted Virtual Hard Disk URIs. </td>
        <td align=center> on delete </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> powerstate </td>
        <td> Indicates if the state is running, stopped, deallocated </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> deleted_network_interfaces </td>
        <td> List of deleted NICs. </td>
        <td align=center> on delete </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> azure_vm </td>
        <td> Facts about the current state of the object. Note that facts are not part of the registered output but available directly. </td>
        <td align=center> always </td>
        <td align=center> complex </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: For authentication with Azure you can pass parameters, set environment variables or use a profile stored in ~/.azure/credentials. Authentication is possible using a service principal or Active Directory user. To authenticate via service principal pass subscription_id, client_id, secret and tenant or set set environment variables AZURE_SUBSCRIPTION_ID, AZURE_CLIENT_ID, AZURE_SECRET and AZURE_TENANT.
.. note:: To Authentication via Active Directory user pass ad_user and password, or set AZURE_AD_USER and AZURE_PASSWORD in the environment.
.. note:: Alternatively, credentials can be stored in ~/.azure/credentials. This is an ini file containing a [default] section and the following keys: subscription_id, client_id, secret and tenant or subscription_id, ad_user and password. It is also possible to add additional profiles. Specify the profile by passing profile or setting AZURE_PROFILE in the environment.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

