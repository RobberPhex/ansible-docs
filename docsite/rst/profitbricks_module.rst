.. _profitbricks:


profitbricks - Create, destroy, start, stop, and reboot a ProfitBricks virtual machine.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, destroy, update, start, stop, and reboot a ProfitBricks virtual machine. When the virtual machine is created it can optionally wait for it to be 'running' before returning. This module has a dependency on profitbricks >= 1.0.0


Requirements (on host that executes module)
-------------------------------------------

  * profitbricks
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
            <tr>
    <td>assign_public_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>This will assign the machine to the public LAN. If no LAN exists with public Internet access it is created.</div></td></tr>
            <tr>
    <td>auto_increment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to increment a single number in the name for created virtual machines.</div></td></tr>
            <tr>
    <td>bus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>VIRTIO</td>
        <td><ul><li>IDE</li><li>VIRTIO</li></ul></td>
        <td><div>The bus type for the volume.</div></td></tr>
            <tr>
    <td>cores<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td><ul></ul></td>
        <td><div>The number of CPU cores to allocate to the virtual machine.</div></td></tr>
            <tr>
    <td>count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The number of virtual machines to create.</div></td></tr>
            <tr>
    <td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Datacenter to provision this virtual machine.</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The system image ID for creating the virtual machine, e.g. a3eae284-a2fe-11e4-b187-5f1f641608c8.</div></td></tr>
            <tr>
    <td>instance_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>list of instance ids, currently only used when state='absent' to remove instances.</div></td></tr>
            <tr>
    <td>lan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The ID of the LAN you wish to add the servers to.</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us/las</td>
        <td><ul><li>us/las</li><li>us/lasdev</li><li>de/fra</li><li>de/fkb</li></ul></td>
        <td><div>The datacenter location. Use only if you want to create the Datacenter or else this value is ignored.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the virtual machine.</div></td></tr>
            <tr>
    <td>ram<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2048</td>
        <td><ul></ul></td>
        <td><div>The amount of memory to allocate to the virtual machine.</div></td></tr>
            <tr>
    <td>remove_boot_volume<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>remove the bootVolume of the virtual machine you're destroying.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>running</li><li>stopped</li><li>absent</li><li>present</li></ul></td>
        <td><div>create or terminate instances</div></td></tr>
            <tr>
    <td>subscription_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>THe ProfitBricks password. Overrides the PB_PASSWORD environement variable.</div></td></tr>
            <tr>
    <td>subscription_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ProfitBricks username. Overrides the PB_SUBSCRIPTION_ID environement variable.</div></td></tr>
            <tr>
    <td>volume_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>The size in GB of the boot volume.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the instance to be in state 'running' before returning</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>how long before wait gives up, in seconds</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Provisioning example. This will create three servers and enumerate their names. 
    
    - profitbricks:
        datacenter: Tardis One
        name: web%02d.stackpointcloud.com
        cores: 4
        ram: 2048
        volume_size: 50
        image: a3eae284-a2fe-11e4-b187-5f1f641608c8
        location: us/las
        count: 3
        assign_public_ip: true
    
    # Removing Virtual machines
    
    - profitbricks:
        datacenter: Tardis One
        instance_ids:
          - 'web001.stackpointcloud.com'
          - 'web002.stackpointcloud.com'
          - 'web003.stackpointcloud.com'
        wait_timeout: 500
        state: absent
    
    # Starting Virtual Machines.
    
    - profitbricks:
        datacenter: Tardis One
        instance_ids:
          - 'web001.stackpointcloud.com'
          - 'web002.stackpointcloud.com'
          - 'web003.stackpointcloud.com'
        wait_timeout: 500
        state: running
    
    # Stopping Virtual Machines
    
    - profitbricks:
        datacenter: Tardis One
        instance_ids:
          - 'web001.stackpointcloud.com'
          - 'web002.stackpointcloud.com'
          - 'web003.stackpointcloud.com'
        wait_timeout: 500
        state: stopped
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

