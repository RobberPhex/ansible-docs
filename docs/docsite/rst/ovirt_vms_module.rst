.. _ovirt_vms:


ovirt_vms - Module to manage Virtual Machines in oVirt
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module manages whole lifecycle of the Virtual Machine(VM) in oVirt. Since VM can hold many states in oVirt, this see notes to see how the states of the VM are handled.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * ovirt-engine-sdk-python >= 4.0.0


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
                <tr><td>auth<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values needed to create HTTP/HTTPS connection to oVirt:</div><div><code>username</code>[<em>required</em>] - The name of the user, something like <em>admin@internal</em>. Default value is set by <em>OVIRT_USERNAME</em> environment variable.</div><div><code>password</code>[<em>required</em>] - The password of the user. Default value is set by <em>OVIRT_PASSWORD</em> environment variable.</div><div><code>url</code>[<em>required</em>] - A string containing the base URL of the server, usually something like `<em>https://server.example.com/ovirt-engine/api</em>`. Default value is set by <em>OVIRT_URL</em> environment variable.</div><div><code>token</code> - Token to be used instead of login with username/password. Default value is set by <em>OVIRT_TOKEN</em> environment variable.</div><div><code>insecure</code> - A boolean flag that indicates if the server TLS certificate and host name should be checked.</div><div><code>ca_file</code> - A PEM file containing the trusted CA certificates. The certificate presented by the server will be verified using these CA certificates. If `<code>ca_file</code>` parameter is not set, system wide CA certificate store is used. Default value is set by <em>OVIRT_CAFILE</em> environment variable.</div><div><code>kerberos</code> - A boolean flag indicating if Kerberos authentication should be used instead of the default basic authentication.</div>        </td></tr>
                <tr><td>boot_devices<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of boot devices which should be used to boot. Choices <em>network</em>, <em>hd</em> and <em>cdrom</em>.</div><div>For example: ['cdrom', 'hd']. Default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>cd_iso<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>ISO file from ISO storage domain which should be attached to Virtual Machine.</div><div>If you pass empty string the CD will be ejected from VM.</div><div>If used with <code>state</code> <em>running</em> or <em>present</em> and VM is running the CD will be attached to VM.</div><div>If used with <code>state</code> <em>running</em> or <em>present</em> and VM is down the CD will be attached to VM persistently.</div>        </td></tr>
                <tr><td>clone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> then the disks of the created virtual machine will be cloned and independent of the template.</div><div>This parameter is used only when <code>state</code> is <em>running</em> or <em>present</em> and VM didn't exist before.</div>        </td></tr>
                <tr><td>clone_permissions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> then the permissions of the template (only the direct ones, not the inherited ones) will be copied to the created virtual machine.</div><div>This parameter is used only when <code>state</code> is <em>running</em> or <em>present</em> and VM didn't exist before.</div>        </td></tr>
                <tr><td>cloud_init<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values for Unix-like Virtual Machine initialization using cloud init:</div><div><code>host_name</code> - Hostname to be set to Virtual Machine when deployed.</div><div><code>timezone</code> - Timezone to be set to Virtual Machine when deployed.</div><div><code>user_name</code> - Username to be used to set password to Virtual Machine when deployed.</div><div><code>root_password</code> - Password to be set for user specified by <code>user_name</code> parameter.</div><div><code>authorized_ssh_keys</code> - Use this SSH keys to login to Virtual Machine.</div><div><code>regenerate_ssh_keys</code> - If <em>True</em> SSH keys will be regenerated on Virtual Machine.</div><div><code>custom_script</code> - Cloud-init script which will be executed on Virtual Machine when deployed.</div><div><code>dns_servers</code> - DNS servers to be configured on Virtual Machine.</div><div><code>dns_search</code> - DNS search domains to be configured on Virtual Machine.</div><div><code>nic_boot_protocol</code> - Set boot protocol of the network interface of Virtual Machine. Can be one of none, dhcp or static.</div><div><code>nic_ip_address</code> - If boot protocol is static, set this IP address to network interface of Virtual Machine.</div><div><code>nic_netmask</code> - If boot protocol is static, set this netmask to network interface of Virtual Machine.</div><div><code>nic_gateway</code> - If boot protocol is static, set this gateway to network interface of Virtual Machine.</div><div><code>nic_name</code> - Set name to network interface of Virtual Machine.</div><div><code>nic_on_boot</code> - If <em>True</em> network interface will be set to start on boot.</div>        </td></tr>
                <tr><td>cloud_init_nics<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of dictionaries representing network interafaces to be setup by cloud init.</div><div>This option is used, when user needs to setup more network interfaces via cloud init.</div><div>If one network interface is enough, user should use <code>cloud_init</code> <em>nic_*</em> parameters. <code>cloud_init</code> <em>nic_*</em> parameters are merged with <code>cloud_init_nics</code> parameters.</div><div>Dictionary can contain following values:</div><div><code>nic_boot_protocol</code> - Set boot protocol of the network interface of Virtual Machine. Can be one of none, dhcp or static.</div><div><code>nic_ip_address</code> - If boot protocol is static, set this IP address to network interface of Virtual Machine.</div><div><code>nic_netmask</code> - If boot protocol is static, set this netmask to network interface of Virtual Machine.</div><div><code>nic_gateway</code> - If boot protocol is static, set this gateway to network interface of Virtual Machine.</div><div><code>nic_name</code> - Set name to network interface of Virtual Machine.</div><div><code>nic_on_boot</code> - If <em>True</em> network interface will be set to start on boot.</div>        </td></tr>
                <tr><td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the cluster, where Virtual Machine should be created. Required if creating VM.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comment of the Virtual Machine.</div>        </td></tr>
                <tr><td>cpu_cores<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of virtual CPUs cores of the Virtual Machine. Default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>cpu_shares<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set a CPU shares for this Virtual Machine. Default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>cpu_sockets<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of virtual CPUs sockets of the Virtual Machine. Default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>delete_protected<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> Virtual Machine will be set as delete protected.</div><div>If <em>False</em> Virtual Machine won't be set as delete protected.</div><div>If no value is passed, default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the Virtual Machine.</div>        </td></tr>
                <tr><td>disks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of disks, which should be attached to Virtual Machine. Disk is described by following dictionary:</div><div><code>name</code> - Name of the disk. Either <code>name</code> or <code>id</code> is reuqired.</div><div><code>id</code> - ID of the disk. Either <code>name</code> or <code>id</code> is reuqired.</div><div><code>interface</code> - Interface of the disk, either <em>virtio</em> or <em>IDE</em>, default is <em>virtio</em>.</div><div><code>bootable</code> - <em>True</em> if the disk should be bootable, default is non bootable.</div><div><code>activate</code> - <em>True</em> if the disk should be activated, default is activated.</div><div><code>Note:</code></div><div>This parameter is used only when <code>state</code> is <em>running</em> or <em>present</em> and is able to only attach disks. To manage disks of the VM in more depth please use <span class='module'>ovirt_disks</span> module instead.</div>        </td></tr>
                <tr><td>fetch_nested<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> the module will fetch additional data from the API.</div><div>It will fetch IDs of the VMs disks, snapshots, etc. User can configure to fetch other attributes of the nested entities by specifying <code>nested_attributes</code>.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Please check to <em>Synopsis</em> to more detailed description of force parameter, it can behave differently in different situations.</div>        </td></tr>
                <tr><td>high_availability<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> Virtual Machine will be set as highly available.</div><div>If <em>False</em> Virtual Machine won't be set as highly available.</div><div>If no value is passed, default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify host where Virtual Machine should be running. By default the host is chosen by engine scheduler.</div><div>This parameter is used only when <code>state</code> is <em>running</em> or <em>present</em>.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>ID of the the Virtual Machine to manage.</div>        </td></tr>
                <tr><td>initrd_path<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to an initial ramdisk to be used with the kernel specified by <code>kernel_path</code> option.</div><div>Ramdisk image must be stored on either the ISO domain or on the host's storage.</div>        </td></tr>
                <tr><td>instance_type<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of virtual machine's hardware configuration.</div><div>By default no instance type is used.</div>        </td></tr>
                <tr><td>kernel_params<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Kernel command line parameters (formatted as string) to be used with the kernel specified by <code>kernel_path</code> option.</div>        </td></tr>
                <tr><td>kernel_path<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to a kernel image used to boot the virtual machine.</div><div>Kernel image must be stored on either the ISO domain or on the host's storage.</div>        </td></tr>
                <tr><td>memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Amount of memory of the Virtual Machine. Prefix uses IEC 60027-2 standard (for example 1GiB, 1024MiB).</div><div>Default value is set by engine.</div>        </td></tr>
                <tr><td>memory_guaranteed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Amount of minimal guaranteed memory of the Virtual Machine. Prefix uses IEC 60027-2 standard (for example 1GiB, 1024MiB).</div><div><code>memory_guaranteed</code> parameter can't be lower than <code>memory</code> parameter. Default value is set by engine.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the the Virtual Machine to manage. If VM don't exists <code>name</code> is required. Otherwise <code>id</code> or <code>name</code> can be used.</div>        </td></tr>
                <tr><td>nested_attributes<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies list of the attributes which should be fetched from the API.</div><div>This parameter apply only when <code>fetch_nested</code> is <em>true</em>.</div>        </td></tr>
                <tr><td>nics<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of NICs, which should be attached to Virtual Machine. NIC is described by following dictionary:</div><div><code>name</code> - Name of the NIC.</div><div><code>profile_name</code> - Profile name where NIC should be attached.</div><div><code>interface</code> -  Type of the network interface. One of following: <em>virtio</em>, <em>e1000</em>, <em>rtl8139</em>, default is <em>virtio</em>.</div><div><code>mac_address</code> - Custom MAC address of the network interface, by default it's obtained from MAC pool.</div><div><code>Note:</code></div><div>This parameter is used only when <code>state</code> is <em>running</em> or <em>present</em> and is able to only create NICs. To manage NICs of the VM in more depth please use <span class='module'>ovirt_nics</span> module instead.</div>        </td></tr>
                <tr><td>operating_system<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>rhel_6_ppc64</li><li>other</li><li>freebsd</li><li>windows_2003x64</li><li>windows_10</li><li>rhel_6x64</li><li>rhel_4x64</li><li>windows_2008x64</li><li>windows_2008R2x64</li><li>debian_7</li><li>windows_2012x64</li><li>ubuntu_14_04</li><li>ubuntu_12_04</li><li>ubuntu_13_10</li><li>windows_8x64</li><li>other_linux_ppc64</li><li>windows_2003</li><li>other_linux</li><li>windows_10x64</li><li>windows_2008</li><li>rhel_3</li><li>rhel_5</li><li>rhel_4</li><li>other_ppc64</li><li>sles_11</li><li>rhel_6</li><li>windows_xp</li><li>rhel_7x64</li><li>freebsdx64</li><li>rhel_7_ppc64</li><li>windows_7</li><li>rhel_5x64</li><li>ubuntu_14_04_ppc64</li><li>sles_11_ppc64</li><li>windows_8</li><li>windows_2012R2x64</li><li>windows_2008r2x64</li><li>ubuntu_13_04</li><li>ubuntu_12_10</li><li>windows_7x64</li></ul></td>
        <td><div>Operating system of the Virtual Machine. Default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>poll_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td></td>
        <td><div>Number of the seconds the module waits until another poll request on entity status is sent.</div>        </td></tr>
                <tr><td>serial_policy<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a serial number policy for the Virtual Machine.</div><div>Following options are supported:</div><div><code>vm</code> - Sets the Virtual Machine's UUID as its serial number.</div><div><code>host</code> - Sets the host's UUID as the Virtual Machine's serial number.</div><div><code>custom</code> - Allows you to specify a custom serial number in <code>serial_policy_value</code>.</div>        </td></tr>
                <tr><td>serial_policy_value<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Allows you to specify a custom serial number.</div><div>This parameter is used only when <code>serial_policy</code> is <em>custom</em>.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>running</li><li>stopped</li><li>present</li><li>absent</li><li>suspended</li><li>next_run</li></ul></td>
        <td><div>Should the Virtual Machine be running/stopped/present/absent/suspended/next_run.</div><div><em>present</em> and <em>running</em> are equal states.</div><div><em>next_run</em> state updates the VM and if the VM has next run configuration it will be rebooted.</div><div>Please check <em>notes</em> to more detailed description of states.</div>        </td></tr>
                <tr><td>stateless<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> Virtual Machine will be set as stateless.</div><div>If <em>False</em> Virtual Machine will be unset as stateless.</div><div>If no value is passed, default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>sysprep<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values for Windows Virtual Machine initialization using sysprep:</div><div><code>host_name</code> - Hostname to be set to Virtual Machine when deployed.</div><div><code>active_directory_ou</code> - Active Directory Organizational Unit, to be used for login of user.</div><div><code>org_name</code> - Organization name to be set to Windows Virtual Machine.</div><div><code>domain</code> - Domain to be set to Windows Virtual Machine.</div><div><code>timezone</code> - Timezone to be set to Windows Virtual Machine.</div><div><code>ui_language</code> - UI language of the Windows Virtual Machine.</div><div><code>system_locale</code> - System localization of the Windows Virtual Machine.</div><div><code>input_locale</code> - Input localization of the Windows Virtual Machine.</div><div><code>windows_license_key</code> - License key to be set to Windows Virtual Machine.</div><div><code>user_name</code> - Username to be used for set password to Windows Virtual Machine.</div><div><code>root_password</code> - Password to be set for username to Windows Virtual Machine.</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the template, which should be used to create Virtual Machine. Required if creating VM.</div><div>If template is not specified and VM doesn't exist, VM will be created from <em>Blank</em> template.</div>        </td></tr>
                <tr><td>template_version<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Version number of the template to be used for VM.</div><div>By default the latest available version of the template is used.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td></td>
        <td><div>The amount of time in seconds the module should wait for the instance to get into desired state.</div>        </td></tr>
                <tr><td>timezone<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets time zone offset of the guest hardware clock.</div><div>For example: Etc/GMT</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>server</li><li>desktop</li></ul></td>
        <td><div>Type of the Virtual Machine. Default value is set by oVirt engine.</div>        </td></tr>
                <tr><td>use_latest_template_version<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if latest template version should be used, when running a stateless VM.</div><div>If this parameter is set to <em>true</em> stateless VM is created.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div><em>True</em> if the module should wait for the entity to get into desired state.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Examples don't contain auth parameter for simplicity,
    # look at ovirt_auth module to see how to reuse authentication:
    
    # Creates a new Virtual Machine from template named 'rhel7_template'
    ovirt_vms:
        state: present
        name: myvm
        template: rhel7_template
    
    # Creates a stateless VM which will always use latest template version:
    ovirt_vms:
        name: myvm
        template: rhel7
        cluster: mycluster
        use_latest_template_version: true
    
    # Creates a new server rhel7 Virtual Machine from Blank template
    # on brq01 cluster with 2GiB memory and 2 vcpu cores/sockets
    # and attach bootable disk with name rhel7_disk and attach virtio NIC
    ovirt_vms:
        state: present
        cluster: brq01
        name: myvm
        memory: 2GiB
        cpu_cores: 2
        cpu_sockets: 2
        cpu_shares: 1024
        type: server
        operating_system: rhel_7x64
        disks:
          - name: rhel7_disk
            bootable: True
        nics:
          - name: nic1
    
    # Run VM with cloud init:
    ovirt_vms:
        name: rhel7
        template: rhel7
        cluster: Default
        memory: 1GiB
        high_availability: true
        cloud_init:
          nic_boot_protocol: static
          nic_ip_address: 10.34.60.86
          nic_netmask: 255.255.252.0
          nic_gateway: 10.34.63.254
          nic_name: eth1
          nic_on_boot: true
          host_name: example.com
          custom_script: |
            write_files:
             - content: |
                 Hello, world!
               path: /tmp/greeting.txt
               permissions: '0644'
          user_name: root
          root_password: super_password
    
    # Run VM with cloud init, with multiple network interfaces:
    ovirt_vms:
      name: rhel7_4
      template: rhel7
      cluster: mycluster
      cloud_init_nics:
        - nic_name: eth0
          nic_boot_protocol: dhcp
          nic_on_boot: true
        - nic_name: eth1
          nic_boot_protocol: static
          nic_ip_address: 10.34.60.86
          nic_netmask: 255.255.252.0
          nic_gateway: 10.34.63.254
          nic_on_boot: true
    
    # Run VM with sysprep:
    ovirt_vms:
        name: windows2012R2_AD
        template: windows2012R2
        cluster: Default
        memory: 3GiB
        high_availability: true
        sysprep:
          host_name: windowsad.example.com
          user_name: Administrator
          root_password: SuperPassword123
    
    # Migrate/Run VM to/on host named 'host1'
    ovirt_vms:
        state: running
        name: myvm
        host: host1
    
    # Change Vm's CD:
    ovirt_vms:
        name: myvm
        cd_iso: drivers.iso
    
    # Eject Vm's CD:
    ovirt_vms:
        name: myvm
        cd_iso: ''
    
    # Boot VM from CD:
    ovirt_vms:
        name: myvm
        cd_iso: centos7_x64.iso
        boot_devices:
            - cdrom
    
    # Stop vm:
    ovirt_vms:
        state: stopped
        name: myvm
    
    # Upgrade memory to already created VM:
    ovirt_vms:
        name: myvm
        memory: 4GiB
    
    # Hot plug memory to already created and running VM:
    # (VM won't be restarted)
    ovirt_vms:
        name: myvm
        memory: 4GiB
    
    # When change on the VM needs restart of the VM, use next_run state,
    # The VM will be updated and rebooted if there are any changes.
    # If present state would be used, VM won't be restarted.
    ovirt_vms:
        state: next_run
        name: myvm
        boot_devices:
          - network
    
    # Remove VM, if VM is running it will be stopped:
    ovirt_vms:
        state: absent
        name: myvm

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
        <td> id </td>
        <td> ID of the VM which is managed </td>
        <td align=center> On success if VM is found. </td>
        <td align=center> str </td>
        <td align=center> 7de90f31-222c-436c-a1ca-7e655bd5b60c </td>
    </tr>
            <tr>
        <td> vm </td>
        <td> Dictionary of all the VM attributes. VM attributes can be found on your oVirt instance at following url: https://ovirt.example.com/ovirt-engine/api/model#types/vm. </td>
        <td align=center> On success if VM is found. </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - If VM is in *UNASSIGNED* or *UNKNOWN* state before any operation, the module will fail. If VM is in *IMAGE_LOCKED* state before any operation, we try to wait for VM to be *DOWN*. If VM is in *SAVING_STATE* state before any operation, we try to wait for VM to be *SUSPENDED*. If VM is in *POWERING_DOWN* state before any operation, we try to wait for VM to be *UP* or *DOWN*. VM can get into *UP* state from *POWERING_DOWN* state, when there is no ACPI or guest agent running inside VM, or if the shutdown operation fails. When user specify *UP* ``state``, we always wait to VM to be in *UP* state in case VM is *MIGRATING*, *REBOOTING*, *POWERING_UP*, *RESTORING_STATE*, *WAIT_FOR_LAUNCH*. In other states we run start operation on VM. When user specify *stopped* ``state``, and If user pass ``force`` parameter set to *true* we forcibly stop the VM in any state. If user don't pass ``force`` parameter, we always wait to VM to be in UP state in case VM is *MIGRATING*, *REBOOTING*, *POWERING_UP*, *RESTORING_STATE*, *WAIT_FOR_LAUNCH*. If VM is in *PAUSED* or *SUSPENDED* state, we start the VM. Then we gracefully shutdown the VM. When user specify *suspended* ``state``, we always wait to VM to be in UP state in case VM is *MIGRATING*, *REBOOTING*, *POWERING_UP*, *RESTORING_STATE*, *WAIT_FOR_LAUNCH*. If VM is in *PAUSED* or *DOWN* state, we start the VM. Then we suspend the VM. When user specify *absent* ``state``, we forcibly stop the VM in any state and remove it.
    - In order to use this module you have to install oVirt Python SDK. To ensure it's installed with correct version you can create the following task: *pip: name=ovirt-engine-sdk-python version=4.0.0*



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
