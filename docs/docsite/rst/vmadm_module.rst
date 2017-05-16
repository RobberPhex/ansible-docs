.. _vmadm:


vmadm - Manage SmartOS virtual machines and zones.
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage SmartOS virtual machines through vmadm(1M).


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6


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
                <tr><td>archive_on_delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When enabled, the zone dataset will be mounted on <code>/zones/archive</code> upon removal.</div>        </td></tr>
                <tr><td>autoboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not a VM is booted when the system is rebooted.</div>        </td></tr>
                <tr><td>boot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set the boot order for KVM VMs.</div>        </td></tr>
                <tr><td>brand<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>joyent</td>
        <td><ul><li>joyent</li><li>joyent-minimal</li><li>kvm</li><li>lx</li></ul></td>
        <td><div>Type of virtual machine.</div>        </td></tr>
                <tr><td>cpu_cap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets a limit on the amount of CPU time that can be used by a VM. Use <code>0</code> for no cap.</div>        </td></tr>
                <tr><td>cpu_shares<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets a limit on the number of fair share scheduler (FSS) CPU shares for a VM. This limit is relative to all other VMs on the system.</div>        </td></tr>
                <tr><td>cpu_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>qemu64</td>
        <td><ul><li>qemu64</li><li>host</li></ul></td>
        <td><div>Control the type of virtual CPU exposed to KVM VMs.</div>        </td></tr>
                <tr><td>customer_metadata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Metadata to be set and associated with this VM, this contain customer modifiable keys.</div>        </td></tr>
                <tr><td>delegate_dataset<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether to delegate a ZFS dataset to an OS VM.</div>        </td></tr>
                <tr><td>disk_driver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Default value for a virtual disk model for KVM guests.</div>        </td></tr>
                <tr><td>disks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of disks to add, valid properties are documented in vmadm(1M).</div>        </td></tr>
                <tr><td>dns_domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain value for <code>/etc/hosts</code>.</div>        </td></tr>
                <tr><td>filesystems<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Mount additional filesystems into an OS VM.</div>        </td></tr>
                <tr><td>firewall_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enables the firewall, allowing fwadm(1M) rules to be applied.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Force a particular action (i.e. stop or delete a VM).</div>        </td></tr>
                <tr><td>fs_allowed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comma separated list of filesystem types this zone is allowed to mount.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Zone/VM hostname.</div>        </td></tr>
                <tr><td>image_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Image UUID.</div>        </td></tr>
                <tr><td>indestructible_delegated<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Adds an <code>@indestructible</code> snapshot to delegated datasets.</div>        </td></tr>
                <tr><td>indestructible_zoneroot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Adds an <code>@indestructible</code> snapshot to zoneroot.</div>        </td></tr>
                <tr><td>internal_metadata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Metadata to be set and associated with this VM, this contains operator generated keys.</div>        </td></tr>
                <tr><td>internal_metadata_namespace<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of namespaces to be set as <em>internal_metadata-only</em>; these namespaces will come from <em>internal_metadata</em> rather than <em>customer_metadata</em>.</div>        </td></tr>
                <tr><td>kernel_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Kernel version to emulate for LX VMs.</div>        </td></tr>
                <tr><td>limit_priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set (comma separated) list of privileges the zone is allowed to use.</div>        </td></tr>
                <tr><td>maintain_resolvers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Resolvers in <code>/etc/resolv.conf</code> will be updated when updating the <em>resolvers</em> property.</div>        </td></tr>
                <tr><td>max_locked_memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Total amount of memory (in MiBs) on the host that can be locked by this VM.</div>        </td></tr>
                <tr><td>max_lwps<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum number of lightweight processes this VM is allowed to have running.</div>        </td></tr>
                <tr><td>max_physical_memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum amount of memory (in MiBs) on the host that the VM is allowed to use.</div>        </td></tr>
                <tr><td>max_swap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum amount of virtual memory (in MiBs) the VM is allowed to use.</div>        </td></tr>
                <tr><td>mdata_exec_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Timeout in seconds (or 0 to disable) for the <code>svc:/smartdc/mdata:execute</code> service that runs user-scripts in the zone.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the VM. vmadm(1M) uses this as an optional name.</div></br>
    <div style="font-size: small;">aliases: alias<div>        </td></tr>
                <tr><td>nic_driver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Default value for a virtual NIC model for KVM guests.</div>        </td></tr>
                <tr><td>nics<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of nics to add, valid properties are documented in vmadm(1M).</div>        </td></tr>
                <tr><td>nowait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Consider the provisioning complete when the VM first starts, rather than when the VM has rebooted.</div>        </td></tr>
                <tr><td>qemu_extra_opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Additional qemu cmdline arguments for KVM guests.</div>        </td></tr>
                <tr><td>qemu_opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Additional qemu arguments for KVM guests. This overwrites the default arguments provided by vmadm(1M) and should only be used for debugging.</div>        </td></tr>
                <tr><td>quota<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Quota on zone filesystems (in MiBs).</div>        </td></tr>
                <tr><td>ram<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Amount of virtual RAM for a KVM guest (in MiBs).</div>        </td></tr>
                <tr><td>resolvers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of resolvers to be put into <code>/etc/resolv.conf</code>.</div>        </td></tr>
                <tr><td>routes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary that maps destinations to gateways, these will be set as static routes in the VM.</div>        </td></tr>
                <tr><td>spice_opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Addition options for SPICE-enabled KVM VMs.</div>        </td></tr>
                <tr><td>spice_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password required to connect to SPICE. By default no password is set. Please note this can be read from the Global Zone.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>stopped</li><li>restarted</li></ul></td>
        <td><div>States for the VM to be in. Please note that <code>present</code>, <code>stopped</code> and <code>restarted</code> operate on a VM that is currently provisioned. <code>present</code> means that the VM will be created if it was absent, and that it will be in a running state. <code>absent</code> will shutdown the zone before removing it. <code>stopped</code> means the zone will be created if it doesn't exist already, before shutting it down.</div>        </td></tr>
                <tr><td>tmpfs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Amount of memory (in MiBs) that will be available in the VM for the <code>/tmp</code> filesystem.</div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of the VM. Can either be a full UUID or <code>*</code> for all VMs.</div>        </td></tr>
                <tr><td>vcpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of virtual CPUs for a KVM guest.</div>        </td></tr>
                <tr><td>vga<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify VGA emulation used by KVM VMs.</div>        </td></tr>
                <tr><td>virtio_txburst<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of packets that can be sent in a single flush of the tx queue of virtio NICs.</div>        </td></tr>
                <tr><td>virtio_txtimer<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Timeout (in nanoseconds) for the TX timer of virtio NICs.</div>        </td></tr>
                <tr><td>vnc_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password required to connect to VNC. By default no password is set. Please note this can be read from the Global Zone.</div>        </td></tr>
                <tr><td>vnc_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>TCP port to listen of the VNC server. Or set <code>0</code> for random, or <code>-1</code> to disable.</div>        </td></tr>
                <tr><td>zfs_data_compression<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies compression algorithm used for this VMs data dataset. This option only has effect on delegated datasets.</div>        </td></tr>
                <tr><td>zfs_data_recsize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Suggested block size (power of 2) for files in the delegated dataset's filesystem.</div>        </td></tr>
                <tr><td>zfs_filesystem_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum number of filesystems the VM can have.</div>        </td></tr>
                <tr><td>zfs_io_priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IO throttle priority value relative to other VMs.</div>        </td></tr>
                <tr><td>zfs_root_compression<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies compression algorithm used for this VMs root dataset. This option only has effect on the zoneroot dataset.</div>        </td></tr>
                <tr><td>zfs_root_recsize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Suggested block size (power of 2) for files in the zoneroot dataset's filesystem.</div>        </td></tr>
                <tr><td>zfs_snapshot_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of snapshots the VM can have.</div>        </td></tr>
                <tr><td>zpool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>ZFS pool the VM's zone dataset will be created in.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create SmartOS zone
      vmadm:
        brand: joyent
        state: present
        alias: fw_zone
        image_uuid: 95f265b8-96b2-11e6-9597-972f3af4b6d5
        firewall_enabled: yes
        indestructible_zoneroot: yes
        nics:
          - nic_tag: admin
            ip: dhcp
            primary: true
        internal_metadata:
          root_pw: 'secret'
        quota: 1
    
    - name: Delete a zone
      vmadm:
        alias: test_zone
        state: deleted
    
    - name: Stop all zones
      vmadm:
        uuid: '*'
        state: stopped

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
        <td> alias </td>
        <td> Alias of the managed VM. </td>
        <td align=center> When addressing a VM by alias. </td>
        <td align=center> string </td>
        <td align=center> dns-zone </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the target, after execution. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> running </td>
    </tr>
            <tr>
        <td> uuid </td>
        <td> UUID of the managed VM. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> b217ab0b-cf57-efd8-cd85-958d0b80be33 </td>
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
