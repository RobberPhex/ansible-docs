.. _ovirt_disks:


ovirt_disks - Module to manage Virtual Machine and floating disks in oVirt.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Module to manage Virtual Machine and floating disks in oVirt.


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
            <tr>
    <td>auth<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary with values needed to create HTTP/HTTPS connection to oVirt:</div><div><code>username</code>[<em>required</em>] - The name of the user, something like `<em>admin@internal</em>`.</div><div><code>password</code>[<em>required</em>] - The password of the user.</div><div><code>url</code>[<em>required</em>] - A string containing the base URL of the server, usually something like `<em>https://server.example.com/ovirt-engine/api</em>`.</div><div><code>token</code> - Token to be used instead of login with username/password.</div><div><code>insecure</code> - A boolean flag that indicates if the server TLS certificate and host name should be checked.</div><div><code>ca_file</code> - A PEM file containing the trusted CA certificates. The certificate presented by the server will be verified using these CA certificates. If `<code>ca_file</code>` parameter is not set, system wide CA certificate store is used.</div><div><code>kerberos</code> - A boolean flag indicating if Kerberos authentication should be used instead of the default basic authentication.</div></td></tr>
            <tr>
    <td>bootable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div><em>True</em> if the disk should be bootable. By default when disk is created it isn't bootable.</div></td></tr>
            <tr>
    <td>format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>raw</li><li>cow</li></ul></td>
        <td><div>Format of the disk. Either copy-on-write or raw.</div></td></tr>
            <tr>
    <td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ID of the disk to manage. Either <code>id</code> or <code>name</code> is required.</div></td></tr>
            <tr>
    <td>interface<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>virtio</td>
        <td><ul><li>virtio</li><li>ide</li><li>virtio_scsi</li></ul></td>
        <td><div>Driver of the storage interface.</div></td></tr>
            <tr>
    <td>logical_unit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary which describes LUN to be directly attached to VM:</div><div><code>address</code> - Address of the storage server. Used by iSCSI.</div><div><code>port</code> - Port of the storage server. Used by iSCSI.</div><div><code>target</code> - iSCSI target.</div><div><code>lun_id</code> - LUN id.</div><div><code>username</code> - CHAP Username to be used to access storage server. Used by iSCSI.</div><div><code>password</code> - CHAP Password of the user to be used to access storage server. Used by iSCSI.</div><div><code>storage_type</code> - Storage type either <em>fcp</em> or <em>iscsi</em>.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the disk to manage. Either <code>id</code> or <code>name</code>/<code>alias</code> is required.</div></br>
        <div style="font-size: small;">aliases: alias<div></td></tr>
            <tr>
    <td>poll_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td><ul></ul></td>
        <td><div>Number of the seconds the module waits until another poll request on entity status is sent.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Disk profile name to be attached to disk. By default profile is chosen by oVirt engine.</div></td></tr>
            <tr>
    <td>shareable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div><em>True</em> if the disk should be shareable. By default when disk is created it isn't shareable.</div></td></tr>
            <tr>
    <td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Size of the disk. Size should be specified using IEC standard units. For example 10GiB, 1024MiB, etc.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>attached</li><li>detached</li></ul></td>
        <td><div>Should the Virtual Machine disk be present/absent/attached/detached.</div></td></tr>
            <tr>
    <td>storage_domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Storage domain name where disk should be created. By default storage is chosen by oVirt engine.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td><ul></ul></td>
        <td><div>The amount of time in seconds the module should wait for the instance to get into desired state.</div></td></tr>
            <tr>
    <td>vm_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ID of the Virtual Machine to manage. Either <code>vm_id</code> or <code>vm_name</code> is required if <code>state</code> is <em>attached</em> or <em>detached</em>.</div></td></tr>
            <tr>
    <td>vm_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the Virtual Machine to manage. Either <code>vm_id</code> or <code>vm_name</code> is required if <code>state</code> is <em>attached</em> or <em>detached</em>.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>True if the module should wait for the entity to get into desired state.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Examples don't contain auth parameter for simplicity,
    # look at ovirt_auth module to see how to reuse authentication:
    
    # Create and attach new disk to VM
    - ovirt_disks:
        name: myvm_disk
        vm_name: rhel7
        size: 10GiB
        format: cow
        interface: virtio
    
    # Attach logical unit to VM rhel7
    - ovirt_disks:
        vm_name: rhel7
        logical_unit:
          target: iqn.2016-08-09.brq.str-01:omachace
          id: 1IET_000d0001
          address: 10.34.63.204
        interface: virtio
    
    # Detach disk from VM
    - ovirt_disks:
        state: detached
        name: myvm_disk
        vm_name: rhel7
        size: 10GiB
        format: cow
        interface: virtio

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
        <td> disk </td>
        <td> Dictionary of all the disk attributes. Disk attributes can be found on your oVirt instance at following url: https://ovirt.example.com/ovirt-engine/api/model#types/disk. </td>
        <td align=center> On success if disk is found and C(vm_id) or C(vm_name) wasn't passed. </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> id </td>
        <td> ID of the managed disk </td>
        <td align=center> On success if disk is found. </td>
        <td align=center> str </td>
        <td align=center> 7de90f31-222c-436c-a1ca-7e655bd5b60c </td>
    </tr>
            <tr>
        <td> disk_attachment </td>
        <td> Dictionary of all the disk attachment attributes. Disk attachment attributes can be found on your oVirt instance at following url: https://ovirt.example.com/ovirt-engine/api/model#types/disk_attachment. </td>
        <td align=center> On success if disk is found and C(vm_id) or C(vm_name) was passed and VM was found. </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: In order to use this module you have to install oVirt Python SDK. To ensure it's installed with correct version you can create the following task: pip: name=ovirt-engine-sdk-python version=4.0.0


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

