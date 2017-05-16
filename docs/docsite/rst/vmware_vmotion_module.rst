.. _vmware_vmotion:


vmware_vmotion - Move a virtual machine using vMotion
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Using VMware vCenter, move a virtual machine using vMotion to a different host.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * pyVmomi


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
                <tr><td>destination_host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the end host the VM should be running on</div></br>
    <div style="font-size: small;">aliases: destination<div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the vSphere vCenter.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: pass, pwd<div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: user, admin<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted.</div>        </td></tr>
                <tr><td>vm_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the VM to perform a vMotion on</div></br>
    <div style="font-size: small;">aliases: vm<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example from Ansible playbook
    
        - name: Perform vMotion of VM
          local_action:
            module: vmware_vmotion
            hostname: 'vcenter_hostname'
            username: 'vcenter_username'
            password: 'vcenter_password'
            validate_certs: False
            vm_name: 'vm_name_as_per_vcenter'
            destination_host: 'destination_host_as_per_vcenter'

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
        <td> running_host </td>
        <td> List the host the virtual machine is registered to </td>
        <td align=center> ['changed', 'success'] </td>
        <td align=center> string </td>
        <td align=center> host1.example.com </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Tested on vSphere 6.0



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
