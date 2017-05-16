.. _vmware_guest:


vmware_guest - Manages virtualmachines in vcenter
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Uses pyvmomi to ...
copy a template to a new virtualmachine
poweron/poweroff/restart a virtualmachine
remove a virtualmachine


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
            <tr>
    <td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Destination datacenter for the deploy operation</div></td></tr>
            <tr>
    <td>disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of disks to add</div></td></tr>
            <tr>
    <td>esxi_hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The esxi hostname where the VM will run.</div></td></tr>
            <tr>
    <td>folder<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Destination folder path for the new guest</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Ignore warnings and complete the actions</div></td></tr>
            <tr>
    <td>hardware<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Attributes such as cpus, memory, osid, and disk controller</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname or IP address of the vSphere vCenter</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the newly deployed guest</div></td></tr>
            <tr>
    <td>name_match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>first</td>
        <td><ul><li>first</li><li>last</li></ul></td>
        <td><div>If multiple vms matching the name, use the first or last found</div></td></tr>
            <tr>
    <td>nic<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of nics to add</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: pass, pwd<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>poweredon</li><li>poweredoff</li><li>restarted</li><li>suspended</li></ul></td>
        <td><div>What state should the virtualmachine be in?</div></td></tr>
            <tr>
    <td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the template to deploy, if needed to create the guest (state=present).</div><div>If the guest exists already this setting will be ignored.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: user, admin<div></td></tr>
            <tr>
    <td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>UUID of the instance to manage if known, this is vmware's unique identifier.</div><div>This is required if name is not supplied.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted</div></td></tr>
            <tr>
    <td>wait_for_ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Wait until vcenter detects an IP address for the guest</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Example from Ansible playbook
    #
    # Create a VM from a template
    #
        - name: create the VM
          vmware_guest:
            validate_certs: False
            hostname: 192.0.2.44
            username: administrator@vsphere.local
            password: vmware
            name: testvm_2
            state: poweredon
            folder: testvms
            disk:
                - size_gb: 10
                  type: thin
                  datastore: g73_datastore
            nic:
                - type: vmxnet3
                  network: VM Network
                  network_type: standard
            hardware:
                memory_mb: 512
                num_cpus: 1
                osid: centos64guest
                scsi: paravirtual
            datacenter: datacenter1
            esxi_hostname: 192.0.2.117
            template: template_el7
            wait_for_ip_address: yes
          register: deploy
    
    #
    # Gather facts only
    #
        - name: gather the VM facts
          vmware_guest:
            validate_certs: False
            hostname: 192.168.1.209
            username: administrator@vsphere.local
            password: vmware
            name: testvm_2
            esxi_hostname: 192.168.1.117
          register: facts

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

.. note:: Tested on vSphere 6.0


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

