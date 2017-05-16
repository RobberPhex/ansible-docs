.. _vmware_target_canonical_facts:


vmware_target_canonical_facts - Return canonical (NAA) from an ESXi host
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Return canonical (NAA) from an ESXi host based on SCSI target ID


Requirements (on host that executes module)
-------------------------------------------

  * Tested on vSphere 5.5
  * PyVmomi installed


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
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname or IP address of the vSphere vCenter</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: pass, pwd<div></td></tr>
            <tr>
    <td>target_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The target id based on order of scsi device</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: user, admin<div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example vmware_target_canonical_facts command from Ansible Playbooks
    - name: Get Canonical name
          local_action: >
            vmware_target_canonical_facts
            hostname="{{ ansible_ssh_host }}" username=root password=vmware
            target_id=7




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

