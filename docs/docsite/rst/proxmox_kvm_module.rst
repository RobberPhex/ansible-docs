.. _proxmox_kvm:


proxmox_kvm - Management of Qemu(KVM) Virtual Machines in Proxmox VE cluster.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Allows you to create/delete/stop Qemu(KVM) Virtual Machines in Proxmox VE cluster.


Requirements (on host that executes module)
-------------------------------------------

  * proxmoxer
  * requests


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
                <tr><td>acpi<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specify if ACPI should be enables/disabled.</div>        </td></tr>
                <tr><td>agent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specify if the QEMU GuestAgent should be enabled/disabled.</div>        </td></tr>
                <tr><td>api_host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify the target host of the Proxmox VE cluster.</div>        </td></tr>
                <tr><td>api_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the password to authenticate with.</div><div>You can use <code>PROXMOX_PASSWORD</code> environment variable.</div>        </td></tr>
                <tr><td>api_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify the user to authenticate with.</div>        </td></tr>
                <tr><td>args<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>-serial unix:/var/run/qemu-server/VMID.serial,server,nowait</td>
        <td></td>
        <td><div>Pass arbitrary arguments to kvm.</div><div>This option is for experts only!</div>        </td></tr>
                <tr><td>autostart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specify, if the VM should be automatically restarted after crash (currently ignored in PVE API).</div>        </td></tr>
                <tr><td>balloon<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the amount of RAM for the VM in MB.</div><div>Using zero disables the balloon driver.</div>        </td></tr>
                <tr><td>bios<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>seabios</li><li>ovmf</li></ul></td>
        <td><div>Specify the BIOS implementation.</div>        </td></tr>
                <tr><td>boot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cnd</td>
        <td></td>
        <td><div>Specify the boot order -&gt; boot on floppy <code>a</code>, hard disk <code>c</code>, CD-ROM <code>d</code>, or network <code>n</code>.</div><div>You can combine to set order.</div>        </td></tr>
                <tr><td>bootdisk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable booting from specified disk. <code>(ide|sata|scsi|virtio</code>\d+)</div>        </td></tr>
                <tr><td>clone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of VM to be cloned. If <code>vmid</code> is setted, <code>clone</code> can take arbitrary value but required for intiating the clone.</div>        </td></tr>
                <tr><td>cores<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Specify number of cores per socket.</div>        </td></tr>
                <tr><td>cpu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>kvm64</td>
        <td></td>
        <td><div>Specify emulated CPU type.</div>        </td></tr>
                <tr><td>cpulimit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if CPU usage will be limited. Value 0 indicates no CPU limit.</div><div>If the computer has 2 CPUs, it has total of '2' CPU time</div>        </td></tr>
                <tr><td>cpuunits<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1000</td>
        <td></td>
        <td><div>Specify CPU weight for a VM.</div><div>You can disable fair-scheduler configuration by setting this to 0</div>        </td></tr>
                <tr><td>delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a list of settings you want to delete.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the description for the VM. Only used on the configuration web interface.</div><div>This is saved as comment inside the configuration file.</div>        </td></tr>
                <tr><td>digest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if to prevent changes if current configuration file has different SHA1 digest.</div><div>This can be used to prevent concurrent modifications.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Allow to force stop VM.</div><div>Can be used only with states <code>stopped</code>, <code>restarted</code>.</div>        </td></tr>
                <tr><td>format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>qcow2</td>
        <td><ul><li>cloop</li><li>cow</li><li>qcow</li><li>qcow2</li><li>qed</li><li>raw</li><li>vmdk</li></ul></td>
        <td><div>Target drive’s backing file’s data format.</div><div>Used only with clone</div>        </td></tr>
                <tr><td>freeze<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specify if PVE should freeze CPU at startup (use 'c' monitor command to start execution).</div>        </td></tr>
                <tr><td>full<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Create a full copy of all disk. This is always done when you clone a normal VM.</div><div>For VM templates, we try to create a linked clone by default.</div><div>Used only with clone</div>        </td></tr>
                <tr><td>hostpci<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a hash/dictionary of map host pci devices into guest. <code>hostpci='{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - <code>hostpci[n]</code> where 0 ≤ n ≤ N.</div><div>Values allowed are -  <code>"host="HOSTPCIID[;HOSTPCIID2...]",pcie="1|0",rombar="1|0",x-vga="1|0""</code>.</div><div>The <code>host</code> parameter is Host PCI device pass through. HOSTPCIID syntax is <code>bus:dev.func</code> (hexadecimal numbers).</div><div><code>pcie=boolean</code> <em>default=0</em> Choose the PCI-express bus (needs the q35 machine model).</div><div><code>rombar=boolean</code> <em>default=1</em> Specify whether or not the device’s ROM will be visible in the guest’s memory map.</div><div><code>x-vga=boolean</code> <em>default=0</em> Enable vfio-vga device support.</div><div>/!\ This option allows direct access to host hardware. So it is no longer possible to migrate such machines - use with special care.</div>        </td></tr>
                <tr><td>hotplug<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Selectively enable hotplug features.</div><div>This is a comma separated list of hotplug features <code>'network', 'disk', 'cpu', 'memory' and 'usb'</code>.</div><div>Value 0 disables hotplug completely and value 1 is an alias for the default <code>'network,disk,usb'</code>.</div>        </td></tr>
                <tr><td>hugepages<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>any</li><li>2</li><li>1024</li></ul></td>
        <td><div>Enable/disable hugepages memory.</div>        </td></tr>
                <tr><td>ide<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash/dictionary of volume used as IDE hard disk or CD-ROM. <code>ide='{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - <code>ide[n]</code> where 0 ≤ n ≤ 3.</div><div>Values allowed are - <code>"storage:size,format=value"</code>.</div><div><code>storage</code> is the storage identifier where to create the disk.</div><div><code>size</code> is the size of the disk in GB.</div><div><code>format</code> is the drive’s backing file’s data format. <code>qcow2|raw|subvol</code>.</div>        </td></tr>
                <tr><td>keyboard<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the keyboard layout for VNC server.</div>        </td></tr>
                <tr><td>kvm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enable/disable KVM hardware virtualization.</div>        </td></tr>
                <tr><td>localtime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Sets the real time clock to local time.</div><div>This is enabled by default if ostype indicates a Microsoft OS.</div>        </td></tr>
                <tr><td>lock<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>migrate</li><li>backup</li><li>snapshot</li><li>rollback</li></ul></td>
        <td><div>Lock/unlock the VM.</div>        </td></tr>
                <tr><td>machine<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the Qemu machine type.</div><div>type =&gt; <code>(pc|pc(-i440fx</code>?-\d+\.\d+(\.pxe)?|q35|pc-q35-\d+\.\d+(\.pxe)?))</div>        </td></tr>
                <tr><td>memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>512</td>
        <td></td>
        <td><div>Memory size in MB for instance.</div>        </td></tr>
                <tr><td>migrate_downtime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets maximum tolerated downtime (in seconds) for migrations.</div>        </td></tr>
                <tr><td>migrate_speed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets maximum speed (in MB/s) for migrations.</div><div>A value of 0 is no limit.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the VM name. Only used on the configuration web interface.</div><div>Required only for <code>state=present</code>.</div>        </td></tr>
                <tr><td>net<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash/dictionary of network interfaces for the VM. <code>net='{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - <code>net[n]</code> where 0 ≤ n ≤ N.</div><div>Values allowed are - <code>"model="XX:XX:XX:XX:XX:XX",brigde="value",rate="value",tag="value",firewall="1|0",trunks="vlanid""</code>.</div><div>Model is one of <code>e1000 e1000-82540em e1000-82544gc e1000-82545em i82551 i82557b i82559er ne2k_isa ne2k_pci pcnet rtl8139 virtio vmxnet3</code>.</div><div><code>XX:XX:XX:XX:XX:XX</code> should be an unique MAC address. This is automatically generated if not specified.</div><div>The <code>bridge</code> parameter can be used to automatically add the interface to a bridge device. The Proxmox VE standard bridge is called 'vmbr0'.</div><div>Option <code>rate</code> is used to limit traffic bandwidth from and to this interface. It is specified as floating point number, unit is 'Megabytes per second'.</div><div>If you specify no bridge, we create a kvm 'user' (NATed) network device, which provides DHCP and DNS services.</div>        </td></tr>
                <tr><td>newid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>VMID for the clone. Used only with clone.</div><div>If newid is not set, the next available VM ID will be fetched from ProxmoxAPI.</div>        </td></tr>
                <tr><td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Proxmox VE node, where the new VM will be created.</div><div>Only required for <code>state=present</code>.</div><div>For other states, it will be autodiscovered.</div>        </td></tr>
                <tr><td>numa<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash/dictionaries of NUMA topology. <code>numa='{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - <code>numa[n]</code> where 0 ≤ n ≤ N.</div><div>Values allowed are - <code>"cpu="&lt;id[-id];...&gt;",hostnodes="&lt;id[-id];...&gt;",memory="number",policy="(bind|interleave|preferred</code>"").</div><div><code>cpus</code> CPUs accessing this NUMA node.</div><div><code>hostnodes</code> Host NUMA nodes to use.</div><div><code>memory</code> Amount of memory this NUMA node provides.</div><div><code>policy</code> NUMA allocation policy.</div>        </td></tr>
                <tr><td>onboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies whether a VM will be started during system bootup.</div>        </td></tr>
                <tr><td>ostype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>l26</td>
        <td><ul><li>other</li><li>wxp</li><li>w2k</li><li>w2k3</li><li>w2k8</li><li>wvista</li><li>win7</li><li>win8</li><li>l24</li><li>l26</li><li>solaris</li></ul></td>
        <td><div>Specifies guest operating system. This is used to enable special optimization/features for specific operating systems.</div><div>The l26 is Linux 2.6/3.X Kernel.</div>        </td></tr>
                <tr><td>parallel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash/dictionary of map host parallel devices. <code>parallel='{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - (parallel[n]) where 0 ≤ n ≤ 2.</div><div>Values allowed are - <code>"/dev/parport\d+|/dev/usb/lp\d+"</code>.</div>        </td></tr>
                <tr><td>pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Add the new VM to the specified pool.</div>        </td></tr>
                <tr><td>protection<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enable/disable the protection flag of the VM. This will enable/disable the remove VM and remove disk operations.</div>        </td></tr>
                <tr><td>reboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Allow reboot. If set to yes, the VM exit on reboot.</div>        </td></tr>
                <tr><td>revert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Revert a pending change.</div>        </td></tr>
                <tr><td>sata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash/dictionary of volume used as sata hard disk or CD-ROM. <code>sata='{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - <code>sata[n]</code> where 0 ≤ n ≤ 5.</div><div>Values allowed are -  <code>"storage:size,format=value"</code>.</div><div><code>storage</code> is the storage identifier where to create the disk.</div><div><code>size</code> is the size of the disk in GB.</div><div><code>format</code> is the drive’s backing file’s data format. <code>qcow2|raw|subvol</code>.</div>        </td></tr>
                <tr><td>scsi<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash/dictionary of volume used as SCSI hard disk or CD-ROM. <code>scsi='{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - <code>sata[n]</code> where 0 ≤ n ≤ 13.</div><div>Values allowed are -  <code>"storage:size,format=value"</code>.</div><div><code>storage</code> is the storage identifier where to create the disk.</div><div><code>size</code> is the size of the disk in GB.</div><div><code>format</code> is the drive’s backing file’s data format. <code>qcow2|raw|subvol</code>.</div>        </td></tr>
                <tr><td>scsihw<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>lsi</li><li>lsi53c810</li><li>virtio-scsi-pci</li><li>virtio-scsi-single</li><li>megasas</li><li>pvscsi</li></ul></td>
        <td><div>Specifies the SCSI controller model.</div>        </td></tr>
                <tr><td>serial<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash/dictionary of serial device to create inside the VM. <code>'{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - serial[n](str; required) where 0 ≤ n ≤ 3.</div><div>Values allowed are - <code>(/dev/.+|socket</code>).</div><div>/!\ If you pass through a host serial device, it is no longer possible to migrate such machines - use with special care.</div>        </td></tr>
                <tr><td>shares<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rets amount of memory shares for auto-ballooning. (0 - 50000).</div><div>The larger the number is, the more memory this VM gets.</div><div>The number is relative to weights of all other running VMs.</div><div>Using 0 disables auto-ballooning, this means no limit.</div>        </td></tr>
                <tr><td>skiplock<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ignore locks</div><div>Only root is allowed to use this option.</div>        </td></tr>
                <tr><td>smbios<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies SMBIOS type 1 fields.</div>        </td></tr>
                <tr><td>snapname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the snapshot. Used only with clone.</div>        </td></tr>
                <tr><td>sockets<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Sets the number of CPU sockets. (1 - N).</div>        </td></tr>
                <tr><td>startdate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the initial date of the real time clock.</div><div>Valid format for date are <code>'now'</code> or <code>'2016-09-25T16:01:21'</code> or <code>'2016-09-25'</code>.</div>        </td></tr>
                <tr><td>startup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Startup and shutdown behavior. <code>[[order=]\d+] [,up=\d+] [,down=\d+]</code>.</div><div>Order is a non-negative number defining the general startup order.</div><div>Shutdown in done with reverse ordering.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>started</li><li>absent</li><li>stopped</li><li>restarted</li><li>current</li></ul></td>
        <td><div>Indicates desired state of the instance.</div><div>If <code>current</code>, the current state of the VM will be fecthed. You can access it with <code>results.status</code></div>        </td></tr>
                <tr><td>storage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Target storage for full clone.</div>        </td></tr>
                <tr><td>tablet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enables/disables the USB tablet device.</div>        </td></tr>
                <tr><td>target<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Target node. Only allowed if the original VM is on shared storage.</div><div>Used only with clone</div>        </td></tr>
                <tr><td>tdf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enables/disables time drift fix.</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enables/disables the template.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>Timeout for operations.</div>        </td></tr>
                <tr><td>update<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, the VM will be update with new value.</div><div>Cause of the operations of the API and security reasons, I have disabled the update of the following parameters</div><div><code>net, virtio, ide, sata, scsi</code>. Per example updating <code>net</code> update the MAC address and <code>virtio</code> create always new disk...</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
                <tr><td>vcpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets number of hotplugged vcpus.</div>        </td></tr>
                <tr><td>vga<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>std</td>
        <td><ul><li>std</li><li>cirrus</li><li>vmware</li><li>qxl</li><li>serial0</li><li>serial1</li><li>serial2</li><li>serial3</li><li>qxl2</li><li>qxl3</li><li>qxl4</li></ul></td>
        <td><div>Select VGA type. If you want to use high resolution modes (&gt;= 1280x1024x16) then you should use option 'std' or 'vmware'.</div>        </td></tr>
                <tr><td>virtio<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash/dictionary of volume used as VIRTIO hard disk. <code>virtio='{"key":"value", "key":"value"}'</code>.</div><div>Keys allowed are - <code>virto[n]</code> where 0 ≤ n ≤ 15.</div><div>Values allowed are -  <code>"storage:size,format=value"</code>.</div><div><code>storage</code> is the storage identifier where to create the disk.</div><div><code>size</code> is the size of the disk in GB.</div><div><code>format</code> is the drive’s backing file’s data format. <code>qcow2|raw|subvol</code>.</div>        </td></tr>
                <tr><td>vmid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the VM ID. Instead use <em>name</em> parameter.</div><div>If vmid is not set, the next available VM ID will be fetched from ProxmoxAPI.</div>        </td></tr>
                <tr><td>watchdog<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Creates a virtual hardware watchdog device.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create new VM with minimal options
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
    
    # Create new VM with minimal options and given vmid
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        vmid        : 100
    
    # Create new VM with two network interface options.
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        net         : '{"net0":"virtio,bridge=vmbr1,rate=200", "net1":"e1000,bridge=vmbr2,"}'
    
    # Create new VM with one network interface, three virto hard disk, 4 cores, and 2 vcpus.
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        net         : '{"net0":"virtio,bridge=vmbr1,rate=200"}'
        virtio      : '{"virtio0":"VMs_LVM:10", "virtio1":"VMs:2,format=qcow2", "virtio2":"VMs:5,format=raw"}'
        cores       : 4
        vcpus       : 2
    
    # Clone VM with only source VM name
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        clone       : spynal   # The VM source
        name        : zavala  # The target VM name
        node        : sabrewulf
        storage     : VMs
        format      : qcow2
        timeout     : 500  # Note: The task can take a while. Adapt
    
    # Clone VM with source vmid and target newid and raw format
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        clone       : arbitrary_name
        vmid        : 108
        newid       : 152
        name        : zavala  # The target VM name
        node        : sabrewulf
        storage     : LVM_STO
        format      : raw
        timeout     : 300  # Note: The task can take a while. Adapt
    
    # Create new VM and lock it for snapashot.
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        lock        : snapshot
    
    # Create new VM and set protection to disable the remove VM and remove disk operations
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        protection  : yes
    
    # Start VM
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        state       : started
    
    # Stop VM
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        state       : stopped
    
    # Stop VM with force
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        state       : stopped
        force       : yes
    
    # Restart VM
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        state       : restarted
    
    # Remove VM
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        state       : absent
    
    # Get VM current state
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        state       : current
    
    # Update VM configuration
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        cpu         : 8
        memory      : 16384
        update      : yes
    
    # Delete QEMU parameters
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        delete      : 'args,template,cpulimit'
    
    # Revert a pending change
    - proxmox_kvm:
        api_user    : root@pam
        api_password: secret
        api_host    : helldorado
        name        : spynal
        node        : sabrewulf
        revert      : 'template,cpulimit'

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
        <td> status </td>
        <td> ['The current virtual machine status.', 'Returned only when C(state=current)'] </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> { "changed": false, "msg": "VM kropta with vmid = 110 is running", "status": "running" } </td>
    </tr>
            <tr>
        <td> mac </td>
        <td> List of mac address created and net[n] attached. Useful when you want to use provision systems like Foreman via PXE. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center>  { "net0": "3E:6E:97:D2:31:9F", "net1": "B6:A1:FC:EF:78:A4" } </td>
    </tr>
            <tr>
        <td> vmid </td>
        <td> The VM vmid. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 115 </td>
    </tr>
            <tr>
        <td> devices </td>
        <td> The list of devices created or used. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center>  { "ide0": "VMS_LVM:vm-115-disk-1", "ide1": "VMs:115/vm-115-disk-3.raw", "virtio0": "VMS_LVM:vm-115-disk-2", "virtio1": "VMs:115/vm-115-disk-1.qcow2", "virtio2": "VMs:115/vm-115-disk-2.raw" } </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
