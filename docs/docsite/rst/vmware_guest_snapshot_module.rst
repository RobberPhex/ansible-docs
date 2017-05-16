.. _vmware_guest_snapshot:


vmware_guest_snapshot - Manages virtual machines snapshots in vcenter
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create virtual machines snapshots


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
                <tr><td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Destination datacenter for the deploy operation</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Define an arbitrary description to attach to snapshot.</div>        </td></tr>
                <tr><td>folder<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Define instance folder location.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the vSphere vCenter.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the VM to work with</div>        </td></tr>
                <tr><td>name_match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>first</td>
        <td><ul><li>first</li><li>last</li></ul></td>
        <td><div>If multiple VMs matching the name, use the first or last found</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: pass, pwd<div>        </td></tr>
                <tr><td>snapshot_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the snapshot name to manage.</div><div>This param is required only if state is not <code>remove_all</code></div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>revert</li><li>remove_all</li></ul></td>
        <td><div>Manage snapshots attached to a specific virtual machine.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: user, admin<div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of the instance to manage if known, this is VMware's unique identifier.</div><div>This is required if name is not supplied.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: Create snapshot
        vmware_guest_snapshot:
          hostname: 192.168.1.209
          username: administrator@vsphere.local
          password: vmware
          name: dummy_vm
          state: present
          snapshot_name: snap1
          description: snap1_description
    
      - name: Remove a snapshot
        vmware_guest_snapshot:
          hostname: 192.168.1.209
          username: administrator@vsphere.local
          password: vmware
          name: dummy_vm
          state: remove
          snapshot_name: snap1
    
      - name: Revert to a snapshot
        vmware_guest_snapshot:
          hostname: 192.168.1.209
          username: administrator@vsphere.local
          password: vmware
          name: dummy_vm
          state: revert
          snapshot_name: snap1
    
      - name: Remove all snapshots of a VM
        vmware_guest_snapshot:
          hostname: 192.168.1.209
          username: administrator@vsphere.local
          password: vmware
          name: dummy_vm
          state: remove_all

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

.. note::
    - Tested on vSphere 5.5



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
