.. _ovirt:


ovirt - oVirt/RHEV platform management
++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

allows you to create new instances, either from scratch or an image, in addition to deleting or stopping instances on the oVirt/RHEV platform

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
    <td>disk_alloc</td>
    <td>no</td>
    <td>thin</td>
        <td><ul><li>thin</li><li>preallocated</li></ul></td>
        <td>define if disk is thin or preallocated</td>
    </tr>
            <tr>
    <td>disk_int</td>
    <td>no</td>
    <td>virtio</td>
        <td><ul><li>virtio</li><li>ide</li></ul></td>
        <td>interface type of the disk</td>
    </tr>
            <tr>
    <td>image</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>template to use for the instance</td>
    </tr>
            <tr>
    <td>instance_cores</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>define the instance's number of cores</td>
    </tr>
            <tr>
    <td>instance_cpus</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>the instance's number of cpu's</td>
    </tr>
            <tr>
    <td>instance_disksize</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>size of the instance's disk in GB</td>
    </tr>
            <tr>
    <td>instance_mem</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the instance's amount of memory in MB</td>
    </tr>
            <tr>
    <td>instance_name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the name of the instance to use</td>
    </tr>
            <tr>
    <td>instance_network</td>
    <td>no</td>
    <td>rhevm</td>
        <td><ul></ul></td>
        <td>the logical network the machine should belong to</td>
    </tr>
            <tr>
    <td>instance_nic</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the network interface in oVirt/RHEV</td>
    </tr>
            <tr>
    <td>instance_os</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>type of Operating System</td>
    </tr>
            <tr>
    <td>instance_type</td>
    <td>no</td>
    <td>server</td>
        <td><ul><li>server</li><li>desktop</li></ul></td>
        <td>define if the instance is a server or desktop</td>
    </tr>
            <tr>
    <td>password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>password of the user to authenticate with</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the oVirt/RHEV datacenter where you want to deploy to</td>
    </tr>
            <tr>
    <td>resource_type</td>
    <td>no</td>
    <td></td>
        <td><ul><li>new</li><li>template</li></ul></td>
        <td>whether you want to deploy an image or create an instance from scratch.</td>
    </tr>
            <tr>
    <td>sdomain</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the Storage Domain where you want to create the instance's disk on.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>shutdown</li><li>started</li><li>restarted</li></ul></td>
        <td>create, terminate or remove instances</td>
    </tr>
            <tr>
    <td>url</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the url of the oVirt instance</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the user to authenticate with</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>deploy the image to this oVirt cluster</td>
    </tr>
        </table>


.. note:: Requires ovirt-engine-sdk


Examples
--------

.. raw:: html

    <br/>


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

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

