.. _vmware_cluster:


vmware_cluster - Create VMware vSphere Cluster
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create VMware vSphere Cluster


Requirements
------------

  * Tested on ESXi 5.5
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
    <td>cluster_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the cluster that will be created</div></td></tr>
            <tr>
    <td>datacenter_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the datacenter the cluster will be created in.</div></td></tr>
            <tr>
    <td>enable_drs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set to True will enable DRS when the cluster is created.</div></td></tr>
            <tr>
    <td>enable_ha<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set to True will enable HA when the cluster is created.</div></td></tr>
            <tr>
    <td>enable_vsan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set to True will enable vSAN when the cluster is created.</div></td></tr>
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
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: user, admin<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example vmware_cluster command from Ansible Playbooks
    - name: Create Cluster
          local_action: >
            vmware_cluster
            hostname="{{ ansible_ssh_host }}" username=root password=vmware
            datacenter_name="datacenter"
            cluster_name="cluster"
            enable_ha=True
            enable_drs=True
            enable_vsan=True




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

