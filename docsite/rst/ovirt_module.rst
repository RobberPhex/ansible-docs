.. _ovirt:


ovirt - oVirt/RHEV platform management
++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

allows you to create new instances, either from scratch or an image, in addition to deleting or stopping instances on the oVirt/RHEV platform


Requirements
------------

  * python >= 2.6
  * ovirt-engine-sdk-python


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
    <td>disk_alloc<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>thin</td>
        <td><ul><li>thin</li><li>preallocated</li></ul></td>
        <td><div>define if disk is thin or preallocated</div></td></tr>
            <tr>
    <td>disk_int<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>virtio</td>
        <td><ul><li>virtio</li><li>ide</li></ul></td>
        <td><div>interface type of the disk</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>template to use for the instance</div></td></tr>
            <tr>
    <td>instance_cores<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>define the instance's number of cores</div></br>
        <div style="font-size: small;">aliases: vmcores<div></td></tr>
            <tr>
    <td>instance_cpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>the instance's number of cpu's</div></br>
        <div style="font-size: small;">aliases: vmcpus<div></td></tr>
            <tr>
    <td>instance_disksize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>size of the instance's disk in GB</div></br>
        <div style="font-size: small;">aliases: vm_disksize<div></td></tr>
            <tr>
    <td>instance_mem<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the instance's amount of memory in MB</div></br>
        <div style="font-size: small;">aliases: vmmem<div></td></tr>
            <tr>
    <td>instance_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the name of the instance to use</div></br>
        <div style="font-size: small;">aliases: vmname<div></td></tr>
            <tr>
    <td>instance_network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>rhevm</td>
        <td><ul></ul></td>
        <td><div>the logical network the machine should belong to</div></br>
        <div style="font-size: small;">aliases: vmnetwork<div></td></tr>
            <tr>
    <td>instance_nic<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the network interface in oVirt/RHEV</div></br>
        <div style="font-size: small;">aliases: vmnic<div></td></tr>
            <tr>
    <td>instance_os<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>type of Operating System</div></br>
        <div style="font-size: small;">aliases: vmos<div></td></tr>
            <tr>
    <td>instance_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>server</td>
        <td><ul><li>server</li><li>desktop</li></ul></td>
        <td><div>define if the instance is a server or desktop</div></br>
        <div style="font-size: small;">aliases: vmtype<div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>password of the user to authenticate with</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the oVirt/RHEV datacenter where you want to deploy to</div></td></tr>
            <tr>
    <td>resource_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>new</li><li>template</li></ul></td>
        <td><div>whether you want to deploy an image or create an instance from scratch.</div></td></tr>
            <tr>
    <td>sdomain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the Storage Domain where you want to create the instance's disk on.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>shutdown</li><li>started</li><li>restarted</li></ul></td>
        <td><div>create, terminate or remove instances</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the url of the oVirt instance</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the user to authenticate with</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>deploy the image to this oVirt cluster</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic example provisioning from image.
    
    action: ovirt >
        user=admin@internal 
        url=https://ovirt.example.com 
        instance_name=ansiblevm04 
        password=secret 
        image=centos_64 
        zone=cluster01 
        resource_type=template"
    
    # Full example to create new instance from scratch
    action: ovirt > 
        instance_name=testansible 
        resource_type=new 
        instance_type=server 
        user=admin@internal 
        password=secret 
        url=https://ovirt.example.com 
        instance_disksize=10 
        zone=cluster01 
        region=datacenter1 
        instance_cpus=1 
        instance_nic=nic1 
        instance_network=rhevm 
        instance_mem=1000 
        disk_alloc=thin 
        sdomain=FIBER01 
        instance_cores=1 
        instance_os=rhel_6x64 
        disk_int=virtio"
    
    # stopping an instance
    action: ovirt >
        instance_name=testansible
        state=stopped
        user=admin@internal
        password=secret
        url=https://ovirt.example.com
    
    # starting an instance
    action: ovirt >
        instance_name=testansible 
        state=started 
        user=admin@internal 
        password=secret 
        url=https://ovirt.example.com
    
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

