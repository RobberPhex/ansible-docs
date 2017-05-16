.. _vca_vapp:


vca_vapp - Manages vCloud Air vApp instances.
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module will actively managed vCloud Air vApp instances.  Instances can be created and deleted as well as both deployed and undeployed.




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
    <td>api_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5.7</td>
        <td><ul></ul></td>
        <td><div>The api version to be used with the vca</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The authentication host to be used when service type  is vcd.</div></td></tr>
            <tr>
    <td>instance_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The instance id in a vchs environment to be used for creating the vapp</div></td></tr>
            <tr>
    <td>network_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>pool</td>
        <td><ul><li>pool</li><li>dhcp</li><li>static</li></ul></td>
        <td><div>Configures the mode of the network connection.</div></td></tr>
            <tr>
    <td>network_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the network that should be attached to the virtual machine in the vApp.  The virtual network specified must already be created in the vCloud Air VDC.  If the <em>state</em> is not 'absent' then the <em>network_name</em> argument must be provided.</div></td></tr>
            <tr>
    <td>operation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>noop</td>
        <td><ul><li>noop</li><li>poweron</li><li>poweroff</li><li>suspend</li><li>shutdown</li><li>reboot</li><li>reset</li></ul></td>
        <td><div>Specifies an operation to be performed on the vApp.</div></td></tr>
            <tr>
    <td>org<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The org to login to for creating vapp, mostly set when the service_type is vdc.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The vCloud Air password to use during authentication</div></td></tr>
            <tr>
    <td>service_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>vca</td>
        <td><ul><li>vca</li><li>vchs</li><li>vcd</li></ul></td>
        <td><div>The type of service we are authenticating against</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>deployed</li><li>undeployed</li></ul></td>
        <td><div>Configures the state of the vApp.</div></td></tr>
            <tr>
    <td>template_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the vApp template to use to create the vApp instance.  If the <em>state</em> is not `absent` then the <em>template_name</em> value must be provided.  The <em>template_name</em> must be previously uploaded to the catalog specified by <em>catalog_name</em></div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The vCloud Air username to use during authentication</div></td></tr>
            <tr>
    <td>vapp_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the vCloud Air vApp instance</div></td></tr>
            <tr>
    <td>vdc_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the virtual data center (VDC) where the vm should be created or contains the vAPP.</div></td></tr>
            <tr>
    <td>vm_cpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The number of vCPUs to configure for the VM in the vApp.   If the <em>vm_name</em> argument is provided, then this becomes a per VM setting otherwise it is applied to all VMs in the vApp.</div></td></tr>
            <tr>
    <td>vm_memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The amount of memory in MB to allocate to VMs in the vApp.  If the <em>vm_name</em> argument is provided, then this becomes a per VM setting otherise it is applied to all VMs in the vApp.</div></td></tr>
            <tr>
    <td>vm_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the virtual machine instance in the vApp to manage.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: Creates a new vApp in a VCA instance
      vca_vapp:
        vapp_name: tower
        state=present
        template_name='Ubuntu Server 12.04 LTS (amd64 20150127)'
        vdc_name=VDC1
        instance_id=<your instance id here>
        username=<your username here>
        password=<your password here>
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

